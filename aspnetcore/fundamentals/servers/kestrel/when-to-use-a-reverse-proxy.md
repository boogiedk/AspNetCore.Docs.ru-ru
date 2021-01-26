---
title: Когда следует использовать обратный прокси-сервер с веб-сервером Kestrel для ASP.NET Core
author: rick-anderson
description: Дополнительные сведения о том, когда следует использовать обратный прокси-сервер перед Kestrel, кроссплатформенным веб-сервером для ASP.NET Core.
monikerRange: '>= aspnetcore-5.0'
ms.author: riande
ms.custom: mvc
ms.date: 01/14/2021
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
uid: fundamentals/servers/kestrel/when-to-use-a-reverse-proxy
ms.openlocfilehash: fc89a9f841403bbccedff0a9c0720a08c11abdd6
ms.sourcegitcommit: 063a06b644d3ade3c15ce00e72a758ec1187dd06
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2021
ms.locfileid: "98253856"
---
# <a name="when-to-use-kestrel-with-a-reverse-proxy"></a>Условия использования Kestrel с обратным прокси-сервером

Kestrel можно использовать отдельно или с *обратным прокси-сервером*, таким как [IIS](https://www.iis.net/), [Nginx](https://nginx.org) или [Apache](https://httpd.apache.org/). Обратный прокси-сервер получает HTTP-запросы из сети и пересылает их в Kestrel.

Kestrel используется в качестве веб-сервера перехода (с выходом в Интернет).

![Kestrel взаимодействует с Интернетом напрямую, без обратного прокси-сервера](_static/kestrel-to-internet2.png)

Kestrel используется в конфигурации обратного прокси-сервера.

![Kestrel взаимодействует с Интернетом косвенно, через обратный прокси-сервер, такой как IIS, Nginx или Apache.](_static/kestrel-to-internet.png)

Любая из этих конфигураций — с обратным прокси-сервером и без него — является поддерживаемой конфигурацией для размещения.

Kestrel, используемый в качестве пограничного сервера без обратного прокси-сервера, не поддерживает общий доступ нескольких процессов к одним и тем же IP-адресам и портам. Когда Kestrel настроен на ожидание передачи данных от порта, Kestrel обрабатывает весь трафик для этого порта независимо от заголовка `Host` запросов. Поэтому обратный прокси-сервер, который может совместно использовать порты, способен пересылать запросы в Kestrel с уникальным IP-адресом и портом.

Даже если обратный прокси-сервер не требуется, его использование может оказаться удобным.

Обратный прокси-сервер:

* Может ограничить общедоступную контактную зону размещенных на нем приложений.
* Предоставляет дополнительный уровень конфигурации и защиты.
* Может лучше интегрироваться с существующей инфраструктурой.
* Упрощает настройку балансировки нагрузки и безопасных подключений (HTTPS). Сертификат X.509 требуется только обратному прокси-серверу, а сам этот сервер может обмениваться данными с серверами приложения во внутренней сети по обычному протоколу HTTP.

> [!WARNING]
> Для размещения в конфигурации обратного прокси-сервера требуется [фильтрация узлов](xref:fundamentals/servers/kestrel/host-filtering).

## <a name="additional-resources"></a>Дополнительные ресурсы

<xref:host-and-deploy/proxy-load-balancer>
