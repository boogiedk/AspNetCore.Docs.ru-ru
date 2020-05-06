---
title: Дополнительные Blazor сценарии безопасности ASP.NET Core Server
author: guardrex
description: Узнайте, как настроить Blazor сервер для дополнительных сценариев безопасности.
monikerRange: '>= aspnetcore-3.1'
ms.author: riande
ms.custom: mvc
ms.date: 04/27/2020
no-loc:
- Blazor
- Identity
- Let's Encrypt
- Razor
- SignalR
uid: security/blazor/server/additional-scenarios
ms.openlocfilehash: 95e9e57889fdbb5270f895874c9b8148ae4ca48d
ms.sourcegitcommit: 70e5f982c218db82aa54aa8b8d96b377cfc7283f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82772808"
---
# <a name="aspnet-core-blazor-server-additional-security-scenarios"></a><span data-ttu-id="aa4ab-103">Дополнительные Blazor сценарии безопасности ASP.NET Core Server</span><span class="sxs-lookup"><span data-stu-id="aa4ab-103">ASP.NET Core Blazor Server additional security scenarios</span></span>

<span data-ttu-id="aa4ab-104">Автор: [Javier Calvarro Nelson](https://github.com/javiercn) (Хавьер Кальварро Нельсон)</span><span class="sxs-lookup"><span data-stu-id="aa4ab-104">By [Javier Calvarro Nelson](https://github.com/javiercn)</span></span>

## <a name="pass-tokens-to-a-blazor-server-app"></a><span data-ttu-id="aa4ab-105">Передача маркеров в Blazor серверное приложение</span><span class="sxs-lookup"><span data-stu-id="aa4ab-105">Pass tokens to a Blazor Server app</span></span>

<span data-ttu-id="aa4ab-106">Токены, доступные за Razor пределами Blazor компонентов серверного приложения, можно передавать в компоненты с помощью подхода, описанного в этом разделе.</span><span class="sxs-lookup"><span data-stu-id="aa4ab-106">Tokens available outside of the Razor components in a Blazor Server app can be passed to components with the approach described in this section.</span></span> <span data-ttu-id="aa4ab-107">Пример кода, включая полный `Startup.ConfigureServices` пример, см. в разделе [Передача токенов в приложение на стороне Blazor сервера](https://github.com/javiercn/blazor-server-aad-sample).</span><span class="sxs-lookup"><span data-stu-id="aa4ab-107">For sample code, including a complete `Startup.ConfigureServices` example, see the [Passing tokens to a server-side Blazor application](https://github.com/javiercn/blazor-server-aad-sample).</span></span>

<span data-ttu-id="aa4ab-108">Проверяйте Blazor подлинность серверного приложения так же Razor , как обычные страницы или приложения MVC.</span><span class="sxs-lookup"><span data-stu-id="aa4ab-108">Authenticate the Blazor Server app as you would with a regular Razor Pages or MVC app.</span></span> <span data-ttu-id="aa4ab-109">Подготавливает и сохраняйте маркеры в файле cookie проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="aa4ab-109">Provision and save the tokens to the authentication cookie.</span></span> <span data-ttu-id="aa4ab-110">Например:</span><span class="sxs-lookup"><span data-stu-id="aa4ab-110">For example:</span></span>

```csharp
using Microsoft.AspNetCore.Authentication.OpenIdConnect;

...

services.Configure<OpenIdConnectOptions>(AzureADDefaults.OpenIdScheme, options =>
{
    options.ResponseType = "code";
    options.SaveTokens = true;

    options.Scope.Add("offline_access");
    options.Scope.Add("{SCOPE}");
    options.Resource = "{RESOURCE}";
});
```

<span data-ttu-id="aa4ab-111">Определите класс для передачи исходного состояния приложения с маркерами доступа и обновления:</span><span class="sxs-lookup"><span data-stu-id="aa4ab-111">Define a class to pass in the initial app state with the access and refresh tokens:</span></span>

```csharp
public class InitialApplicationState
{
    public string AccessToken { get; set; }
    public string RefreshToken { get; set; }
}
```

<span data-ttu-id="aa4ab-112">Определите службу поставщика маркеров с заданной **областью** , которую можно использовать Blazor в приложении для разрешения маркеров [путем внедрения зависимостей (DI)](xref:blazor/dependency-injection):</span><span class="sxs-lookup"><span data-stu-id="aa4ab-112">Define a **scoped** token provider service that can be used within the Blazor app to resolve the tokens from [dependency injection (DI)](xref:blazor/dependency-injection):</span></span>

```csharp
public class TokenProvider
{
    public string AccessToken { get; set; }
    public string RefreshToken { get; set; }
}
```

<span data-ttu-id="aa4ab-113">В `Startup.ConfigureServices`службах добавьте службы для:</span><span class="sxs-lookup"><span data-stu-id="aa4ab-113">In `Startup.ConfigureServices`, add services for:</span></span>

* `IHttpClientFactory`
* `TokenProvider`

```csharp
services.AddHttpClient();
services.AddScoped<TokenProvider>();
```

<span data-ttu-id="aa4ab-114">В файле *_Host. cshtml* создайте экземпляр `InitialApplicationState` и передайте его в качестве параметра в приложение:</span><span class="sxs-lookup"><span data-stu-id="aa4ab-114">In the *_Host.cshtml* file, create and instance of `InitialApplicationState` and pass it as a parameter to the app:</span></span>

```cshtml
@using Microsoft.AspNetCore.Authentication

...

@{
    var tokens = new InitialApplicationState
    {
        AccessToken = await HttpContext.GetTokenAsync("access_token"),
        RefreshToken = await HttpContext.GetTokenAsync("refresh_token")
    };
}

<app>
    <component type="typeof(App)" param-InitialState="tokens" 
        render-mode="ServerPrerendered" />
</app>
```

<span data-ttu-id="aa4ab-115">В `App` компоненте (*app. Razor*) разрешите службу и инициализируйте ее с помощью данных из параметра:</span><span class="sxs-lookup"><span data-stu-id="aa4ab-115">In the `App` component (*App.razor*), resolve the service and initialize it with the data from the parameter:</span></span>

```razor
@inject TokenProvider TokenProvider

...

@code {
    [Parameter]
    public InitialApplicationState InitialState { get; set; }

    protected override Task OnInitializedAsync()
    {
        TokenProvider.AccessToken = InitialState.AccessToken;
        TokenProvider.RefreshToken = InitialState.RefreshToken;

        return base.OnInitializedAsync();
    }
}
```

<span data-ttu-id="aa4ab-116">В службе, которая выполняет запрос безопасного API, вставьте поставщик маркера и получите маркер для вызова API:</span><span class="sxs-lookup"><span data-stu-id="aa4ab-116">In the service that makes a secure API request, inject the token provider and retrieve the token to call the API:</span></span>

```csharp
public class WeatherForecastService
{
    private readonly TokenProvider _store;

    public WeatherForecastService(IHttpClientFactory clientFactory, 
        TokenProvider tokenProvider)
    {
        Client = clientFactory.CreateClient();
        _store = tokenProvider;
    }

    public HttpClient Client { get; }

    public async Task<WeatherForecast[]> GetForecastAsync(DateTime startDate)
    {
        var token = _store.AccessToken;
        var request = new HttpRequestMessage(HttpMethod.Get, 
            "https://localhost:5003/WeatherForecast");
        request.Headers.Add("Authorization", $"Bearer {token}");
        var response = await Client.SendAsync(request);
        response.EnsureSuccessStatusCode();

        return await response.Content.ReadAsAsync<WeatherForecast[]>();
    }
}
```