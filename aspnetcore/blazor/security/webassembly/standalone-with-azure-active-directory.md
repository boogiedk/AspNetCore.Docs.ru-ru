---
title: Защита изолированного приложения ASP.NET Core Blazor WebAssembly с помощью Azure Active Directory
author: guardrex
description: ''
monikerRange: '>= aspnetcore-3.1'
ms.author: riande
ms.custom: mvc
ms.date: 05/19/2020
no-loc:
- Blazor
- Identity
- Let's Encrypt
- Razor
- SignalR
uid: blazor/security/webassembly/standalone-with-azure-active-directory
ms.openlocfilehash: 4b03468d04c96ce90b84ab3c86709f266df187a7
ms.sourcegitcommit: 490434a700ba8c5ed24d849bd99d8489858538e3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2020
ms.locfileid: "85103495"
---
# <a name="secure-an-aspnet-core-blazor-webassembly-standalone-app-with-azure-active-directory"></a>Защита изолированного приложения ASP.NET Core Blazor WebAssembly с помощью Azure Active Directory

Авторы: [Хавьер Кальварро Нельсон](https://github.com/javiercn) (Javier Calvarro Nelson) и [Люк Латэм](https://github.com/guardrex) (Luke Latham)

Чтобы создать изолированное приложение Blazor WebAssembly, использующее [Azure Active Directory (AAD](https://azure.microsoft.com/services/active-directory/)) для проверки подлинности, выполните приведенные ниже действия.

[Создайте клиент AAD и веб-приложение](/azure/active-directory/develop/v2-overview):

Зарегистрируйте приложение AAD на портале Azure в разделе ****Azure Active Directory** > Регистрация приложений**.

1. Укажите **имя** приложения (например, **BlazorИзолированный AAD**).
1. Выберите **поддерживаемые типы учетных записей**. Можно выбрать **Учетные записи только в этом каталоге организации**.
1. В раскрывающемся списке **URI перенаправления** оставьте значение **Интернет** и укажите следующий URI перенаправления: `https://localhost:{PORT}/authentication/login-callback`. Порт по умолчанию для приложения, работающего на Kestrel, — 5001. Если приложение выполняется на другом порте Kestrel, используйте порт приложения. Для IIS Express созданный случайным образом порт для приложения указан в свойствах приложения на панели **Отладка**. Поскольку на этом этапе приложение не существует и порт IIS Express неизвестен, вернитесь к этому шагу после создания приложения и обновите URI перенаправления. В этом разделе появится замечание с напоминанием для пользователей IIS Express о необходимости обновить URI перенаправления.
1. Снимите флажок **Разрешения** > **Предоставьте согласие администратора для разрешений openid и offline_access**.
1. Выберите **Зарегистрировать**.

Запишите следующие сведения:

* Идентификатор приложения (идентификатор клиента) (например, `11111111-1111-1111-1111-111111111111`)
* Идентификатор каталога (идентификатор клиента) (например, `22222222-2222-2222-2222-222222222222`)

В разделе **Проверка подлинности** > **Конфигурации платформы** > **Интернет** выполните следующие действия.

1. Убедитесь в том, что параметру **URI-перенаправления** присвоено значение `https://localhost:{PORT}/authentication/login-callback`.
1. В разделе **Неявное предоставление разрешения** установите флажки **Маркеры доступа** и **Токен идентификатора**.
1. Для остальных параметров можно оставить значения по умолчанию.
1. Нажмите кнопку **Сохранить**.

Создайте приложение. Замените заполнители в следующей команде на записанные ранее сведения и выполните команду в командной оболочке:

```dotnetcli
dotnet new blazorwasm -au SingleOrg --client-id "{CLIENT ID}" --tenant-id "{TENANT ID}"
```

Чтобы указать расположение выходных данных для создания папки проекта, если она не существует, включите в команду параметр выходных данных с путем (например, `-o BlazorSample`). Имя папки также станет частью имени проекта.

> [!NOTE]
> На портале Azure в разделе **Проверка подлинности** > **Конфигурации платформы** > **Интернет** > **URI перенаправления** в качестве порта для приложений, выполняющихся на сервере Kestrel с параметрами по умолчанию, задан порт 5001.
>
> Если приложение выполняется на случайном порту IIS Express, порт для приложения указан в свойствах приложения на панели **Отладка**.
>
> Если порт не был настроен ранее с помощью известного порта приложения, вернитесь к регистрации приложения на портале Azure и обновите URI перенаправления, указав правильный порт.

После создания приложения вы сможете:

* Входить в приложение, используя учетную запись пользователя AAD.
* Запрашивать маркеры доступа для API Майкрософт. Дополнительные сведения можно найти в разделе
  * [Области маркеров доступа](#access-token-scopes)
  * [Краткое руководство. Настройка приложения для предоставления интерфейсов веб-API](/azure/active-directory/develop/quickstart-configure-app-expose-web-apis).

## <a name="authentication-package"></a>Пакет проверки подлинности

Когда приложение создается для использования рабочих или учебных учетных записей (`SingleOrg`), оно автоматически получает ссылку на пакет для [библиотеки проверки подлинности Майкрософт](/azure/active-directory/develop/msal-overview) ([Microsoft.Authentication.WebAssembly.Msal](https://www.nuget.org/packages/Microsoft.Authentication.WebAssembly.Msal/)). В пакете содержится набор примитивов, которые помогают приложению проверять подлинность пользователей и получать маркеры для вызова защищенных API.

При добавлении проверки подлинности в приложение вручную добавьте пакет в файл проекта приложения:

```xml
<PackageReference Include="Microsoft.Authentication.WebAssembly.Msal" 
  Version="3.2.0" />
```

Пакет [Microsoft.Authentication.WebAssembly.Msal](https://www.nuget.org/packages/Microsoft.Authentication.WebAssembly.Msal/) транзитивно добавляет в приложение пакет [Microsoft.AspNetCore.Components.WebAssembly.Authentication](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.WebAssembly.Authentication/).

## <a name="authentication-service-support"></a>Поддержка службы проверки подлинности

Поддержка проверки подлинности пользователей регистрируется в контейнере службы с помощью метода расширения <xref:Microsoft.Extensions.DependencyInjection.MsalWebAssemblyServiceCollectionExtensions.AddMsalAuthentication%2A>, предоставляемого в пакете [Microsoft.Authentication.WebAssembly.Msal](https://www.nuget.org/packages/Microsoft.Authentication.WebAssembly.Msal/). Этот метод настраивает службы, необходимые для взаимодействия приложения с поставщиком Identity (IP).

*Program.cs*:

```csharp
builder.Services.AddMsalAuthentication(options =>
{
    builder.Configuration.Bind("AzureAd", options.ProviderOptions.Authentication);
});
```

Метод <xref:Microsoft.Extensions.DependencyInjection.MsalWebAssemblyServiceCollectionExtensions.AddMsalAuthentication%2A> принимает обратный вызов для настройки параметров, необходимых для проверки подлинности приложения. Значения, необходимые для настройки приложения, можно получить из конфигурации AAD при регистрации приложения.

Конфигурация предоставляется файлом *wwwroot/appsettings.json*:

```json
{
  "AzureAd": {
    "Authority": "https://login.microsoftonline.com/{TENANT ID}",
    "ClientId": "{CLIENT ID}",
    "ValidateAuthority": true
  }
}
```

Пример.

```json
{
  "AzureAd": {
    "Authority": "https://login.microsoftonline.com/e86c78e2-...-918e0565a45e",
    "ClientId": "41451fa7-82d9-4673-8fa5-69eff5a761fd",
    "ValidateAuthority": true
  }
}
```

## <a name="access-token-scopes"></a>Области маркеров доступа

Шаблон Blazor WebAssembly не обеспечивает автоматическую настройку приложения для запроса маркера доступа для защищенного API. Чтобы настроить маркер доступа как часть потока входа, добавьте область в области маркера доступа по умолчанию <xref:Microsoft.Authentication.WebAssembly.Msal.Models.MsalProviderOptions>:

```csharp
builder.Services.AddMsalAuthentication(options =>
{
    ...
    options.ProviderOptions.DefaultAccessTokenScopes.Add("{SCOPE URI}");
});
```

[!INCLUDE[](~/includes/blazor-security/azure-scope.md)]

Дополнительные сведения см. в следующих разделах статьи *Дополнительные сценарии*:

* [Запрашивание дополнительных маркеров доступа](xref:blazor/security/webassembly/additional-scenarios#request-additional-access-tokens)
* [Присоединение маркеров к исходящим запросам](xref:blazor/security/webassembly/additional-scenarios#attach-tokens-to-outgoing-requests)

## <a name="imports-file"></a>Файл импорта

[!INCLUDE[](~/includes/blazor-security/imports-file-standalone.md)]

## <a name="index-page"></a>Страница индексов

[!INCLUDE[](~/includes/blazor-security/index-page-msal.md)]

## <a name="app-component"></a>Компонент приложения

[!INCLUDE[](~/includes/blazor-security/app-component.md)]

## <a name="redirecttologin-component"></a>Компонент RedirectToLogin

[!INCLUDE[](~/includes/blazor-security/redirecttologin-component.md)]

## <a name="logindisplay-component"></a>Компонент LoginDisplay

[!INCLUDE[](~/includes/blazor-security/logindisplay-component.md)]

## <a name="authentication-component"></a>Компонент проверки подлинности

[!INCLUDE[](~/includes/blazor-security/authentication-component.md)]

[!INCLUDE[](~/includes/blazor-security/troubleshoot.md)]

## <a name="additional-resources"></a>Дополнительные ресурсы

* <xref:blazor/security/webassembly/additional-scenarios>
* [Запросы веб-API, не прошедшие проверку подлинности или неавторизованные, в приложении с защищенным клиентом по умолчанию](xref:blazor/security/webassembly/additional-scenarios#unauthenticated-or-unauthorized-web-api-requests-in-an-app-with-a-secure-default-client)
* <xref:blazor/security/webassembly/aad-groups-roles>
* <xref:security/authentication/azure-active-directory/index>
* [Документация по платформе удостоверений Майкрософт](/azure/active-directory/develop/)