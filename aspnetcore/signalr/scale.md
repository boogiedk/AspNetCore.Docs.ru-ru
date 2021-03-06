---
title: ASP.NET Core SignalR производственного размещения и масштабирования
author: bradygaster
description: Узнайте, как избежать проблем с производительностью и масштабированием в приложениях, использующих ASP.NET Core SignalR .
monikerRange: '>= aspnetcore-2.1'
ms.author: bradyg
ms.custom: mvc
ms.date: 01/17/2020
no-loc:
- appsettings.json
- ASP.NET Core Identity
- cookie
- Cookie
- Blazor
- Blazor Server
- Blazor WebAssembly
- Identity
- Let's Encrypt
- Razor
- SignalR
uid: signalr/scale
ms.openlocfilehash: d3e9cd23a55702bcf9b002dcce556428683afeca
ms.sourcegitcommit: ca34c1ac578e7d3daa0febf1810ba5fc74f60bbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/30/2020
ms.locfileid: "93052777"
---
# <a name="aspnet-core-no-locsignalr-hosting-and-scaling"></a>ASP.NET Core SignalR размещение и масштабирование

[Эндрю Стантон-медперсонала](https://twitter.com/anurse), [Брейди Гастер](https://twitter.com/bradygaster)и [Tom Dykstra)](https://github.com/tdykstra)

В этой статье описываются вопросы размещения и масштабирования для приложений с высоким уровнем трафика, использующих ASP.NET Core SignalR .

## <a name="sticky-sessions"></a>Закрепленные сеансы

SignalR требует, чтобы все HTTP-запросы для определенного соединения обрабатывались одним и тем же процессом сервера. Если SignalR работает на ферме серверов (несколько серверов), необходимо использовать "прикрепленные сеансы". «Прикрепленные сеансы» также называют сходством сеансов некоторыми подсистемами балансировки нагрузки. Служба приложений Azure использует [маршрутизацию запросов приложений](/iis/extensions/planning-for-arr/application-request-routing-version-2-overview) (ARR) для маршрутизации запросов. Включение параметра "Настройка сходства" в службе приложений Azure включит "закрепленные сеансы". Существуют следующие ситуации, в которых не требуется закрепить сеансы.

1. При размещении на одном сервере в одном процессе.
1. При использовании службы Azure SignalR .
1. Если все клиенты настроены на использование **только** WebSockets, **а** [параметр скипнеготиатион](xref:signalr/configuration#configure-additional-options) включен в конфигурации клиента.

Во всех остальных случаях (включая использование объединительной платы Redis) серверная среда должна быть настроена для работы с закрепленными сеансами.

Рекомендации по настройке службы приложений Azure для SignalR см. в разделе <xref:signalr/publish-to-azure-web-app> .

## <a name="tcp-connection-resources"></a>Ресурсы TCP-подключения

Количество одновременных TCP-подключений, которое может поддерживаться веб-сервером, ограничено. Стандартные клиенты HTTP используют *временные* подключения. Эти подключения могут быть закрыты, когда клиент переходит в состояние простоя и снова открывается позже. С другой стороны, SignalR подключение является *постоянным* . SignalR соединения остаются открытыми, даже когда клиент переходит в состояние бездействия. В приложении с большим трафиком, которое обслуживает много клиентов, эти постоянные подключения могут привести к тому, что серверы достигли максимального числа подключений.

Постоянные подключения также потребляют некоторую дополнительную память для наблюдения за каждым подключением.

Интенсивное использование ресурсов, связанных с подключением, SignalR может повлиять на другие веб-приложения, размещенные на том же сервере. Когда SignalR открывает и сохраняет последние доступные подключения TCP, другие веб-приложения на том же сервере также будут иметь недоступные для них подключения.

Если на сервере не хватает подключений, вы увидите случайные ошибки сокета и ошибки сброса соединения. Пример:

```
An attempt was made to access a socket in a way forbidden by its access permissions...
```

Чтобы SignalR использование ресурсов не вызывало ошибок в других веб-приложениях, запустите SignalR на разных серверах другие веб-приложения.

Чтобы SignalR использование ресурсов не вызывало ошибок в SignalR приложении, необходимо выполнить масштабирование, чтобы ограничить число подключений, которое должен выполнять сервер.

## <a name="scale-out"></a>Горизонтальное увеличение масштаба

Приложение, использующее, SignalR должно отследить все его подключения, что создает проблемы для фермы серверов. Добавьте сервер, и он получает новые подключения, о которых не известны другие серверы. Например, SignalR на каждом сервере на следующей схеме не знаются соединения на других серверах. Когда SignalR на одном из серверов требуется отправить сообщение всем клиентам, оно передается только тем клиентам, которые подключены к этому серверу.

![Масштабирование::: No-Loc (SignalR)::: без объединительной платы](scale/_static/scale-no-backplane.png)

Варианты решения этой проблемы: [ SignalR служба Azure](#azure-signalr-service) и [Redisная Объединительная плата](#redis-backplane).

## <a name="azure-no-locsignalr-service"></a>Служба Azure SignalR

Служба Azure SignalR — это прокси-сервер, а не Объединительная плата. Каждый раз, когда клиент инициирует подключение к серверу, клиент перенаправляется для подключения к службе. Этот процесс показан на следующей схеме:

![Установление соединения с Azure::: No-Loc (SignalR)::: Service](scale/_static/azure-signalr-service-one-connection.png)

В результате служба управляет всеми клиентскими подключениями, в то время как каждому серверу требуется лишь небольшое постоянное число подключений к службе, как показано на следующей схеме:

![Клиенты, подключенные к службе, серверы, подключенные к службе](scale/_static/azure-signalr-service-multiple-connections.png)

Этот подход к горизонтальному масштабированию имеет несколько преимуществ по сравнению с альтернативой объединительной платы Redis:

* Прикрепленные сеансы, также известные как [сходство клиентов](/iis/extensions/configuring-application-request-routing-arr/http-load-balancing-using-application-request-routing#step-3---configure-client-affinity), не являются обязательными, так как клиенты сразу же перенаправляются в SignalR службу Azure при подключении.
* SignalRПриложение может масштабироваться в зависимости от числа отправленных сообщений, а SignalR служба Azure масштабируется для выполнения любого числа подключений. Например, могут быть тысячи клиентов, но если отправлено всего несколько сообщений в секунду, SignalR приложению не придется масштабироваться на несколько серверов, чтобы обрабатывать сами подключения.
* SignalRПриложение не будет использовать значительно больше ресурсов для подключения, чем веб-приложение SignalR .

По этим причинам мы рекомендуем использовать службу Azure SignalR для всех ASP.NET Core SignalR приложений, размещенных в Azure, включая службу приложений, виртуальные машины и контейнеры.

Дополнительные сведения см. в [ SignalR документации по службе Azure](/azure/azure-signalr/signalr-overview).

## <a name="redis-backplane"></a>Канал обмена Redis

[Redis](https://redis.io/) — это хранилище "ключ — значение" в памяти, которое поддерживает систему обмена сообщениями с моделью публикации и подписки. SignalRДля пересылки сообщений на другие серверы в объединительной плате Redis используется функция Pub/подкаталогов. Когда клиент устанавливает соединение, сведения о соединении передаются в объединительную плату. Когда сервер хочет отправить сообщение всем клиентам, он отправляется в объединительную плату. Объединительная плата знает все подключенные клиенты и серверы, на которых они находятся. Он отправляет сообщение всем клиентам через соответствующие серверы. Этот процесс показан на следующей схеме:

![Redis Объединительная часть, сообщение, отправленное с одного сервера на все клиенты](scale/_static/redis-backplane.png)

Объединительная плата Redis — это рекомендуемый подход к горизонтальному масштабированию для приложений, размещенных в собственной инфраструктуре. Если между центром обработки данных и центром обработки данных Azure возникает значительная задержка подключения, SignalR служба Azure может оказаться непрактичной для локальных приложений с низкой задержкой или требованиями высокой пропускной способности.

SignalRПреимущества службы Azure, упомянутые ранее, являются недостатками объединительной платы Redis:

* Прикрепленные сеансы, также известные как [сходство клиентов](/iis/extensions/configuring-application-request-routing-arr/http-load-balancing-using-application-request-routing#step-3---configure-client-affinity), являются обязательными, за исключением случаев, когда выполняются **оба** следующих условия.
  * Все клиенты настроены для использования **только** WebSockets.
  * [Параметр скипнеготиатион](xref:signalr/configuration#configure-additional-options) включен в конфигурации клиента. 
   После инициации подключения на сервере соединение должно остаться на этом сервере.
* SignalRПриложение должно масштабироваться на основе числа клиентов, даже если отправляется несколько сообщений.
* SignalRПриложение использует значительно больше ресурсов для подключения, чем веб-приложение, без SignalR .

## <a name="iis-limitations-on-windows-client-os"></a>Ограничения IIS в клиентской ОС Windows

Windows 10 и Windows 8. x являются клиентскими операционными системами. Службы IIS в клиентских операционных системах имеют ограничение в 10 одновременных подключений. SignalRподключения:

* Временное и часто переустановленное.
* **Не** удаляется сразу, когда больше не используется.

Предыдущие условия, вероятно, пристигают 10 ограничений на подключение к клиентской ОС. При использовании клиентской ОС для разработки рекомендуется:

* Избегайте IIS.
* Используйте Kestrel или IIS Express в качестве целевых объектов развертывания.

## <a name="linux-with-nginx"></a>Linux с Nginx

Ниже приведены минимальные необходимые параметры для включения WebSockets, Серверсентевентс и Лонгполлинг для SignalR :

```nginx
http {
  map $http_connection $connection_upgrade {
    "~*Upgrade" $http_connection;
    default keep-alive;
}

  server {
    listen 80;
    server_name example.com *.example.com;

    # Configure the SignalR Endpoint
    location /hubroute {
      # App server url
      proxy_pass http://localhost:5000;

      # Configuration for WebSockets
      proxy_set_header Upgrade $http_upgrade;
      proxy_set_header Connection $connection_upgrade;
      proxy_cache off;

      # Configuration for ServerSentEvents
      proxy_buffering off;

      # Configuration for LongPolling or if your KeepAliveInterval is longer than 60 seconds
      proxy_read_timeout 100s;

      proxy_set_header Host $host;
      proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
      proxy_set_header X-Forwarded-Proto $scheme;
    }
  }
}
```

При использовании нескольких внутренних серверов необходимо добавить прикрепленные сеансы, чтобы предотвратить SignalR Переключение серверов при подключении. Существует несколько способов добавления прикрепленных сеансов в nginx. Ниже показаны два подхода в зависимости от доступных возможностей.

В дополнение к предыдущей конфигурации добавляется следующее. В следующих примерах `backend` — это имя группы серверов.

С [открытым исходным кодом nginx](https://nginx.org/en/)используйте `ip_hash` для маршрутизации подключений к серверу на основе IP-адреса клиента:

```nginx
http {
  upstream backend {
    # App server 1
    server http://localhost:5000;
    # App server 2
    server http://localhost:5002;

    ip_hash;
  }
}
```

С помощью [nginx Plus](https://www.nginx.com/products/nginx)используйте, `sticky` чтобы добавить cookie запрос в запросы и закрепить запросы пользователя на сервере:

```nginx
http {
  upstream backend {
    # App server 1
    server http://localhost:5000;
    # App server 2
    server http://localhost:5002;

    sticky cookie srv_id expires=max domain=.example.com path=/ httponly;
  }
}
```

Наконец, измените `proxy_pass http://localhost:5000` в `server` разделе на `proxy_pass http://backend` .

Дополнительные сведения о WebSockets через nginx см. в разделе [nginx как прокси-сервер](https://www.nginx.com/blog/websocket-nginx).

Дополнительные сведения о балансировке нагрузки и закрепленных сеансах см. в разделе [nginx Load балансировка нагрузки](https://docs.nginx.com/nginx/admin-guide/load-balancer/http-load-balancer/).

Дополнительные сведения о ASP.NET Core с nginx см. в следующей статье:
* <xref:host-and-deploy/linux-nginx>

## <a name="third-party-no-locsignalr-backplane-providers"></a>Сторонние SignalR поставщики объединительной платы

* [NCache](https://www.alachisoft.com/ncache/asp-net-core-signalr.html)
* [Orleans](https://github.com/OrleansContrib/SignalR.Orleans)

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения см. в следующих ресурсах:

* [SignalRДокументация по службе Azure](/azure/azure-signalr/signalr-overview)
* [Настройка объединительной платы Redis](xref:signalr/redis-backplane)
