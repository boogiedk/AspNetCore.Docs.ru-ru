---
title: Хттпрепл телеметрии
author: scottaddie
description: Сведения о телеметрии, собираемых Хттпрепл.
monikerRange: '>= aspnetcore-2.1'
ms.author: scaddie
ms.date: 11/11/2020
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
uid: web-api/http-repl/telemetry
ms.openlocfilehash: 5ff22753f566c494e51dae67c8c4f6371211be78
ms.sourcegitcommit: 202144092067ea81be1dbb229329518d781dbdfb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/12/2020
ms.locfileid: "94550612"
---
# <a name="httprepl-telemetry"></a>Хттпрепл телеметрии

[Хттпрепл](xref:web-api/http-repl) включает функцию телеметрии, которая собирает данные об использовании. Важно, чтобы команда Хттпрепл могла улучшить работу средства.

## <a name="how-to-opt-out"></a>Как отключить функцию

Функция телеметрии Хттпрепл включена по умолчанию. Чтобы отключить ее, присвойте переменной среды `DOTNET_HTTPREPL_TELEMETRY_OPTOUT` значение `1` или `true`.

## <a name="disclosure"></a>Раскрытие информации

При первом запуске средства Хттпрепл отображает текст, аналогичный приведенному ниже. Текст может немного отличаться в зависимости от используемой версии инструмента. Именно таким образом корпорация Майкрософт уведомляет вас о сборе данных.

```console
Telemetry
---------
The .NET tools collect usage data in order to help us improve your experience. It is collected by Microsoft and shared with the community. You can opt-out of telemetry by setting the DOTNET_HTTPREPL_TELEMETRY_OPTOUT environment variable to '1' or 'true' using your favorite shell.
```

Чтобы отключить текст "первый запуск", задайте `DOTNET_HTTPREPL_SKIP_FIRST_TIME_EXPERIENCE` для переменной среды значение `1` или `true` .

## <a name="data-points"></a>Точки данных

Функция телеметрии не:

* Собирайте персональные данные, такие как имена пользователей, адреса электронной почты или URL-адреса.
* Проверка HTTP-запросов или ответов.

Данные безопасно передаются на серверы Майкрософт и удерживаются в ограниченном доступе.

Мы заботимся о вашей конфиденциальности. Если вы подозреваете, что функция телеметрии собирает конфиденциальные данные, или что данные не являются безопасными или несоответствующим образом обрабатываются, выполните одно из следующих действий.

* Заполните ошибку в репозитории [DotNet/хттпрепл](https://github.com/dotnet/httprepl/issues) .
* Отправьте сообщение по электронной почте [dotnet@microsoft.com](mailto:dotnet@microsoft.com) для изучения.

Функция телеметрии собирает следующие данные.

| Версии пакета SDK для .NET | Данные |
|--------------|------|
| >= 5,0        | Метка времени вызова. |
| >= 5,0        | IP-адрес из трех октетов, используемый для определения географического расположения. |
| >= 5,0        | Операционная система и ее версия. |
| >= 5,0        | Идентификатор среды выполнения (RID), в которой работает средство. |
| >= 5,0        | Выполняется ли средство в контейнере. |
| >= 5,0        | Хэшированный контроль доступа к носителю (MAC): криптографический (SHA256) хэшированный и уникальный идентификатор для компьютера. |
| >= 5,0        | Версия ядра. |
| >= 5,0        | Версия Хттпрепл. |
| >= 5,0        | Было ли средство запущено с `help` `run` `connect` аргументами, или. Фактические значения аргументов не собираются. |
| >= 5,0        | Вызванная команда (например, `get` ) и ее успешность. |
| >= 5,0        | Для `connect` команды, указывает, `root` были ли `base` `openapi` предоставлены аргументы, или. Фактические значения аргументов не собираются. |
| >= 5,0        | Для `pref` команды — независимо от того, была ли выполнена команда `get` или `set` и к какой предпочтению осуществлялся доступ. Если нет хорошо известных предпочтений, имя хэшируется. Значение не собираются. |
| >= 5,0        | Для `set header` команды задается имя заголовка. Если не является хорошо известным заголовком, имя хэшируется. Значение не собираются. |
| >= 5,0        | Для `connect` команды — используется ли особый случай для `dotnet new webapi` , и, является ли он обходится с помощью предпочтений. |
| >= 5,0        | Для всех команд HTTP (например, GET, POST, WHERE) указывается, задан ли каждый из параметров. Значения параметров не собираются. |

## <a name="additional-resources"></a>Дополнительные ресурсы

* [Телеметрия пакета SDK для .NET Core](/dotnet/core/tools/telemetry)
* [.NET Core CLI данных телеметрии](https://dotnet.microsoft.com/platform/telemetry)