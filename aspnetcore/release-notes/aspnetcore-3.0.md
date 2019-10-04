---
title: Новые возможности в ASP.NET Core 3.0
author: rick-anderson
description: Сведения о новых возможностях в ASP.NET Core 3.0.
ms.author: riande
ms.custom: mvc
ms.date: 09/26/2019
uid: aspnetcore-3.0
ms.openlocfilehash: ec3de5b35883752b7b3dbefceccec55da3986f39
ms.sourcegitcommit: dc96d76f6b231de59586fcbb989a7fb5106d26a8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2019
ms.locfileid: "71703683"
---
# <a name="whats-new-in-aspnet-core-30"></a><span data-ttu-id="6b7c4-103">Новые возможности в ASP.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="6b7c4-103">What's new in ASP.NET Core 3.0</span></span>

<span data-ttu-id="6b7c4-104">В этой статье описываются наиболее важные изменения в ASP.NET Core 3.0 со ссылками на соответствующую документацию.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-104">This article highlights the most significant changes in ASP.NET Core 3.0 with links to relevant documentation.</span></span>

## <a name="blazor"></a><span data-ttu-id="6b7c4-105">Blazor</span><span class="sxs-lookup"><span data-stu-id="6b7c4-105">Blazor</span></span>

<span data-ttu-id="6b7c4-106">Blazor — это новая платформа в ASP.NET Core, предназначенная для создания интерактивного веб-интерфейса на стороне клиента с использованием .NET. Она предлагает следующие возможности:</span><span class="sxs-lookup"><span data-stu-id="6b7c4-106">Blazor is a new framework in ASP.NET Core for building interactive client-side web UI with .NET:</span></span>

* <span data-ttu-id="6b7c4-107">создание многофункциональных интерактивных пользовательских интерфейсов на C# вместо JavaScript;</span><span class="sxs-lookup"><span data-stu-id="6b7c4-107">Create rich interactive UIs using C# instead of JavaScript.</span></span>
* <span data-ttu-id="6b7c4-108">совместное использование серверной и клиентской логик приложений, написанных с помощью .NET;</span><span class="sxs-lookup"><span data-stu-id="6b7c4-108">Share server-side and client-side app logic written in .NET.</span></span>
* <span data-ttu-id="6b7c4-109">отображение пользовательского интерфейса в виде HTML-страницы с CSS для широкой поддержки браузеров, в том числе для мобильных устройств.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-109">Render the UI as HTML and CSS for wide browser support, including mobile browsers.</span></span>

<span data-ttu-id="6b7c4-110">Поддерживаемые сценарии платформы Blazor:</span><span class="sxs-lookup"><span data-stu-id="6b7c4-110">Blazor framework supported scenarios:</span></span>

* <span data-ttu-id="6b7c4-111">повторно используемые компоненты пользовательского интерфейса (компоненты Razor);</span><span class="sxs-lookup"><span data-stu-id="6b7c4-111">Reusable UI components (Razor components)</span></span>
* <span data-ttu-id="6b7c4-112">маршрутизация на стороне клиента;</span><span class="sxs-lookup"><span data-stu-id="6b7c4-112">Client-side routing</span></span>
* <span data-ttu-id="6b7c4-113">макеты компонентов;</span><span class="sxs-lookup"><span data-stu-id="6b7c4-113">Component layouts</span></span>
* <span data-ttu-id="6b7c4-114">поддержка внедрения зависимостей;</span><span class="sxs-lookup"><span data-stu-id="6b7c4-114">Support for dependency injection</span></span>
* <span data-ttu-id="6b7c4-115">Формы и проверка</span><span class="sxs-lookup"><span data-stu-id="6b7c4-115">Forms and validation</span></span>
* <span data-ttu-id="6b7c4-116">создание библиотек компонентов с помощью библиотек классов Razor;</span><span class="sxs-lookup"><span data-stu-id="6b7c4-116">Build component libraries with Razor class libraries</span></span>
* <span data-ttu-id="6b7c4-117">Взаимодействие с JavaScript</span><span class="sxs-lookup"><span data-stu-id="6b7c4-117">JavaScript interop</span></span>

<span data-ttu-id="6b7c4-118">Дополнительные сведения можно найти по адресу: <xref:blazor/index>.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-118">For more information, see <xref:blazor/index>.</span></span>

### <a name="blazor-server"></a><span data-ttu-id="6b7c4-119">Blazor Server</span><span class="sxs-lookup"><span data-stu-id="6b7c4-119">Blazor Server</span></span>

<span data-ttu-id="6b7c4-120">Blazor отделяет логику отображения компонентов от того, как применяются обновления пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-120">Blazor decouples component rendering logic from how UI updates are applied.</span></span> <span data-ttu-id="6b7c4-121">Blazor Server предоставляет поддержку размещения компонентов Razor на сервере в приложении ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-121">Blazor Server provides support for hosting Razor components on the server in an ASP.NET Core app.</span></span> <span data-ttu-id="6b7c4-122">Обновления пользовательского интерфейса обрабатываются через подключение SignalR.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-122">UI updates are handled over a SignalR connection.</span></span> <span data-ttu-id="6b7c4-123">Серверное приложение Blazor поддерживается только в ASP.NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-123">Blazor Server is supported in ASP.NET Core 3.0.</span></span>

### <a name="blazor-webassembly-preview"></a><span data-ttu-id="6b7c4-124">WebAssembly Blazor (предварительная версия)</span><span class="sxs-lookup"><span data-stu-id="6b7c4-124">Blazor WebAssembly (Preview)</span></span>

<span data-ttu-id="6b7c4-125">Приложения Blazor можно также запускать непосредственно в браузере с использованием среды выполнения .NET на основе WebAssembly.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-125">Blazor apps can also be run directly in the browser using a WebAssembly-based .NET runtime.</span></span> <span data-ttu-id="6b7c4-126">WebAssembly Blazor доступна в режиме предварительной версии и *не* поддерживается в ASP.NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-126">Blazor WebAssembly is in preview and *not* supported in ASP.NET Core 3.0.</span></span> <span data-ttu-id="6b7c4-127">WebAssembly Blazor будет поддерживаться в будущем выпуске ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-127">Blazor WebAssembly will be supported in a future release of ASP.NET Core.</span></span>

### <a name="razor-components"></a><span data-ttu-id="6b7c4-128">Компоненты Razor</span><span class="sxs-lookup"><span data-stu-id="6b7c4-128">Razor components</span></span>

<span data-ttu-id="6b7c4-129">Приложения Blazor создаются на основе компонентов.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-129">Blazor apps are built from components.</span></span> <span data-ttu-id="6b7c4-130">Компоненты — это автономные блоки пользовательского интерфейса, такие как страница, диалоговое окно или форма.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-130">Components are self-contained chunks of user interface (UI), such as a page, dialog, or form.</span></span> <span data-ttu-id="6b7c4-131">Это обычные классы .NET, определяющие логику отрисовки пользовательского интерфейса и обработчики событий на стороне клиента.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-131">Components are normal .NET classes that define UI rendering logic and client-side event handlers.</span></span> <span data-ttu-id="6b7c4-132">Многофункциональные интерактивные веб-приложения можно создавать без JavaScript.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-132">You can create rich interactive web apps without JavaScript.</span></span>

<span data-ttu-id="6b7c4-133">Компоненты в Blazor обычно создаются с помощью синтаксиса Razor, естественного сочетания HTML и C#.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-133">Components in Blazor are typically authored using Razor syntax, a natural blend of HTML and C#.</span></span> <span data-ttu-id="6b7c4-134">Компоненты Razor похожи на Razor Pages и представления MVC тем, что они используют Razor.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-134">Razor components are similar to Razor Pages and MVC views in that they both use Razor.</span></span> <span data-ttu-id="6b7c4-135">В отличие от страниц и представлений, которые созданы на базе модели "запрос и ответ", компоненты используются исключительно для обработки компоновки пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-135">Unlike pages and views, which are based on a request-response model, components are used specifically for handling UI composition.</span></span>

## <a name="grpc"></a><span data-ttu-id="6b7c4-136">gRPC</span><span class="sxs-lookup"><span data-stu-id="6b7c4-136">gRPC</span></span>

<span data-ttu-id="6b7c4-137">[gRPC](https://grpc.io/):</span><span class="sxs-lookup"><span data-stu-id="6b7c4-137">[gRPC](https://grpc.io/):</span></span>

* <span data-ttu-id="6b7c4-138">это популярная высокопроизводительная платформа RPC (удаленный вызов процедур).</span><span class="sxs-lookup"><span data-stu-id="6b7c4-138">Is a popular, high-performance RPC (remote procedure call) framework.</span></span>
* <span data-ttu-id="6b7c4-139">Для разработки API используется подход, при котором сначала создается контракт.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-139">Offers an opinionated contract-first approach to API development.</span></span>
* <span data-ttu-id="6b7c4-140">Использует современные технологии, такие как:</span><span class="sxs-lookup"><span data-stu-id="6b7c4-140">Uses modern technologies such as:</span></span>

  * <span data-ttu-id="6b7c4-141">HTTP/2 для транспортировки;</span><span class="sxs-lookup"><span data-stu-id="6b7c4-141">HTTP/2 for transport.</span></span>
  * <span data-ttu-id="6b7c4-142">буферы протоколов в качестве языка описания интерфейса;</span><span class="sxs-lookup"><span data-stu-id="6b7c4-142">Protocol Buffers as the interface description language.</span></span>
  * <span data-ttu-id="6b7c4-143">формат двоичной сериализации.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-143">Binary serialization format.</span></span>
* <span data-ttu-id="6b7c4-144">Предоставляет следующие возможности:</span><span class="sxs-lookup"><span data-stu-id="6b7c4-144">Provides features such as:</span></span>

  * <span data-ttu-id="6b7c4-145">Проверка подлинности</span><span class="sxs-lookup"><span data-stu-id="6b7c4-145">Authentication</span></span>
  * <span data-ttu-id="6b7c4-146">двунаправленная потоковая передача и управление потоком;</span><span class="sxs-lookup"><span data-stu-id="6b7c4-146">Bidirectional streaming and flow control.</span></span>
  * <span data-ttu-id="6b7c4-147">отмена и время ожидания.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-147">Cancellation and timeouts.</span></span>

<span data-ttu-id="6b7c4-148">К функциям gRPC в ASP.NET Core 3.0 относятся:</span><span class="sxs-lookup"><span data-stu-id="6b7c4-148">gRPC functionality in ASP.NET Core 3.0 includes:</span></span>

* <span data-ttu-id="6b7c4-149">[Grpc.AspNetCore](https://www.nuget.org/packages/Grpc.AspNetCore) — платформа ASP.NET Core для размещения служб gRPC.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-149">[Grpc.AspNetCore](https://www.nuget.org/packages/Grpc.AspNetCore) &ndash; An ASP.NET Core framework for hosting gRPC services.</span></span> <span data-ttu-id="6b7c4-150">gRPC в ASP.NET Core поддерживает интеграцию со стандартными возможностями ASP.NET Core, такими как ведение журнала, внедрение зависимостей, проверка подлинности и авторизация.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-150">gRPC on ASP.NET Core integrates with standard ASP.NET Core features like logging, dependency injection (DI), authentication and authorization.</span></span>
* <span data-ttu-id="6b7c4-151">[Grpc.Net.Client](https://www.nuget.org/packages/Grpc.Net.Client) — клиент gRPC для .NET Core, созданный на основе знакомого `HttpClient`.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-151">[Grpc.Net.Client](https://www.nuget.org/packages/Grpc.Net.Client) &ndash; A gRPC client for .NET Core that builds upon the familiar `HttpClient`.</span></span>
* <span data-ttu-id="6b7c4-152">[Grpc.Net.ClientFactory](https://www.nuget.org/packages/Grpc.Net.ClientFactory) — интеграция клиента gRPC с `HttpClientFactory`.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-152">[Grpc.Net.ClientFactory](https://www.nuget.org/packages/Grpc.Net.ClientFactory) &ndash; gRPC client integration with `HttpClientFactory`.</span></span>

<span data-ttu-id="6b7c4-153">Дополнительные сведения можно найти по адресу: <xref:grpc/index>.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-153">For more information, see <xref:grpc/index>.</span></span>

## <a name="signalr"></a><span data-ttu-id="6b7c4-154">SignalR</span><span class="sxs-lookup"><span data-stu-id="6b7c4-154">SignalR</span></span>

<span data-ttu-id="6b7c4-155">Инструкции по миграции см. в разделе [SignalR](xref:migration/22-to-30#signalr).</span><span class="sxs-lookup"><span data-stu-id="6b7c4-155">See [Update SignalR code](xref:migration/22-to-30#signalr) for migration instructions.</span></span> <span data-ttu-id="6b7c4-156">Для сериализации и десериализации сообщений JSON SignalR теперь использует `System.Text.Json`.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-156">SignalR now uses `System.Text.Json` to serialize/deserialize JSON messages.</span></span> <span data-ttu-id="6b7c4-157">Инструкции по восстановлению сериализатора на основе `Newtonsoft.Json` см. в разделе [Switch to Newtonsoft.Json](xref:migration/22-to-30#switch-to-newtonsoftjson) (Переключение на Newtonsoft.JSON).</span><span class="sxs-lookup"><span data-stu-id="6b7c4-157">See [Switch to Newtonsoft.Json](xref:migration/22-to-30#switch-to-newtonsoftjson) for instructions to restore the `Newtonsoft.Json`-based serializer.</span></span>

<span data-ttu-id="6b7c4-158">В клиентах JavaScript и .NET для SignalR добавлена поддержка автоматического повторного подключения.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-158">In the JavaScript and .NET Clients for SignalR, support was added for automatic reconnection.</span></span> <span data-ttu-id="6b7c4-159">По умолчанию клиент пытается немедленно заново подключиться и повторить попытку через 2, 10 и 30 секунд при необходимости.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-159">By default, the client tries to reconnect immediately and retry after 2, 10, and 30 seconds if necessary.</span></span> <span data-ttu-id="6b7c4-160">Если клиент успешно повторно подключается, он получает новый идентификатор подключения.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-160">If the client successfully reconnects, it receives a new connection ID.</span></span> <span data-ttu-id="6b7c4-161">Автоматическое повторное подключение необходимо явно выбирать:</span><span class="sxs-lookup"><span data-stu-id="6b7c4-161">Automatic reconnect is opt-in:</span></span>

```javascript
const connection = new signalR.HubConnectionBuilder()
    .withUrl("/chatHub")
    .withAutomaticReconnect()
    .build();
```

<span data-ttu-id="6b7c4-162">Интервалы повторного подключения можно указать, передав массив длительности в миллисекундах:</span><span class="sxs-lookup"><span data-stu-id="6b7c4-162">The reconnection intervals can be specified by passing an array of millisecond-based durations:</span></span>

```javascript
.withAutomaticReconnect([0, 3000, 5000, 10000, 15000, 30000])
//.withAutomaticReconnect([0, 2000, 10000, 30000]) The default intervals.
```

<span data-ttu-id="6b7c4-163">Пользовательскую реализацию можно передать для полного управления интервалами повторного подключения.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-163">A custom implementation can be passed in for full control of the reconnection intervals.</span></span>

<span data-ttu-id="6b7c4-164">Если повторное подключение не удается выполнить после последнего интервала повторного подключения:</span><span class="sxs-lookup"><span data-stu-id="6b7c4-164">If the reconnection fails after the last reconnect interval:</span></span>

* <span data-ttu-id="6b7c4-165">клиент считает, что подключение находится в автономном режиме;</span><span class="sxs-lookup"><span data-stu-id="6b7c4-165">The client considers the connection is offline.</span></span>
* <span data-ttu-id="6b7c4-166">клиент прекращает попытки повторного подключения.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-166">The client stops trying to reconnect.</span></span>

<span data-ttu-id="6b7c4-167">Во время повторных попыток подключения обновите пользовательский интерфейс приложения, чтобы уведомить пользователя о попытке повторного подключения.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-167">During reconnection attempts, update the app UI to notify the user that the reconnection is being attempted.</span></span>

<span data-ttu-id="6b7c4-168">Чтобы обеспечить возможность отправлять отзывы о пользовательском интерфейсе при прерывании подключения, в API клиента SignalR добавлены следующие обработчики событий:</span><span class="sxs-lookup"><span data-stu-id="6b7c4-168">To provide UI feedback when the connection is interrupted, the SignalR client API has been expanded to include the following event handlers:</span></span>

* <span data-ttu-id="6b7c4-169">`onreconnecting`.  Дает разработчикам возможность отключить пользовательский интерфейс или сообщить пользователям о том, что приложение находится в автономном режиме.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-169">`onreconnecting`:  Gives developers an opportunity to disable UI or to let users know the app is offline.</span></span>
* <span data-ttu-id="6b7c4-170">`onreconnected`. Предоставляет разработчикам возможность обновлять пользовательский интерфейс после повторного установления соединения.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-170">`onreconnected`: Gives developers an opportunity to update the UI once the connection is reestablished.</span></span>

<span data-ttu-id="6b7c4-171">Следующий код использует `onreconnecting` для обновления пользовательского интерфейса при попытке подключения:</span><span class="sxs-lookup"><span data-stu-id="6b7c4-171">The following code uses `onreconnecting` to update the UI while trying to connect:</span></span>

```javascript
connection.onreconnecting((error) => {
    const status = `Connection lost due to error "${error}". Reconnecting.`;
    document.getElementById("messageInput").disabled = true;
    document.getElementById("sendButton").disabled = true;
    document.getElementById("connectionStatus").innerText = status;
});
```

<span data-ttu-id="6b7c4-172">Следующий код использует `onreconnected` для обновления пользовательского интерфейса при подключении:</span><span class="sxs-lookup"><span data-stu-id="6b7c4-172">The following code uses `onreconnected` to update the UI on connection:</span></span>

```javascript
connection.onreconnected((connectionId) => {
    const status = `Connection reestablished. Connected.`;
    document.getElementById("messageInput").disabled = false;
    document.getElementById("sendButton").disabled = false;
    document.getElementById("connectionStatus").innerText = status;
});
```

<span data-ttu-id="6b7c4-173">SignalR 3.0 и более поздних версий предоставляют пользовательский ресурс для обработчиков авторизации, когда методу концентратора требуется авторизация.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-173">SignalR 3.0 and later provides a custom resource to authorization handlers when a hub method requires authorization.</span></span> <span data-ttu-id="6b7c4-174">Ресурс является экземпляром `HubInvocationContext`.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-174">The resource is an instance of `HubInvocationContext`.</span></span> <span data-ttu-id="6b7c4-175">`HubInvocationContext` включает:</span><span class="sxs-lookup"><span data-stu-id="6b7c4-175">The `HubInvocationContext` includes the:</span></span>

* `HubCallerContext`
* <span data-ttu-id="6b7c4-176">Имя вызываемого метода концентратора.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-176">Name of the hub method being invoked.</span></span>
* <span data-ttu-id="6b7c4-177">Аргументы для метода концентратора.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-177">Arguments to the hub method.</span></span>

<span data-ttu-id="6b7c4-178">Рассмотрим следующий пример приложения чата, разрешающего вход нескольких организаций с помощью Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-178">Consider the following example of a chat room app allowing multiple organization sign-in via Azure Active Directory.</span></span> <span data-ttu-id="6b7c4-179">Любой пользователь с учетной записью Майкрософт может войти в чат, но запрещать пользователям принимать участие в обсуждениях или просматривать журналы чата пользователей могут только члены владеющей организации.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-179">Anyone with a Microsoft account can sign in to chat, but only members of the owning organization can ban users or view users’ chat histories.</span></span> <span data-ttu-id="6b7c4-180">Приложение может ограничивать определенные функции для определенных пользователей.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-180">The app could restrict certain functionality from specific users.</span></span>

```csharp
public class DomainRestrictedRequirement :
    AuthorizationHandler<DomainRestrictedRequirement, HubInvocationContext>,
    IAuthorizationRequirement
{
    protected override Task HandleRequirementAsync(AuthorizationHandlerContext context,
        DomainRestrictedRequirement requirement,
        HubInvocationContext resource)
    {
        if (context.User?.Identity?.Name == null)
        {
            return Task.CompletedTask;
        }

        if (IsUserAllowedToDoThis(resource.HubMethodName, context.User.Identity.Name))
        {
            context.Succeed(requirement);
        }

        return Task.CompletedTask;
    }

    private bool IsUserAllowedToDoThis(string hubMethodName, string currentUsername)
    {
        if (hubMethodName.Equals("banUser", StringComparison.OrdinalIgnoreCase))
        {
            return currentUsername.Equals("bob42@jabbr.net", StringComparison.OrdinalIgnoreCase);
        }

        return currentUsername.EndsWith("@jabbr.net", StringComparison.OrdinalIgnoreCase));
    }
}
```

<span data-ttu-id="6b7c4-181">В приведенном выше коде `DomainRestrictedRequirement` служит пользовательским `IAuthorizationRequirement`.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-181">In the preceding code, `DomainRestrictedRequirement` serves as a custom `IAuthorizationRequirement`.</span></span> <span data-ttu-id="6b7c4-182">Так как параметр ресурса `HubInvocationContext` передается, внутренняя логика может выполнять следующее:</span><span class="sxs-lookup"><span data-stu-id="6b7c4-182">Because the `HubInvocationContext` resource parameter is being passed in, the internal logic can:</span></span>

* <span data-ttu-id="6b7c4-183">проверять контекст, в котором вызывается концентратор;</span><span class="sxs-lookup"><span data-stu-id="6b7c4-183">Inspect the context in which the Hub is being called.</span></span>
* <span data-ttu-id="6b7c4-184">принимать решения о разрешении пользователю выполнять отдельные методы концентратора.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-184">Make decisions on allowing the user to execute individual Hub methods.</span></span>

<span data-ttu-id="6b7c4-185">Отдельные методы концентратора можно обозначить именем политики, которую проверяет код во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-185">Individual Hub methods can be decorated with the name of the policy the code checks at run-time.</span></span> <span data-ttu-id="6b7c4-186">Когда клиенты пытаются вызвать отдельные методы концентратора, обработчик `DomainRestrictedRequirement` запускается и управляет доступом к методам.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-186">As clients attempt to call individual Hub methods, the `DomainRestrictedRequirement` handler runs and controls access to the methods.</span></span> <span data-ttu-id="6b7c4-187">В зависимости от того, как `DomainRestrictedRequirement` управляет доступом:</span><span class="sxs-lookup"><span data-stu-id="6b7c4-187">Based on the way the `DomainRestrictedRequirement` controls access:</span></span>

* <span data-ttu-id="6b7c4-188">все вошедшие в систему пользователи могут вызывать метод `SendMessage`;</span><span class="sxs-lookup"><span data-stu-id="6b7c4-188">All logged-in users can call the `SendMessage` method.</span></span>
* <span data-ttu-id="6b7c4-189">просматривать журналы пользователей могут только пользователи, выполнившие вход с помощью адреса электронной почты `@jabbr.net`;</span><span class="sxs-lookup"><span data-stu-id="6b7c4-189">Only users who have logged in with a `@jabbr.net` email address can view users’ histories.</span></span>
* <span data-ttu-id="6b7c4-190">запретить пользователям участвовать в обсуждениях могут только члены `bob42@jabbr.net`.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-190">Only `bob42@jabbr.net` can ban users from the chat room.</span></span>

```csharp
[Authorize]
public class ChatHub : Hub
{
    public void SendMessage(string message)
    {
    }

    [Authorize("DomainRestricted")]
    public void BanUser(string username)
    {
    }

    [Authorize("DomainRestricted")]
    public void ViewUserHistory(string username)
    {
    }
}
```

<span data-ttu-id="6b7c4-191">Для создания политики `DomainRestricted` может потребоваться сделать следующее:</span><span class="sxs-lookup"><span data-stu-id="6b7c4-191">Creating the `DomainRestricted` policy might involve:</span></span>

* <span data-ttu-id="6b7c4-192">добавить новую политику в *Startup.cs*;</span><span class="sxs-lookup"><span data-stu-id="6b7c4-192">In *Startup.cs*, adding the new policy.</span></span>
* <span data-ttu-id="6b7c4-193">предоставить настраиваемое требование `DomainRestrictedRequirement` в качестве параметра;</span><span class="sxs-lookup"><span data-stu-id="6b7c4-193">Provide the custom `DomainRestrictedRequirement` requirement as a parameter.</span></span>
* <span data-ttu-id="6b7c4-194">зарегистрировать `DomainRestricted` с помощью ПО промежуточного слоя авторизации.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-194">Registering `DomainRestricted` with the authorization middleware.</span></span>

```csharp
services
    .AddAuthorization(options =>
    {
        options.AddPolicy("DomainRestricted", policy =>
        {
            policy.Requirements.Add(new DomainRestrictedRequirement());
        });
    });
```

<span data-ttu-id="6b7c4-195">Концентраторы SignalR используют [маршрутизацию конечных точек](xref:fundamentals/routing).</span><span class="sxs-lookup"><span data-stu-id="6b7c4-195">SignalR hubs use [Endpoint Routing](xref:fundamentals/routing).</span></span> <span data-ttu-id="6b7c4-196">Подключение концентратора SignalR было ранее выполнено явным образом:</span><span class="sxs-lookup"><span data-stu-id="6b7c4-196">SignalR hub connection was previously done explicitly:</span></span>

```csharp
app.UseSignalR(routes =>
{
    routes.MapHub<ChatHub>("hubs/chat");
});
```

<span data-ttu-id="6b7c4-197">В предыдущей версии разработчикам требовалось подключать контроллеры, страницы Razor и концентраторы в различных местах.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-197">In the previous version, developers needed to wire up controllers, Razor pages, and hubs in a variety of different places.</span></span> <span data-ttu-id="6b7c4-198">В результате явного подключения возникает последовательность практически идентичных сегментов маршрутизации:</span><span class="sxs-lookup"><span data-stu-id="6b7c4-198">Explicit connection results in a series of nearly-identical routing segments:</span></span>

```csharp
app.UseSignalR(routes =>
{
    routes.MapHub<ChatHub>("hubs/chat");
});

app.UseRouting(routes =>
{
    routes.MapRazorPages();
});
```

<span data-ttu-id="6b7c4-199">Концентраторы SignalR 3.0 можно маршрутизировать через маршрутизацию конечных точек.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-199">SignalR 3.0 hubs can be routed via endpoint routing.</span></span> <span data-ttu-id="6b7c4-200">При такой маршрутизации, как правило, можно настроить всю маршрутизацию в `UseRouting`.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-200">With endpoint routing, typically all routing can be configured in `UseRouting`:</span></span>

```csharp
app.UseRouting(routes =>
{
    routes.MapRazorPages();
    routes.MapHub<ChatHub>("hubs/chat");
});
```

<span data-ttu-id="6b7c4-201">Добавлен ASP.NET Core 3.0 SignalR:</span><span class="sxs-lookup"><span data-stu-id="6b7c4-201">ASP.NET Core 3.0 SignalR added:</span></span>

<span data-ttu-id="6b7c4-202">потоковая передача между клиентом и сервером.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-202">Client-to-server streaming.</span></span> <span data-ttu-id="6b7c4-203">При потоковой передаче между клиентом и сервером методы на стороне сервера могут принимать экземпляры `IAsyncEnumerable<T>` или `ChannelReader<T>`.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-203">With client-to-server streaming, server-side methods can take instances of either an `IAsyncEnumerable<T>` or `ChannelReader<T>`.</span></span> <span data-ttu-id="6b7c4-204">В следующем примере C# метод `UploadStream` в концентраторе получит поток строк от клиента:</span><span class="sxs-lookup"><span data-stu-id="6b7c4-204">In the following C# sample, the `UploadStream` method on the Hub will receive a stream of strings from the client:</span></span>

```csharp
public async Task UploadStream(IAsyncEnumerable<string> stream)
{
    await foreach (var item in stream)
    {
        // process content
    }
}
```

<span data-ttu-id="6b7c4-205">Клиентские приложения .NET могут передавать экземпляр `IAsyncEnumerable<T>` или `ChannelReader<T>` в качестве аргумента `stream` для метода концентратора `UploadStream`, приведенного выше.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-205">.NET client apps can pass either an `IAsyncEnumerable<T>` or `ChannelReader<T>` instance as the `stream` argument of the `UploadStream` Hub method above.</span></span>

<span data-ttu-id="6b7c4-206">После завершения цикла `for` и завершения работы локальной функции отправляется завершение потока:</span><span class="sxs-lookup"><span data-stu-id="6b7c4-206">After the `for` loop has completed and the local function exits, the stream completion is sent:</span></span>

```csharp
async IAsyncEnumerable<string> clientStreamData()
{
    for (var i = 0; i < 5; i++)
    {
        var data = await FetchSomeData();
        yield return data;
    }
}

await connection.SendAsync("UploadStream", clientStreamData());
```

<span data-ttu-id="6b7c4-207">Клиентские приложения JavaScript используют SignalR `Subject` (или [субъект RxJS](https://rxjs.dev/api/index/class/Subject)) для аргумента `stream` метода концентратора `UploadStream`, приведенного выше.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-207">JavaScript client apps use the SignalR `Subject` (or an [RxJS Subject](https://rxjs.dev/api/index/class/Subject)) for the `stream` argument of the `UploadStream` Hub method above.</span></span>

```javascript
let subject = new signalR.Subject();
await connection.send("StartStream", "MyAsciiArtStream", subject);
```

<span data-ttu-id="6b7c4-208">Код JavaScript может использовать метод `subject.next` для обработки строк по мере их записи и готовности к отправке на сервер.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-208">The JavaScript code could use the `subject.next` method to handle strings as they are captured and ready to be sent to the server.</span></span>

```javascript
subject.next("example");
subject.complete();
```

<span data-ttu-id="6b7c4-209">С помощью кода, подобного двум предыдущим фрагментам, можно создать потоковую передачу в реальном времени.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-209">Using code like the two preceding snippets, real-time streaming experiences can be created.</span></span>

### <a name="new-json-serialization"></a><span data-ttu-id="6b7c4-210">Новая сериализация JSON</span><span class="sxs-lookup"><span data-stu-id="6b7c4-210">New JSON serialization</span></span>

<span data-ttu-id="6b7c4-211">ASP.NET Core 3.0 теперь по умолчанию использует <xref:System.Text.Json> для сериализации JSON:</span><span class="sxs-lookup"><span data-stu-id="6b7c4-211">ASP.NET Core 3.0 now uses <xref:System.Text.Json> by default for JSON serialization:</span></span>

* <span data-ttu-id="6b7c4-212">асинхронно считывает и записывает JSON;</span><span class="sxs-lookup"><span data-stu-id="6b7c4-212">Reads and writes JSON asynchronously.</span></span>
* <span data-ttu-id="6b7c4-213">оптимизирован для текста UTF-8;</span><span class="sxs-lookup"><span data-stu-id="6b7c4-213">Is optimized for UTF-8 text.</span></span>
* <span data-ttu-id="6b7c4-214">предоставляет более высокую производительность, чем `Newtonsoft.Json`.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-214">Typically higher performance than `Newtonsoft.Json`.</span></span>

<span data-ttu-id="6b7c4-215">Сведения о добавлении Json.NET в ASP.NET Core 3.0 см. в разделе [Добавление поддержки формата JSON на основе Newtonsoft.Json](xref:web-api/advanced/formatting#add-newtonsoftjson-based-json-format-support).</span><span class="sxs-lookup"><span data-stu-id="6b7c4-215">To add Json.NET to ASP.NET Core 3.0, see [Add Newtonsoft.Json-based JSON format support](xref:web-api/advanced/formatting#add-newtonsoftjson-based-json-format-support).</span></span>

## <a name="new-razor-directives"></a><span data-ttu-id="6b7c4-216">Новые директивы Razor</span><span class="sxs-lookup"><span data-stu-id="6b7c4-216">New Razor directives</span></span>

<span data-ttu-id="6b7c4-217">Следующий список содержит новые директивы Razor:</span><span class="sxs-lookup"><span data-stu-id="6b7c4-217">The following list contains new Razor directives:</span></span>

* <span data-ttu-id="6b7c4-218">[@attribute](xref:mvc/views/razor#attribute) &ndash; директива `@attribute` добавляет данный атрибут к классу созданной страницы или представления.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-218">[@attribute](xref:mvc/views/razor#attribute) &ndash; The `@attribute` directive applies the given attribute to the class of the generated page or view.</span></span> <span data-ttu-id="6b7c4-219">Например, `@attribute [Authorize]`.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-219">For example, `@attribute [Authorize]`.</span></span>
* <span data-ttu-id="6b7c4-220">[@implements](xref:mvc/views/razor#implements) &ndash; директива `@implements` реализует интерфейс для созданного класса.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-220">[@implements](xref:mvc/views/razor#implements) &ndash; The `@implements` directive implements an interface for the generated class.</span></span> <span data-ttu-id="6b7c4-221">Например, `@implements IDisposable`.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-221">For example, `@implements IDisposable`.</span></span>

## <a name="identityserver4-supports-authentication-and-authorization-for-web-apis-and-spas"></a><span data-ttu-id="6b7c4-222">IdentityServer4 поддерживает проверку подлинности и авторизацию для веб-API и одностраничных приложений</span><span class="sxs-lookup"><span data-stu-id="6b7c4-222">IdentityServer4 supports authentication and authorization for web APIs and SPAs</span></span>

<span data-ttu-id="6b7c4-223">[IdentityServer4](https://identityserver.io) — это платформа OpenID Connect и OAuth 2.0 для ASP.NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-223">[IdentityServer4](https://identityserver.io) is an OpenID Connect and OAuth 2.0 framework for ASP.NET Core 3.0.</span></span> <span data-ttu-id="6b7c4-224">IdentityServer4 включает следующие функции безопасности:</span><span class="sxs-lookup"><span data-stu-id="6b7c4-224">IdentityServer4 enables the following security features:</span></span>

* <span data-ttu-id="6b7c4-225">Проверка подлинности как услуга (AaaS)</span><span class="sxs-lookup"><span data-stu-id="6b7c4-225">Authentication as a Service (AaaS)</span></span>
* <span data-ttu-id="6b7c4-226">Единый вход (SSO) для нескольких типов приложений</span><span class="sxs-lookup"><span data-stu-id="6b7c4-226">Single sign-on/off (SSO) over multiple application types</span></span>
* <span data-ttu-id="6b7c4-227">Контроль доступа для API</span><span class="sxs-lookup"><span data-stu-id="6b7c4-227">Access control for APIs</span></span>
* <span data-ttu-id="6b7c4-228">Шлюз федерации</span><span class="sxs-lookup"><span data-stu-id="6b7c4-228">Federation Gateway</span></span>

<span data-ttu-id="6b7c4-229">Дополнительные сведения см. в разделе [Добро пожаловать в IdentityServer4](http://docs.identityserver.io/en/latest/index.html).</span><span class="sxs-lookup"><span data-stu-id="6b7c4-229">For more information, see [Welcome to IdentityServer4](http://docs.identityserver.io/en/latest/index.html).</span></span>

## <a name="certificate-and-kerberos-authentication"></a><span data-ttu-id="6b7c4-230">Проверка подлинности Kerberos и проверка подлинности с помощью сертификата</span><span class="sxs-lookup"><span data-stu-id="6b7c4-230">Certificate and Kerberos authentication</span></span>

<span data-ttu-id="6b7c4-231">Для проверки подлинности с помощью сертификата требуется:</span><span class="sxs-lookup"><span data-stu-id="6b7c4-231">Certificate authentication requires:</span></span>

* <span data-ttu-id="6b7c4-232">настройка сервера для принятия сертификатов;</span><span class="sxs-lookup"><span data-stu-id="6b7c4-232">Configuring the server to accept certificates.</span></span>
* <span data-ttu-id="6b7c4-233">добавление ПО промежуточного слоя для проверки подлинности в `Startup.Configure`;</span><span class="sxs-lookup"><span data-stu-id="6b7c4-233">Adding the authentication middleware in `Startup.Configure`.</span></span>
* <span data-ttu-id="6b7c4-234">добавление службы проверки подлинности с помощью сертификатов в `Startup.ConfigureServices`.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-234">Adding the certificate authentication service in `Startup.ConfigureServices`.</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddAuthentication(
        CertificateAuthenticationDefaults.AuthenticationScheme)
            .AddCertificate();
    // Other service configuration removed.
}

public void Configure(IApplicationBuilder app, IHostingEnvironment env)
{
    app.UseAuthentication();
    // Other app configuration removed.
}
```

<span data-ttu-id="6b7c4-235">Параметры проверки подлинности с помощью сертификата включают следующие возможности:</span><span class="sxs-lookup"><span data-stu-id="6b7c4-235">Options for certificate authentication include the ability to:</span></span>

* <span data-ttu-id="6b7c4-236">принятие самозаверяющих сертификатов;</span><span class="sxs-lookup"><span data-stu-id="6b7c4-236">Accept self-signed certificates.</span></span>
* <span data-ttu-id="6b7c4-237">проверка отзыва сертификатов;</span><span class="sxs-lookup"><span data-stu-id="6b7c4-237">Check for certificate revocation.</span></span>
* <span data-ttu-id="6b7c4-238">проверка наличия в предложенном сертификате правильных флагов использования.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-238">Check that the proffered certificate has the right usage flags in it.</span></span>

<span data-ttu-id="6b7c4-239">Субъект-пользователь по умолчанию создается на основе свойств сертификата.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-239">A default user principal is constructed from the certificate properties.</span></span> <span data-ttu-id="6b7c4-240">Субъект-пользователь содержит событие, которое позволяет дополнить или заменить субъект.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-240">The user principal contains an event that enables supplementing or replacing the principal.</span></span> <span data-ttu-id="6b7c4-241">Дополнительные сведения можно найти по адресу: <xref:security/authentication/certauth>.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-241">For more information, see <xref:security/authentication/certauth>.</span></span>

<span data-ttu-id="6b7c4-242">[Проверка подлинности Windows](/windows-server/security/windows-authentication/windows-authentication-overview) теперь предусмотрена для Linux и macOS.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-242">[Windows Authentication](/windows-server/security/windows-authentication/windows-authentication-overview) has been extended onto Linux and macOS.</span></span> <span data-ttu-id="6b7c4-243">В предыдущих версиях проверка подлинности Windows была доступна только для [IIS](xref:host-and-deploy/iis/index) и [HttpSys](xref:fundamentals/servers/httpsys).</span><span class="sxs-lookup"><span data-stu-id="6b7c4-243">In previous versions, Windows Authentication was limited to [IIS](xref:host-and-deploy/iis/index) and [HttpSys](xref:fundamentals/servers/httpsys).</span></span> <span data-ttu-id="6b7c4-244">В ASP.NET Core 3.0 [Kestrel](xref:fundamentals/servers/kestrel) имеет возможность использовать Negotiate, [Kerberos](/windows-server/security/kerberos/kerberos-authentication-overview) и [NTLM в Windows](/windows-server/security/kerberos/ntlm-overview), Linux и macOS для узлов, присоединенных к домену Windows.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-244">In ASP.NET Core 3.0, [Kestrel](xref:fundamentals/servers/kestrel) has the ability to use Negotiate, [Kerberos](/windows-server/security/kerberos/kerberos-authentication-overview), and [NTLM on Windows](/windows-server/security/kerberos/ntlm-overview), Linux, and macOS for Windows domain-joined hosts.</span></span> <span data-ttu-id="6b7c4-245">Поддержка Kestrel этих схем проверки подлинности предоставляется в пакете [Microsoft.AspNetCore.Authentication.Negotiate NuGet](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Negotiate).</span><span class="sxs-lookup"><span data-stu-id="6b7c4-245">Kestrel support of these authentication schemes is provided by the [Microsoft.AspNetCore.Authentication.Negotiate NuGet](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Negotiate) package.</span></span> <span data-ttu-id="6b7c4-246">Как и в других службах проверки подлинности, настройте приложение проверки подлинности во всей организации, а затем настройте службу:</span><span class="sxs-lookup"><span data-stu-id="6b7c4-246">As with the other authentication services, configure authentication app wide, then configure the service:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddAuthentication(NegotiateDefaults.AuthenticationScheme)
        .AddNegotiate();
    // Other service configuration removed.
}

public void Configure(IApplicationBuilder app, IHostingEnvironment env)
{
    app.UseAuthentication();
    // Other app configuration removed.
}
```

<span data-ttu-id="6b7c4-247">Требования к узлу:</span><span class="sxs-lookup"><span data-stu-id="6b7c4-247">Host requirements:</span></span>

* <span data-ttu-id="6b7c4-248">На узлах Windows [имена субъектов-служб](/windows/win32/ad/service-principal-names) должны быть добавлены в учетную запись пользователя, где размещается приложение.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-248">Windows hosts must have [Service Principal Names](/windows/win32/ad/service-principal-names) (SPNs) added to the user account hosting the app.</span></span>
* <span data-ttu-id="6b7c4-249">Компьютеры Linux и macOS должны быть присоединены к домену.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-249">Linux and macOS machines must be joined to the domain.</span></span>
  * <span data-ttu-id="6b7c4-250">Имена субъектов-служб необходимо создать для веб-процесса.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-250">SPNs must be created for the web process.</span></span>
  * <span data-ttu-id="6b7c4-251">[Файлы Keytab](https://blogs.technet.microsoft.com/pie/2018/01/03/all-you-need-to-know-about-keytab-files/) необходимо создать и настроить на компьютере узла.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-251">[Keytab files](https://blogs.technet.microsoft.com/pie/2018/01/03/all-you-need-to-know-about-keytab-files/) must be generated and configured on the host machine.</span></span>

<span data-ttu-id="6b7c4-252">Дополнительные сведения можно найти по адресу: <xref:security/authentication/windowsauth>.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-252">For more information, see <xref:security/authentication/windowsauth>.</span></span>

## <a name="template-changes"></a><span data-ttu-id="6b7c4-253">Изменения шаблонов</span><span class="sxs-lookup"><span data-stu-id="6b7c4-253">Template changes</span></span>

<span data-ttu-id="6b7c4-254">В шаблонах веб-интерфейса (Razor Pages, MVC с контроллером и представлениями) удалены следующие элементы:</span><span class="sxs-lookup"><span data-stu-id="6b7c4-254">The web UI templates (Razor Pages, MVC with controller and views) have the following removed:</span></span>

* <span data-ttu-id="6b7c4-255">Пользовательского интерфейса согласия на файлы cookie больше нет.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-255">The cookie consent UI is no longer included.</span></span> <span data-ttu-id="6b7c4-256">Сведения о включении функции согласия на файлы cookie в приложении, созданном с помощью шаблона ASP.NET Core 3.0, см. в статье <xref:security/gdpr>.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-256">To enable the cookie consent feature in an ASP.NET Core 3.0 template generated app, see <xref:security/gdpr>.</span></span>
* <span data-ttu-id="6b7c4-257">Для ссылки на скрипты и связанные статические ресурсы теперь используются локальные файлы, а не CDN.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-257">Scripts and related static assets are now referenced as local files instead of using CDNs.</span></span> <span data-ttu-id="6b7c4-258">Дополнительные сведения см. в статье [3.0: Scripts and related static assets are now referenced as local files instead of using CDNs based on the current environment](https://github.com/aspnet/AspNetCore.Docs/issues/14350) (В версии 3.0 для ссылки на скрипты и связанные статические ресурсы теперь используются локальные файлы, а не CDN в зависимости от текущей среды) (№ 14350).</span><span class="sxs-lookup"><span data-stu-id="6b7c4-258">For more information, see [Scripts and related static assets are now referenced as local files instead of using CDNs based on the current environment (aspnet/AspNetCore.Docs #14350)](https://github.com/aspnet/AspNetCore.Docs/issues/14350).</span></span>

<span data-ttu-id="6b7c4-259">Шаблон Angular обновлен для использования Angular 8.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-259">The Angular template updated to use Angular 8.</span></span>

<span data-ttu-id="6b7c4-260">По умолчанию для шаблона библиотеки классов Razor (RCL) используется разработка компонентов Razor.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-260">The Razor class library (RCL) template defaults to Razor component development by default.</span></span> <span data-ttu-id="6b7c4-261">Новый параметр шаблона в Visual Studio обеспечивает поддержку шаблонов для страниц и представлений.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-261">A new template option in Visual Studio provides template support for pages and views.</span></span> <span data-ttu-id="6b7c4-262">При создании RCL на основе шаблона в командной оболочке передайте параметр `-support-pages-and-views` (`dotnet new razorclasslib -support-pages-and-views`).</span><span class="sxs-lookup"><span data-stu-id="6b7c4-262">When creating an RCL from the template in a command shell, pass the `-support-pages-and-views` option (`dotnet new razorclasslib -support-pages-and-views`).</span></span>

## <a name="generic-host"></a><span data-ttu-id="6b7c4-263">Универсальный узел</span><span class="sxs-lookup"><span data-stu-id="6b7c4-263">Generic Host</span></span>

<span data-ttu-id="6b7c4-264">Шаблоны ASP.NET Core 3.0 используют <xref:fundamentals/host/generic-host>.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-264">The ASP.NET Core 3.0 templates use <xref:fundamentals/host/generic-host>.</span></span> <span data-ttu-id="6b7c4-265">В предыдущих версиях использовался <xref:Microsoft.AspNetCore.Hosting.WebHostBuilder>.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-265">Previous versions used <xref:Microsoft.AspNetCore.Hosting.WebHostBuilder>.</span></span> <span data-ttu-id="6b7c4-266">Использование универсального узла .NET Core (<xref:Microsoft.Extensions.Hosting.HostBuilder>) обеспечивает лучшую интеграцию приложений ASP.NET Core с другими серверными сценариями, не зависящими от Интернета.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-266">Using the .NET Core Generic Host (<xref:Microsoft.Extensions.Hosting.HostBuilder>) provides better integration of ASP.NET Core apps with other server scenarios that are not web specific.</span></span> <span data-ttu-id="6b7c4-267">Дополнительные сведения см. в разделе [HostBuilder replaces WebHostBuilder](xref:migration/22-to-30?view=aspnetcore-2.2#hostbuilder-replaces-webhostbuilder) (HostBuilder заменяет WebHostBuilder).</span><span class="sxs-lookup"><span data-stu-id="6b7c4-267">For more information, see [HostBuilder replaces WebHostBuilder](xref:migration/22-to-30?view=aspnetcore-2.2#hostbuilder-replaces-webhostbuilder).</span></span>

### <a name="host-configuration"></a><span data-ttu-id="6b7c4-268">Конфигурация узла</span><span class="sxs-lookup"><span data-stu-id="6b7c4-268">Host configuration</span></span>

<span data-ttu-id="6b7c4-269">До выхода ASP.NET Core 3.0 переменные среды с префиксом `ASPNETCORE_` были загружены для конфигурации веб-узла.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-269">Prior to the release of ASP.NET Core 3.0, environment variables prefixed with `ASPNETCORE_` were loaded for host configuration of the Web Host.</span></span> <span data-ttu-id="6b7c4-270">В 3.0 `AddEnvironmentVariables` используется для загрузки переменных среды с префиксом `DOTNET_` для конфигурации узла с помощью `CreateDefaultBuilder`.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-270">In 3.0, `AddEnvironmentVariables` is used to load environment variables prefixed with `DOTNET_` for host configuration with `CreateDefaultBuilder`.</span></span>

### <a name="changes-to-startup-contructor-injection"></a><span data-ttu-id="6b7c4-271">Изменения во внедрении через конструктор Startup</span><span class="sxs-lookup"><span data-stu-id="6b7c4-271">Changes to Startup contructor injection</span></span>

<span data-ttu-id="6b7c4-272">Универсальный узел поддерживает только следующие типы для внедрения через конструктор `Startup`:</span><span class="sxs-lookup"><span data-stu-id="6b7c4-272">The Generic Host only supports the following types for `Startup` constructor injection:</span></span>

* <xref:Microsoft.Extensions.Hosting.IHostEnvironment>
* `IWebHostEnvironment`
* <xref:Microsoft.Extensions.Configuration.IConfiguration>

<span data-ttu-id="6b7c4-273">Все службы по-прежнему можно непосредственно внедрять в метод `Startup.Configure` в качестве аргументов.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-273">All services can still be injected directly as arguments to the `Startup.Configure` method.</span></span> <span data-ttu-id="6b7c4-274">Дополнительные сведения см. в статье [Generic Host restricts Startup constructor injection](https://github.com/aspnet/Announcements/issues/353) (Универсальный узел ограничивает внедрение через конструктор Startup) (№ 353).</span><span class="sxs-lookup"><span data-stu-id="6b7c4-274">For more information, see [Generic Host restricts Startup constructor injection (aspnet/Announcements #353)](https://github.com/aspnet/Announcements/issues/353).</span></span>

## <a name="kestrel"></a><span data-ttu-id="6b7c4-275">Kestrel</span><span class="sxs-lookup"><span data-stu-id="6b7c4-275">Kestrel</span></span>

* <span data-ttu-id="6b7c4-276">В конфигурацию Kestrel добавлена возможность миграции в универсальный узел.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-276">Kestrel configuration has been updated for the migration to the Generic Host.</span></span> <span data-ttu-id="6b7c4-277">В 3.0 Kestrel настраивается в построителе веб-узлов, предоставляемом `ConfigureWebHostDefaults`.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-277">In 3.0, Kestrel is configured on the web host builder provided by `ConfigureWebHostDefaults`.</span></span>
* <span data-ttu-id="6b7c4-278">Адаптеры подключений удалены из Kestrel и заменены на ПО промежуточного слоя подключения, которое похоже на ПО промежуточного слоя HTTP в конвейере ASP.NET Core, но для подключений более низкого уровня.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-278">Connection Adapters have been removed from Kestrel and replaced with Connection Middleware, which is similar to HTTP Middleware in the ASP.NET Core pipeline but for lower-level connections.</span></span>
* <span data-ttu-id="6b7c4-279">Транспортный уровень Kestrel предоставляется как открытый интерфейс в `Connections.Abstractions`.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-279">The Kestrel transport layer has been exposed as a public interface in `Connections.Abstractions`.</span></span>
* <span data-ttu-id="6b7c4-280">Неоднозначность заголовков и конечных строк устранена путем перемещения конечных заголовков в новую коллекцию.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-280">Ambiguity between headers and trailers has been resolved by moving trailing headers to a new collection.</span></span>
* <span data-ttu-id="6b7c4-281">Из-за таких интерфейсов API с синхронными операциями ввода-вывода, как `HttpRequest.Body.Read`, часто возникает нехватка потоков, что приводит к сбоям приложений.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-281">Synchronous IO APIs, such as `HttpRequest.Body.Read`, are a common source of thread starvation leading to app crashes.</span></span> <span data-ttu-id="6b7c4-282">В 3.0 `AllowSynchronousIO` отключен по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-282">In 3.0, `AllowSynchronousIO` is disabled by default.</span></span>

<span data-ttu-id="6b7c4-283">Дополнительные сведения можно найти по адресу: <xref:migration/22-to-30#kestrel>.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-283">For more information, see <xref:migration/22-to-30#kestrel>.</span></span>

## <a name="http2-enabled-by-default"></a><span data-ttu-id="6b7c4-284">HTTP/2 включено по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-284">HTTP/2 enabled by default</span></span>

<span data-ttu-id="6b7c4-285">В Kestrel для конечных точек HTTPS по умолчанию включено HTTP/2.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-285">HTTP/2 is enabled by default in Kestrel for HTTPS endpoints.</span></span> <span data-ttu-id="6b7c4-286">Поддержка HTTP/2 для IIS или HTTP.sys включена, если поддерживается операционной системой.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-286">HTTP/2 support for IIS or HTTP.sys is enabled when supported by the operating system.</span></span>

## <a name="eventcounters-on-request"></a><span data-ttu-id="6b7c4-287">EventCounters по запросу</span><span class="sxs-lookup"><span data-stu-id="6b7c4-287">EventCounters on request</span></span>

<span data-ttu-id="6b7c4-288">EventSource размещения, `Microsoft.AspNetCore.Hosting`, выдает следующие новые типы <xref:System.Diagnostics.Tracing.EventCounter>, связанные с входящими запросами:</span><span class="sxs-lookup"><span data-stu-id="6b7c4-288">The Hosting EventSource, `Microsoft.AspNetCore.Hosting`, emits the following new <xref:System.Diagnostics.Tracing.EventCounter> types related to incoming requests:</span></span>

* `requests-per-second`
* `total-requests`
* `current-requests`
* `failed-requests`

## <a name="endpoint-routing"></a><span data-ttu-id="6b7c4-289">Маршрутизация конечных точек</span><span class="sxs-lookup"><span data-stu-id="6b7c4-289">Endpoint routing</span></span>

<span data-ttu-id="6b7c4-290">Маршрутизация конечных точек, позволяющая платформам (например, MVC) хорошо работать с ПО промежуточного слоя, усовершенствована:</span><span class="sxs-lookup"><span data-stu-id="6b7c4-290">Endpoint Routing, which allows frameworks (for example, MVC) to work well with middleware, is enhanced:</span></span>

* <span data-ttu-id="6b7c4-291">порядок ПО промежуточного слоя и конечных точек можно настроить в конвейере обработки запросов `Startup.Configure`;</span><span class="sxs-lookup"><span data-stu-id="6b7c4-291">The order of middleware and endpoints is configurable in the request processing pipeline of `Startup.Configure`.</span></span>
* <span data-ttu-id="6b7c4-292">конечные точки и ПО промежуточного слоя хорошо используются с другими технологиями на основе ASP.NET Core, такими как проверки работоспособности;</span><span class="sxs-lookup"><span data-stu-id="6b7c4-292">Endpoints and middleware compose well with other ASP.NET Core-based technologies, such as Health Checks.</span></span>
* <span data-ttu-id="6b7c4-293">конечные точки могут реализовывать политику, например CORS или авторизацию, в ПО промежуточного слоя и MVC;</span><span class="sxs-lookup"><span data-stu-id="6b7c4-293">Endpoints can implement a policy, such as CORS or authorization, in both middleware and MVC.</span></span>
* <span data-ttu-id="6b7c4-294">фильтры и атрибуты можно разместить в методах контроллеров.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-294">Filters and attributes can be placed on methods in controllers.</span></span>

<span data-ttu-id="6b7c4-295">Дополнительные сведения можно найти по адресу: <xref:fundamentals/routing#routing-basics>.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-295">For more information, see <xref:fundamentals/routing#routing-basics>.</span></span>

## <a name="health-checks"></a><span data-ttu-id="6b7c4-296">Проверки работоспособности</span><span class="sxs-lookup"><span data-stu-id="6b7c4-296">Health Checks</span></span>

<span data-ttu-id="6b7c4-297">Для проверок работоспособности используется маршрутизация конечных точек с универсальным узлом.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-297">Health Checks use endpoint routing with the Generic Host.</span></span> <span data-ttu-id="6b7c4-298">В `Startup.Configure` вызовите `MapHealthChecks` для построителя конечной точки с URL-адресом конечной точки или относительным путем:</span><span class="sxs-lookup"><span data-stu-id="6b7c4-298">In `Startup.Configure`, call `MapHealthChecks` on the endpoint builder with the endpoint URL or relative path:</span></span>

```csharp
app.UseEndpoints(endpoints =>
{
    endpoints.MapHealthChecks("/health");
});
```

<span data-ttu-id="6b7c4-299">Конечные точки проверки работоспособности могут:</span><span class="sxs-lookup"><span data-stu-id="6b7c4-299">Health Checks endpoints can:</span></span>

* <span data-ttu-id="6b7c4-300">указать один или несколько разрешенных узлов или портов;</span><span class="sxs-lookup"><span data-stu-id="6b7c4-300">Specify one or more permitted hosts/ports.</span></span>
* <span data-ttu-id="6b7c4-301">требовать авторизацию;</span><span class="sxs-lookup"><span data-stu-id="6b7c4-301">Require authorization.</span></span>
* <span data-ttu-id="6b7c4-302">требовать CORS.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-302">Require CORS.</span></span>

<span data-ttu-id="6b7c4-303">Дополнительные сведения см. в следующих статьях:</span><span class="sxs-lookup"><span data-stu-id="6b7c4-303">For more information, see the following articles:</span></span>

* <xref:migration/22-to-30#health-checks>
* <xref:host-and-deploy/health-checks>

## <a name="pipes-on-httpcontext"></a><span data-ttu-id="6b7c4-304">Каналы в HttpContext</span><span class="sxs-lookup"><span data-stu-id="6b7c4-304">Pipes on HttpContext</span></span>

<span data-ttu-id="6b7c4-305">Теперь можно читать текст запроса и писать текст ответа с помощью API <xref:System.IO.Pipelines>.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-305">It's now possible to read the request body and write the response body using the <xref:System.IO.Pipelines> API.</span></span> <span data-ttu-id="6b7c4-306">Классу</span><span class="sxs-lookup"><span data-stu-id="6b7c4-306">The</span></span> <!-- <xref:Microsoft.AspNetCore.Http.HttpRequest.BodyReader> --> <span data-ttu-id="6b7c4-307">Свойство `HttpRequest.BodyReader` предоставляет класс <xref:System.IO.Pipelines.PipeReader>, который можно использовать для чтения текста запроса.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-307">`HttpRequest.BodyReader` property provides a <xref:System.IO.Pipelines.PipeReader> that can be used to read the request body.</span></span> <span data-ttu-id="6b7c4-308">Классу</span><span class="sxs-lookup"><span data-stu-id="6b7c4-308">The</span></span> <!-- <xref:Microsoft.AspNetCore.Http.> --> <span data-ttu-id="6b7c4-309">Свойство `HttpResponse.BodyWriter` предоставляет класс <xref:System.IO.Pipelines.PipeWriter>, который можно использовать для записи текста ответа.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-309">`HttpResponse.BodyWriter` property provides a <xref:System.IO.Pipelines.PipeWriter> that can be used to write the response body.</span></span> <span data-ttu-id="6b7c4-310">`HttpRequest.BodyReader` — это аналог потока `HttpRequest.Body`.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-310">`HttpRequest.BodyReader` is an analogue of the `HttpRequest.Body` stream.</span></span> <span data-ttu-id="6b7c4-311">`HttpResponse.BodyWriter` — это аналог потока `HttpResponse.Body`.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-311">`HttpResponse.BodyWriter` is an analogue of the `HttpResponse.Body` stream.</span></span>

<!-- indirectly related, https://github.com/dotnet/docs/pull/14414 won't be published by 9/23  -->

## <a name="improved-error-reporting-in-iis"></a><span data-ttu-id="6b7c4-312">Улучшены сообщения об ошибках в IIS</span><span class="sxs-lookup"><span data-stu-id="6b7c4-312">Improved error reporting in IIS</span></span>

<span data-ttu-id="6b7c4-313">Теперь при ошибках запуска во время размещения приложений ASP.NET Core в IIS предоставляются более полные диагностические данные.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-313">Startup errors when hosting ASP.NET Core apps in IIS now produce richer diagnostic data.</span></span> <span data-ttu-id="6b7c4-314">Сведения об этих ошибках передаются в журнал событий Windows с трассировками стека везде, где это применимо.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-314">These errors are reported to the Windows Event Log with stack traces wherever applicable.</span></span> <span data-ttu-id="6b7c4-315">Кроме того, все предупреждения, ошибки и необработанные исключения записываются в журнал событий Windows.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-315">In addition, all warnings, errors, and unhandled exceptions are logged to the Windows Event Log.</span></span>

## <a name="worker-service-and-worker-sdk"></a><span data-ttu-id="6b7c4-316">Служба рабочих ролей и пакет SDK для рабочей роли</span><span class="sxs-lookup"><span data-stu-id="6b7c4-316">Worker Service and Worker SDK</span></span>

<span data-ttu-id="6b7c4-317">В .NET Core 3.0 появился новый шаблон приложения службы рабочих ролей.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-317">.NET Core 3.0 introduces the new Worker Service app template.</span></span> <span data-ttu-id="6b7c4-318">Этот шаблон может служить отправной точкой для написания длительных приложений служб в .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-318">This template provides a starting point for writing long running services in .NET Core.</span></span>

<span data-ttu-id="6b7c4-319">Дополнительные сведения:</span><span class="sxs-lookup"><span data-stu-id="6b7c4-319">For more information, see:</span></span>

* <span data-ttu-id="6b7c4-320">[.NET Core Workers as Windows Services](https://devblogs.microsoft.com/aspnet/net-core-workers-as-windows-services/) (Рабочие роли .NET Core в качестве служб Windows)</span><span class="sxs-lookup"><span data-stu-id="6b7c4-320">[.NET Core Workers as Windows Services](https://devblogs.microsoft.com/aspnet/net-core-workers-as-windows-services/)</span></span>
* <xref:fundamentals/host/hosted-services>
* <xref:host-and-deploy/windows-service>

## <a name="forwarded-headers-middleware-improvements"></a><span data-ttu-id="6b7c4-321">Улучшения ПО промежуточного слоя перенаправления заголовков</span><span class="sxs-lookup"><span data-stu-id="6b7c4-321">Forwarded Headers Middleware improvements</span></span>

<span data-ttu-id="6b7c4-322">В предыдущих версиях ASP.NET Core вызвать <xref:Microsoft.AspNetCore.Builder.HstsBuilderExtensions.UseHsts*> и <xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection*> было проблематично при развертывании в Azure Linux или за любым обратным прокси-сервером, отличным от IIS.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-322">In previous versions of ASP.NET Core, calling <xref:Microsoft.AspNetCore.Builder.HstsBuilderExtensions.UseHsts*> and  <xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection*> were problematic when deployed to an Azure Linux or behind any reverse proxy other than IIS.</span></span> <span data-ttu-id="6b7c4-323">Исправление для предыдущих версий описано в разделе [Переадресация схемы для Linux и обратных прокси-серверов не IIS](xref:host-and-deploy/proxy-load-balancer#forward-the-scheme-for-linux-and-non-iis-reverse-proxies).</span><span class="sxs-lookup"><span data-stu-id="6b7c4-323">The fix for previous versions is documented in [Forward the scheme for Linux and non-IIS reverse proxies](xref:host-and-deploy/proxy-load-balancer#forward-the-scheme-for-linux-and-non-iis-reverse-proxies).</span></span>

<span data-ttu-id="6b7c4-324">Этот сценарий исправлен в ASP.NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-324">This scenario is fixed in ASP.NET Core 3.0.</span></span> <span data-ttu-id="6b7c4-325">Узел включает [ПО промежуточного слоя перенаправления заголовков](xref:host-and-deploy/proxy-load-balancer#forwarded-headers-middleware-options), если переменной среды `ASPNETCORE_FORWARDEDHEADERS_ENABLED` присвоено значение `true`.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-325">The host enables the [Forwarded Headers Middleware](xref:host-and-deploy/proxy-load-balancer#forwarded-headers-middleware-options) when the `ASPNETCORE_FORWARDEDHEADERS_ENABLED` environment variable is set to `true`.</span></span> <span data-ttu-id="6b7c4-326">В образах контейнера для `ASPNETCORE_FORWARDEDHEADERS_ENABLED` задано значение `true`.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-326">`ASPNETCORE_FORWARDEDHEADERS_ENABLED` is set to `true` in our container images.</span></span>

## <a name="performance-improvements"></a><span data-ttu-id="6b7c4-327">Улучшения производительности</span><span class="sxs-lookup"><span data-stu-id="6b7c4-327">Performance improvements</span></span>

<span data-ttu-id="6b7c4-328">В ASP.NET Core 3.0 реализованы многочисленные улучшения, сокращающие использование памяти и повышающие пропускную способность:</span><span class="sxs-lookup"><span data-stu-id="6b7c4-328">ASP.NET Core 3.0 includes many improvements that reduce memory usage and improve throughput:</span></span>

* <span data-ttu-id="6b7c4-329">сокращение использования памяти при использовании встроенного контейнера внедрения зависимостей для служб с заданной областью;</span><span class="sxs-lookup"><span data-stu-id="6b7c4-329">Reduction in memory usage when using the built-in dependency injection container for scoped services.</span></span>
* <span data-ttu-id="6b7c4-330">сокращение количества распределений на платформе, включая сценарии ПО промежуточного слоя и маршрутизацию;</span><span class="sxs-lookup"><span data-stu-id="6b7c4-330">Reduction in allocations across the framework, including middleware scenarios and routing.</span></span>
* <span data-ttu-id="6b7c4-331">сокращение использования памяти для подключений WebSocket;</span><span class="sxs-lookup"><span data-stu-id="6b7c4-331">Reduction in memory usage for WebSocket connections.</span></span>
* <span data-ttu-id="6b7c4-332">сокращение использования памяти и улучшение пропускной способности для подключений по протоколу HTTPS;</span><span class="sxs-lookup"><span data-stu-id="6b7c4-332">Memory reduction and throughput improvements for HTTPS connections.</span></span>
* <span data-ttu-id="6b7c4-333">новый оптимизированный и полностью асинхронный сериализатор JSON;</span><span class="sxs-lookup"><span data-stu-id="6b7c4-333">New optimized and fully asynchronous JSON serializer.</span></span>
* <span data-ttu-id="6b7c4-334">сокращение использования памяти и улучшения пропускной способности при анализе формы.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-334">Reduction in memory usage and throughput improvements in form parsing.</span></span>

## <a name="aspnet-core-30-only-runs-on-net-core-30"></a><span data-ttu-id="6b7c4-335">ASP.NET Core 3.0 работает только в .NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="6b7c4-335">ASP.NET Core 3.0 only runs on .NET Core 3.0</span></span>

<span data-ttu-id="6b7c4-336">Начиная с ASP.NET Core 3.0, .NET Framework больше не является поддерживаемой целевой платформой.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-336">As of ASP.NET Core 3.0, .NET Framework is no longer a supported target framework.</span></span> <span data-ttu-id="6b7c4-337">Проекты, предназначенные для .NET Framework, можно полноценно использовать с помощью [выпуска LTS .NET Core 2.1](https://www.microsoft.com/net/download/dotnet-core/2.1).</span><span class="sxs-lookup"><span data-stu-id="6b7c4-337">Projects targeting .NET Framework can continue in a fully supported fashion using the [.NET Core 2.1 LTS release](https://www.microsoft.com/net/download/dotnet-core/2.1).</span></span> <span data-ttu-id="6b7c4-338">Большинство пакетов, связанных с ASP.NET Core 2.1.x, будут поддерживаться неограниченно после истечения 3-летнего периода LTS для .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-338">Most ASP.NET Core 2.1.x related packages will be supported indefinitely, beyond the 3 year LTS period for .NET Core 2.1.</span></span>

<span data-ttu-id="6b7c4-339">Сведения о миграции см. в статье [Перенос кода в .NET Core из .NET Framework](/dotnet/core/porting/).</span><span class="sxs-lookup"><span data-stu-id="6b7c4-339">For migration information, see [Port your code from .NET Framework to .NET Core](/dotnet/core/porting/).</span></span>

## <a name="use-the-aspnet-core-shared-framework"></a><span data-ttu-id="6b7c4-340">Использование общей платформы .NET Core</span><span class="sxs-lookup"><span data-stu-id="6b7c4-340">Use the ASP.NET Core shared framework</span></span>

<span data-ttu-id="6b7c4-341">Для общей платформы ASP.NET Core 3.0, содержащейся в [метапакете Microsoft.AspNetCore.app](xref:fundamentals/metapackage-app), больше не требуется явный элемент `<PackageReference />` в файле проекта.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-341">The ASP.NET Core 3.0 shared framework, contained in the [Microsoft.AspNetCore.App metapackage](xref:fundamentals/metapackage-app), no longer requires an explicit `<PackageReference />` element in the project file.</span></span> <span data-ttu-id="6b7c4-342">При использовании пакета SDK `Microsoft.NET.Sdk.Web` в файле проекта автоматически создается ссылка на общую платформу:</span><span class="sxs-lookup"><span data-stu-id="6b7c4-342">The shared framework is automatically referenced when using the `Microsoft.NET.Sdk.Web` SDK in the project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">
```

## <a name="assemblies-removed-from-the-aspnet-core-shared-framework"></a><span data-ttu-id="6b7c4-343">Сборки, удаленные из общей платформы ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="6b7c4-343">Assemblies removed from the ASP.NET Core shared framework</span></span>

<span data-ttu-id="6b7c4-344">Наиболее важные сборки, удаленные из общей платформы ASP.NET Core 3.0:</span><span class="sxs-lookup"><span data-stu-id="6b7c4-344">The most notable assemblies removed from the ASP.NET Core 3.0 shared framework are:</span></span>

* <span data-ttu-id="6b7c4-345">[Newtonsoft.Json](https://www.nuget.org/packages/Newtonsoft.Json/) (Json.NET).</span><span class="sxs-lookup"><span data-stu-id="6b7c4-345">[Newtonsoft.Json](https://www.nuget.org/packages/Newtonsoft.Json/) (Json.NET).</span></span> <span data-ttu-id="6b7c4-346">Сведения о добавлении Json.NET в ASP.NET Core 3.0 см. в разделе [Добавление поддержки формата JSON на основе Newtonsoft.Json](xref:web-api/advanced/formatting#add-newtonsoftjson-based-json-format-support).</span><span class="sxs-lookup"><span data-stu-id="6b7c4-346">To add Json.NET to ASP.NET Core 3.0, see [Add Newtonsoft.Json-based JSON format support](xref:web-api/advanced/formatting#add-newtonsoftjson-based-json-format-support).</span></span> <span data-ttu-id="6b7c4-347">В ASP.NET Core 3.0 внедрен `System.Text.Json` для чтения файла JSON и записи в него.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-347">ASP.NET Core 3.0 introduces `System.Text.Json` for reading and writing JSON.</span></span> <span data-ttu-id="6b7c4-348">Дополнительные сведения см. в разделе [Новая сериализация JSON](#new-json-serialization) в этом документе.</span><span class="sxs-lookup"><span data-stu-id="6b7c4-348">For more information, see [New JSON serialization](#new-json-serialization) in this document.</span></span>
* [<span data-ttu-id="6b7c4-349">Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="6b7c4-349">Entity Framework Core</span></span>](/ef/core/)

<span data-ttu-id="6b7c4-350">Полный список сборок, удаленных из общей платформы, см. в разделе [Assemblies being removed from Microsoft.AspNetCore.App 3.0](https://github.com/aspnet/AspNetCore/issues/3755) (Сборки, удаленные из Microsoft.AspNetCore.App 3.0).</span><span class="sxs-lookup"><span data-stu-id="6b7c4-350">For a complete list of assemblies removed from the shared framework, see [Assemblies being removed from Microsoft.AspNetCore.App 3.0](https://github.com/aspnet/AspNetCore/issues/3755).</span></span> <span data-ttu-id="6b7c4-351">Дополнительные сведения о мотивации для этого изменения см. в статье [Breaking changes to Microsoft.AspNetCore.App in 3.0](https://github.com/aspnet/Announcements/issues/325) (Критические изменения в Microsoft.AspNetCore.App 3.0) и записи блога [A first look at changes coming in ASP.NET Core 3.0](https://devblogs.microsoft.com/aspnet/a-first-look-at-changes-coming-in-asp-net-core-3-0/) (Первое знакомство с изменениями в ASP.NET Core 3.0).</span><span class="sxs-lookup"><span data-stu-id="6b7c4-351">For more information on the motivation for this change, see [Breaking changes to Microsoft.AspNetCore.App in 3.0](https://github.com/aspnet/Announcements/issues/325) and [A first look at changes coming in ASP.NET Core 3.0](https://devblogs.microsoft.com/aspnet/a-first-look-at-changes-coming-in-asp-net-core-3-0/).</span></span>

<!-- 
## Additional information
For the complete list of changes, see the [ASP.NET Core 3.0 Release Notes](WHERE IS THIS????).
-->