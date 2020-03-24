---
title: Обработка событий Blazor в ASP.NET Core
author: guardrex
description: Сведения о функциях обработки событий Blazor, включая типы аргументов событий, обратные вызовы событий и управление событиями браузера по умолчанию.
monikerRange: '>= aspnetcore-3.1'
ms.author: riande
ms.custom: mvc
ms.date: 03/16/2020
no-loc:
- Blazor
- SignalR
uid: blazor/event-handling
ms.openlocfilehash: c144841805e07a136f153c25a78c7f9af7c5801b
ms.sourcegitcommit: d64ef143c64ee4fdade8f9ea0b753b16752c5998
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/18/2020
ms.locfileid: "79511370"
---
# <a name="aspnet-core-blazor-event-handling"></a><span data-ttu-id="b15df-103">Обработка событий Blazor в ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b15df-103">ASP.NET Core Blazor event handling</span></span>

<span data-ttu-id="b15df-104">Авторы: [Люк Латэм](https://github.com/guardrex) (Luke Latham) и [Дэниэл Рот](https://github.com/danroth27) (Daniel Roth)</span><span class="sxs-lookup"><span data-stu-id="b15df-104">By [Luke Latham](https://github.com/guardrex) and [Daniel Roth](https://github.com/danroth27)</span></span>

<span data-ttu-id="b15df-105">Компоненты Razor предоставляют функции обработки событий.</span><span class="sxs-lookup"><span data-stu-id="b15df-105">Razor components provide event handling features.</span></span> <span data-ttu-id="b15df-106">Для атрибута HTML-элемента с именем [`@on{EVENT}`](xref:mvc/views/razor#onevent) (например, `@onclick`) и значением типа делегата компонент Razor рассматривает значение атрибута как обработчик событий.</span><span class="sxs-lookup"><span data-stu-id="b15df-106">For an HTML element attribute named [`@on{EVENT}`](xref:mvc/views/razor#onevent) (for example, `@onclick`) with a delegate-typed value, a Razor component treats the attribute's value as an event handler.</span></span>

<span data-ttu-id="b15df-107">Следующий код вызывает метод `UpdateHeading`, когда в пользовательском интерфейсе выбрана кнопка:</span><span class="sxs-lookup"><span data-stu-id="b15df-107">The following code calls the `UpdateHeading` method when the button is selected in the UI:</span></span>

```razor
<button class="btn btn-primary" @onclick="UpdateHeading">
    Update heading
</button>

@code {
    private void UpdateHeading(MouseEventArgs e)
    {
        ...
    }
}
```

<span data-ttu-id="b15df-108">Следующий код вызывает метод `CheckChanged`, когда в пользовательском интерфейсе установлен флажок:</span><span class="sxs-lookup"><span data-stu-id="b15df-108">The following code calls the `CheckChanged` method when the check box is changed in the UI:</span></span>

```razor
<input type="checkbox" class="form-check-input" @onchange="CheckChanged" />

@code {
    private void CheckChanged()
    {
        ...
    }
}
```

<span data-ttu-id="b15df-109">Обработчики событий также могут быть асинхронными и возвращать <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="b15df-109">Event handlers can also be asynchronous and return a <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="b15df-110">Нет необходимости вручную вызывать [StateHasChanged](xref:blazor/lifecycle#state-changes).</span><span class="sxs-lookup"><span data-stu-id="b15df-110">There's no need to manually call [StateHasChanged](xref:blazor/lifecycle#state-changes).</span></span> <span data-ttu-id="b15df-111">Исключения регистрируются при их возникновении.</span><span class="sxs-lookup"><span data-stu-id="b15df-111">Exceptions are logged when they occur.</span></span>

<span data-ttu-id="b15df-112">В следующем примере `UpdateHeading` вызывается асинхронно при выборе кнопки:</span><span class="sxs-lookup"><span data-stu-id="b15df-112">In the following example, `UpdateHeading` is called asynchronously when the button is selected:</span></span>

```razor
<button class="btn btn-primary" @onclick="UpdateHeading">
    Update heading
</button>

@code {
    private async Task UpdateHeading(MouseEventArgs e)
    {
        ...
    }
}
```

## <a name="event-argument-types"></a><span data-ttu-id="b15df-113">Типы аргументов событий</span><span class="sxs-lookup"><span data-stu-id="b15df-113">Event argument types</span></span>

<span data-ttu-id="b15df-114">Для некоторых событий разрешены типы аргументов событий.</span><span class="sxs-lookup"><span data-stu-id="b15df-114">For some events, event argument types are permitted.</span></span> <span data-ttu-id="b15df-115">Указание типа события в вызове метода требуется только в том случае, если тип события используется в методе.</span><span class="sxs-lookup"><span data-stu-id="b15df-115">Specifying an event type in the method call is only necessary if the event type is used in the method.</span></span>

<span data-ttu-id="b15df-116">Поддерживаемые параметры `EventArgs` приведены в следующей таблице.</span><span class="sxs-lookup"><span data-stu-id="b15df-116">Supported `EventArgs` are shown in the following table.</span></span>

| <span data-ttu-id="b15df-117">событие</span><span class="sxs-lookup"><span data-stu-id="b15df-117">Event</span></span>            | <span data-ttu-id="b15df-118">Класс</span><span class="sxs-lookup"><span data-stu-id="b15df-118">Class</span></span>                | <span data-ttu-id="b15df-119">События DOM и примечания</span><span class="sxs-lookup"><span data-stu-id="b15df-119">DOM events and notes</span></span> |
| ---------------- | -------------------- | -------------------- |
| <span data-ttu-id="b15df-120">буфер обмена</span><span class="sxs-lookup"><span data-stu-id="b15df-120">Clipboard</span></span>        | `ClipboardEventArgs` | <span data-ttu-id="b15df-121">`oncut`, `oncopy`, `onpaste`</span><span class="sxs-lookup"><span data-stu-id="b15df-121">`oncut`, `oncopy`, `onpaste`</span></span> |
| <span data-ttu-id="b15df-122">Перетаскивание</span><span class="sxs-lookup"><span data-stu-id="b15df-122">Drag</span></span>             | `DragEventArgs`      | <span data-ttu-id="b15df-123">`ondrag`, `ondragstart`, `ondragenter`, `ondragleave`, `ondragover`, `ondrop`, `ondragend`</span><span class="sxs-lookup"><span data-stu-id="b15df-123">`ondrag`, `ondragstart`, `ondragenter`, `ondragleave`, `ondragover`, `ondrop`, `ondragend`</span></span><br><br><span data-ttu-id="b15df-124">`DataTransfer` и `DataTransferItem` содержат данные перетаскиваемого элемента.</span><span class="sxs-lookup"><span data-stu-id="b15df-124">`DataTransfer` and `DataTransferItem` hold dragged item data.</span></span> |
| <span data-ttu-id="b15df-125">Ошибка</span><span class="sxs-lookup"><span data-stu-id="b15df-125">Error</span></span>            | `ErrorEventArgs`     | `onerror` |
| <span data-ttu-id="b15df-126">событие</span><span class="sxs-lookup"><span data-stu-id="b15df-126">Event</span></span>            | `EventArgs`          | <span data-ttu-id="b15df-127">*Общие сведения*</span><span class="sxs-lookup"><span data-stu-id="b15df-127">*General*</span></span><br><span data-ttu-id="b15df-128">`onactivate`, `onbeforeactivate`, `onbeforedeactivate`, `ondeactivate`, `onended`, `onfullscreenchange`, `onfullscreenerror`, `onloadeddata`, `onloadedmetadata`, `onpointerlockchange`, `onpointerlockerror`, `onreadystatechange`, `onscroll`</span><span class="sxs-lookup"><span data-stu-id="b15df-128">`onactivate`, `onbeforeactivate`, `onbeforedeactivate`, `ondeactivate`, `onended`, `onfullscreenchange`, `onfullscreenerror`, `onloadeddata`, `onloadedmetadata`, `onpointerlockchange`, `onpointerlockerror`, `onreadystatechange`, `onscroll`</span></span><br><br><span data-ttu-id="b15df-129">*Буфер обмена*</span><span class="sxs-lookup"><span data-stu-id="b15df-129">*Clipboard*</span></span><br><span data-ttu-id="b15df-130">`onbeforecut`, `onbeforecopy`, `onbeforepaste`</span><span class="sxs-lookup"><span data-stu-id="b15df-130">`onbeforecut`, `onbeforecopy`, `onbeforepaste`</span></span><br><br><span data-ttu-id="b15df-131">*Ввод*</span><span class="sxs-lookup"><span data-stu-id="b15df-131">*Input*</span></span><br><span data-ttu-id="b15df-132">`oninvalid`, `onreset`, `onselect`, `onselectionchange`, `onselectstart`, `onsubmit`</span><span class="sxs-lookup"><span data-stu-id="b15df-132">`oninvalid`, `onreset`, `onselect`, `onselectionchange`, `onselectstart`, `onsubmit`</span></span><br><br><span data-ttu-id="b15df-133">*Носитель*</span><span class="sxs-lookup"><span data-stu-id="b15df-133">*Media*</span></span><br><span data-ttu-id="b15df-134">`oncanplay`, `oncanplaythrough`, `oncuechange`, `ondurationchange`, `onemptied`, `onpause`, `onplay`, `onplaying`, `onratechange`, `onseeked`, `onseeking`, `onstalled`, `onstop`, `onsuspend`, `ontimeupdate`, `onvolumechange`, `onwaiting`</span><span class="sxs-lookup"><span data-stu-id="b15df-134">`oncanplay`, `oncanplaythrough`, `oncuechange`, `ondurationchange`, `onemptied`, `onpause`, `onplay`, `onplaying`, `onratechange`, `onseeked`, `onseeking`, `onstalled`, `onstop`, `onsuspend`, `ontimeupdate`, `onvolumechange`, `onwaiting`</span></span> |
| <span data-ttu-id="b15df-135">Фокус</span><span class="sxs-lookup"><span data-stu-id="b15df-135">Focus</span></span>            | `FocusEventArgs`     | <span data-ttu-id="b15df-136">`onfocus`, `onblur`, `onfocusin`, `onfocusout`</span><span class="sxs-lookup"><span data-stu-id="b15df-136">`onfocus`, `onblur`, `onfocusin`, `onfocusout`</span></span><br><br><span data-ttu-id="b15df-137">Не включает поддержку `relatedTarget`.</span><span class="sxs-lookup"><span data-stu-id="b15df-137">Doesn't include support for `relatedTarget`.</span></span> |
| <span data-ttu-id="b15df-138">Входные данные</span><span class="sxs-lookup"><span data-stu-id="b15df-138">Input</span></span>            | `ChangeEventArgs`    | <span data-ttu-id="b15df-139">`onchange`, `oninput`</span><span class="sxs-lookup"><span data-stu-id="b15df-139">`onchange`, `oninput`</span></span> |
| <span data-ttu-id="b15df-140">Клавиатура</span><span class="sxs-lookup"><span data-stu-id="b15df-140">Keyboard</span></span>         | `KeyboardEventArgs`  | <span data-ttu-id="b15df-141">`onkeydown`, `onkeypress`, `onkeyup`</span><span class="sxs-lookup"><span data-stu-id="b15df-141">`onkeydown`, `onkeypress`, `onkeyup`</span></span> |
| <span data-ttu-id="b15df-142">Мышь</span><span class="sxs-lookup"><span data-stu-id="b15df-142">Mouse</span></span>            | `MouseEventArgs`     | <span data-ttu-id="b15df-143">`onclick`, `oncontextmenu`, `ondblclick`, `onmousedown`, `onmouseup`, `onmouseover`, `onmousemove`, `onmouseout`</span><span class="sxs-lookup"><span data-stu-id="b15df-143">`onclick`, `oncontextmenu`, `ondblclick`, `onmousedown`, `onmouseup`, `onmouseover`, `onmousemove`, `onmouseout`</span></span> |
| <span data-ttu-id="b15df-144">Указатель мыши</span><span class="sxs-lookup"><span data-stu-id="b15df-144">Mouse pointer</span></span>    | `PointerEventArgs`   | <span data-ttu-id="b15df-145">`onpointerdown`, `onpointerup`, `onpointercancel`, `onpointermove`, `onpointerover`, `onpointerout`, `onpointerenter`, `onpointerleave`, `ongotpointercapture`, `onlostpointercapture`</span><span class="sxs-lookup"><span data-stu-id="b15df-145">`onpointerdown`, `onpointerup`, `onpointercancel`, `onpointermove`, `onpointerover`, `onpointerout`, `onpointerenter`, `onpointerleave`, `ongotpointercapture`, `onlostpointercapture`</span></span> |
| <span data-ttu-id="b15df-146">Колесико мыши</span><span class="sxs-lookup"><span data-stu-id="b15df-146">Mouse wheel</span></span>      | `WheelEventArgs`     | <span data-ttu-id="b15df-147">`onwheel`, `onmousewheel`</span><span class="sxs-lookup"><span data-stu-id="b15df-147">`onwheel`, `onmousewheel`</span></span> |
| <span data-ttu-id="b15df-148">Ход выполнения</span><span class="sxs-lookup"><span data-stu-id="b15df-148">Progress</span></span>         | `ProgressEventArgs`  | <span data-ttu-id="b15df-149">`onabort`, `onload`, `onloadend`, `onloadstart`, `onprogress`, `ontimeout`</span><span class="sxs-lookup"><span data-stu-id="b15df-149">`onabort`, `onload`, `onloadend`, `onloadstart`, `onprogress`, `ontimeout`</span></span> |
| <span data-ttu-id="b15df-150">Сенсорные технологии</span><span class="sxs-lookup"><span data-stu-id="b15df-150">Touch</span></span>            | `TouchEventArgs`     | <span data-ttu-id="b15df-151">`ontouchstart`, `ontouchend`, `ontouchmove`, `ontouchenter`, `ontouchleave`, `ontouchcancel`</span><span class="sxs-lookup"><span data-stu-id="b15df-151">`ontouchstart`, `ontouchend`, `ontouchmove`, `ontouchenter`, `ontouchleave`, `ontouchcancel`</span></span><br><br><span data-ttu-id="b15df-152">`TouchPoint` представляет одну точку касания на устройстве с сенсорным вводом.</span><span class="sxs-lookup"><span data-stu-id="b15df-152">`TouchPoint` represents a single contact point on a touch-sensitive device.</span></span> |

<span data-ttu-id="b15df-153">Дополнительные сведения см. в следующих ресурсах:</span><span class="sxs-lookup"><span data-stu-id="b15df-153">For more information, see the following resources:</span></span>

* <span data-ttu-id="b15df-154">[Классы EventArgs в источнике ссылки на ASP.NET Core (ветвь DotNet/aspnetcore Release/3.1)](https://github.com/dotnet/aspnetcore/tree/release/3.1/src/Components/Web/src/Web).</span><span class="sxs-lookup"><span data-stu-id="b15df-154">[EventArgs classes in the ASP.NET Core reference source (dotnet/aspnetcore release/3.1 branch)](https://github.com/dotnet/aspnetcore/tree/release/3.1/src/Components/Web/src/Web).</span></span>
* <span data-ttu-id="b15df-155">[Веб-документы MDN: GlobalEventHandlers](https://developer.mozilla.org/docs/Web/API/GlobalEventHandlers) &ndash; – содержит сведения о том, какие элементы HTML поддерживают каждое событие DOM.</span><span class="sxs-lookup"><span data-stu-id="b15df-155">[MDN web docs: GlobalEventHandlers](https://developer.mozilla.org/docs/Web/API/GlobalEventHandlers) &ndash; Includes information on which HTML elements support each DOM event.</span></span>

## <a name="lambda-expressions"></a><span data-ttu-id="b15df-156">Лямбда-выражения</span><span class="sxs-lookup"><span data-stu-id="b15df-156">Lambda expressions</span></span>

<span data-ttu-id="b15df-157">Также можно использовать [лямбда-выражения](/dotnet/csharp/programming-guide/statements-expressions-operators/lambda-expressions):</span><span class="sxs-lookup"><span data-stu-id="b15df-157">[Lambda expressions](/dotnet/csharp/programming-guide/statements-expressions-operators/lambda-expressions) can also be used:</span></span>

```razor
<button @onclick="@(e => Console.WriteLine("Hello, world!"))">Say hello</button>
```

<span data-ttu-id="b15df-158">Часто бывает удобно закрывать дополнительные значения, например при переборе набора элементов.</span><span class="sxs-lookup"><span data-stu-id="b15df-158">It's often convenient to close over additional values, such as when iterating over a set of elements.</span></span> <span data-ttu-id="b15df-159">В следующем примере создаются три кнопки, каждая из которых вызывает `UpdateHeading` для передачи аргумента события (`MouseEventArgs`) и номера кнопки (`buttonNumber`) при выборе в пользовательском интерфейсе:</span><span class="sxs-lookup"><span data-stu-id="b15df-159">The following example creates three buttons, each of which calls `UpdateHeading` passing an event argument (`MouseEventArgs`) and its button number (`buttonNumber`) when selected in the UI:</span></span>

```razor
<h2>@_message</h2>

@for (var i = 1; i < 4; i++)
{
    var buttonNumber = i;

    <button class="btn btn-primary"
            @onclick="@(e => UpdateHeading(e, buttonNumber))">
        Button #@i
    </button>
}

@code {
    private string _message = "Select a button to learn its position.";

    private void UpdateHeading(MouseEventArgs e, int buttonNumber)
    {
        _message = $"You selected Button #{buttonNumber} at " +
            $"mouse position: {e.ClientX} X {e.ClientY}.";
    }
}
```

> [!NOTE]
> <span data-ttu-id="b15df-160">**Не** используйте переменную цикла (`i`) в цикле `for` непосредственно в лямбда-выражении.</span><span class="sxs-lookup"><span data-stu-id="b15df-160">Do **not** use the loop variable (`i`) in a `for` loop directly in a lambda expression.</span></span> <span data-ttu-id="b15df-161">В противном случае одна и та же переменная будет использоваться во всех лямбда-выражениях, в результате чего значение `i` будет одинаковым во всех лямбда-выражениях.</span><span class="sxs-lookup"><span data-stu-id="b15df-161">Otherwise the same variable is used by all lambda expressions causing `i`'s value to be the same in all lambdas.</span></span> <span data-ttu-id="b15df-162">Всегда записывайте значение в локальную переменную (`buttonNumber` в предыдущем примере), а затем используйте ее.</span><span class="sxs-lookup"><span data-stu-id="b15df-162">Always capture its value in a local variable (`buttonNumber` in the preceding example) and then use it.</span></span>

## <a name="eventcallback"></a><span data-ttu-id="b15df-163">EventCallback</span><span class="sxs-lookup"><span data-stu-id="b15df-163">EventCallback</span></span>

<span data-ttu-id="b15df-164">Распространенным сценарием с вложенными компонентами является необходимость запускать метод родительского компонента при возникновении события дочернего компонента &mdash; например, когда в дочернем элементе возникает событие `onclick`.</span><span class="sxs-lookup"><span data-stu-id="b15df-164">A common scenario with nested components is the desire to run a parent component's method when a child component event occurs&mdash;for example, when an `onclick` event occurs in the child.</span></span> <span data-ttu-id="b15df-165">Чтобы обеспечить доступ к событиям в компонентах, используйте `EventCallback`.</span><span class="sxs-lookup"><span data-stu-id="b15df-165">To expose events across components, use an `EventCallback`.</span></span> <span data-ttu-id="b15df-166">Родительский компонент может назначить метод обратного вызова `EventCallback` дочернего компонента.</span><span class="sxs-lookup"><span data-stu-id="b15df-166">A parent component can assign a callback method to a child component's `EventCallback`.</span></span>

<span data-ttu-id="b15df-167">В `ChildComponent` в примере приложения (*Components/ChildComponent.razor*) показано, как обработчик `onclick` кнопки настроен на получение делегата `EventCallback` из `ParentComponent` образца.</span><span class="sxs-lookup"><span data-stu-id="b15df-167">The `ChildComponent` in the sample app (*Components/ChildComponent.razor*) demonstrates how a button's `onclick` handler is set up to receive an `EventCallback` delegate from the sample's `ParentComponent`.</span></span> <span data-ttu-id="b15df-168">`EventCallback` вводится с `MouseEventArgs`, что подходит для события `onclick` от периферийного устройства:</span><span class="sxs-lookup"><span data-stu-id="b15df-168">The `EventCallback` is typed with `MouseEventArgs`, which is appropriate for an `onclick` event from a peripheral device:</span></span>

[!code-razor[](common/samples/3.x/BlazorWebAssemblySample/Components/ChildComponent.razor?highlight=5-7,17-18)]

<span data-ttu-id="b15df-169">`ParentComponent` задает для `EventCallback<T>` дочернего компонента (`OnClickCallback`) его метод `ShowMessage`.</span><span class="sxs-lookup"><span data-stu-id="b15df-169">The `ParentComponent` sets the child's `EventCallback<T>` (`OnClickCallback`) to its `ShowMessage` method.</span></span>

<span data-ttu-id="b15df-170">*Pages/ParentComponent.razor*:</span><span class="sxs-lookup"><span data-stu-id="b15df-170">*Pages/ParentComponent.razor*:</span></span>

```razor
@page "/ParentComponent"

<h1>Parent-child example</h1>

<ChildComponent Title="Panel Title from Parent"
                OnClickCallback="@ShowMessage">
    Content of the child component is supplied
    by the parent component.
</ChildComponent>

<p><b>@_messageText</b></p>

@code {
    private string _messageText;

    private void ShowMessage(MouseEventArgs e)
    {
        _messageText = $"Blaze a new trail with Blazor! ({e.ScreenX}, {e.ScreenY})";
    }
}
```

<span data-ttu-id="b15df-171">При выборе кнопки в `ChildComponent`:</span><span class="sxs-lookup"><span data-stu-id="b15df-171">When the button is selected in the `ChildComponent`:</span></span>

* <span data-ttu-id="b15df-172">Вызывается метод `ShowMessage` `ParentComponent`.</span><span class="sxs-lookup"><span data-stu-id="b15df-172">The `ParentComponent`'s `ShowMessage` method is called.</span></span> <span data-ttu-id="b15df-173">`_messageText` обновляется и отображается в `ParentComponent`.</span><span class="sxs-lookup"><span data-stu-id="b15df-173">`_messageText` is updated and displayed in the `ParentComponent`.</span></span>
* <span data-ttu-id="b15df-174">Вызов [StateHasChanged](xref:blazor/lifecycle#state-changes) не требуется в методе обратного вызова (`ShowMessage`).</span><span class="sxs-lookup"><span data-stu-id="b15df-174">A call to [StateHasChanged](xref:blazor/lifecycle#state-changes) isn't required in the callback's method (`ShowMessage`).</span></span> <span data-ttu-id="b15df-175">`StateHasChanged` вызывается автоматически для повторной отрисовки `ParentComponent`, так же как и дочерние события запускают повторную отрисовку компонента в обработчиках событий, которые выполняются в дочернем элементе.</span><span class="sxs-lookup"><span data-stu-id="b15df-175">`StateHasChanged` is called automatically to rerender the `ParentComponent`, just as child events trigger component rerendering in event handlers that execute within the child.</span></span>

<span data-ttu-id="b15df-176">`EventCallback` и `EventCallback<T>` разрешают выполнять асинхронные делегаты.</span><span class="sxs-lookup"><span data-stu-id="b15df-176">`EventCallback` and `EventCallback<T>` permit asynchronous delegates.</span></span> <span data-ttu-id="b15df-177">`EventCallback<T>` является строго типизированным и требует определенного типа аргумента.</span><span class="sxs-lookup"><span data-stu-id="b15df-177">`EventCallback<T>` is strongly typed and requires a specific argument type.</span></span> <span data-ttu-id="b15df-178">`EventCallback` слабо типизирован и допускает любой тип аргумента.</span><span class="sxs-lookup"><span data-stu-id="b15df-178">`EventCallback` is weakly typed and allows any argument type.</span></span>

```razor
<ChildComponent 
    OnClickCallback="@(async () => { await Task.Yield(); _messageText = "Blaze It!"; })" />
```

<span data-ttu-id="b15df-179">Вызов `EventCallback` или `EventCallback<T>` с `InvokeAsync` и ожидание <xref:System.Threading.Tasks.Task>:</span><span class="sxs-lookup"><span data-stu-id="b15df-179">Invoke an `EventCallback` or `EventCallback<T>` with `InvokeAsync` and await the <xref:System.Threading.Tasks.Task>:</span></span>

```csharp
await callback.InvokeAsync(arg);
```

<span data-ttu-id="b15df-180">Используйте `EventCallback` и `EventCallback<T>` для обработки событий и параметров компонента привязки.</span><span class="sxs-lookup"><span data-stu-id="b15df-180">Use `EventCallback` and `EventCallback<T>` for event handling and binding component parameters.</span></span>

<span data-ttu-id="b15df-181">Предпочтительнее использовать строго типизированный `EventCallback<T>` вместо `EventCallback`.</span><span class="sxs-lookup"><span data-stu-id="b15df-181">Prefer the strongly typed `EventCallback<T>` over `EventCallback`.</span></span> <span data-ttu-id="b15df-182">`EventCallback<T>` обеспечивает более эффективное реагирование на ошибки для пользователей компонента.</span><span class="sxs-lookup"><span data-stu-id="b15df-182">`EventCallback<T>` provides better error feedback to users of the component.</span></span> <span data-ttu-id="b15df-183">Как и в случае с другими обработчиками событий пользовательского интерфейса, указание параметра события является необязательным.</span><span class="sxs-lookup"><span data-stu-id="b15df-183">Similar to other UI event handlers, specifying the event parameter is optional.</span></span> <span data-ttu-id="b15df-184">Используйте `EventCallback`, если в обратный вызов не было передано значение.</span><span class="sxs-lookup"><span data-stu-id="b15df-184">Use `EventCallback` when there's no value passed to the callback.</span></span>

## <a name="prevent-default-actions"></a><span data-ttu-id="b15df-185">Запрет действий по умолчанию</span><span class="sxs-lookup"><span data-stu-id="b15df-185">Prevent default actions</span></span>

<span data-ttu-id="b15df-186">Используйте атрибут директивы [`@on{EVENT}:preventDefault`](xref:mvc/views/razor#oneventpreventdefault), чтобы запретить выполнение действия по умолчанию для события.</span><span class="sxs-lookup"><span data-stu-id="b15df-186">Use the [`@on{EVENT}:preventDefault`](xref:mvc/views/razor#oneventpreventdefault) directive attribute to prevent the default action for an event.</span></span>

<span data-ttu-id="b15df-187">Если на устройстве ввода выбран ключ, а фокус находится на текстовом поле, то в браузере в текстовом поле обычно отображается символ ключа.</span><span class="sxs-lookup"><span data-stu-id="b15df-187">When a key is selected on an input device and the element focus is on a text box, a browser normally displays the key's character in the text box.</span></span> <span data-ttu-id="b15df-188">В следующем примере поведение по умолчанию запрещено путем указания атрибута директивы `@onkeypress:preventDefault`.</span><span class="sxs-lookup"><span data-stu-id="b15df-188">In the following example, the default behavior is prevented by specifying the `@onkeypress:preventDefault` directive attribute.</span></span> <span data-ttu-id="b15df-189">Счетчик увеличивается, а ключ **+** не записывается в значение элемента `<input>`:</span><span class="sxs-lookup"><span data-stu-id="b15df-189">The counter increments, and the **+** key isn't captured into the `<input>` element's value:</span></span>

```razor
<input value="@_count" @onkeypress="KeyHandler" @onkeypress:preventDefault />

@code {
    private int _count = 0;

    private void KeyHandler(KeyboardEventArgs e)
    {
        if (e.Key == "+")
        {
            _count++;
        }
    }
}
```

<span data-ttu-id="b15df-190">Указание атрибута `@on{EVENT}:preventDefault` без значения эквивалентно `@on{EVENT}:preventDefault="true"`.</span><span class="sxs-lookup"><span data-stu-id="b15df-190">Specifying the `@on{EVENT}:preventDefault` attribute without a value is equivalent to `@on{EVENT}:preventDefault="true"`.</span></span>

<span data-ttu-id="b15df-191">Значение атрибута также может быть выражением.</span><span class="sxs-lookup"><span data-stu-id="b15df-191">The value of the attribute can also be an expression.</span></span> <span data-ttu-id="b15df-192">В следующем примере `_shouldPreventDefault` является полем `bool`, для которого задано значение `true` или `false`:</span><span class="sxs-lookup"><span data-stu-id="b15df-192">In the following example, `_shouldPreventDefault` is a `bool` field set to either `true` or `false`:</span></span>

```razor
<input @onkeypress:preventDefault="_shouldPreventDefault" />
```

<span data-ttu-id="b15df-193">Для запрета действий по умолчанию не требуется обработчик событий.</span><span class="sxs-lookup"><span data-stu-id="b15df-193">An event handler isn't required to prevent the default action.</span></span> <span data-ttu-id="b15df-194">Обработчик событий и сценарий запрета действий по умолчанию можно использовать независимо друг от друга.</span><span class="sxs-lookup"><span data-stu-id="b15df-194">The event handler and prevent default action scenarios can be used independently.</span></span>

## <a name="stop-event-propagation"></a><span data-ttu-id="b15df-195">Остановка распространения событий</span><span class="sxs-lookup"><span data-stu-id="b15df-195">Stop event propagation</span></span>

<span data-ttu-id="b15df-196">Используйте атрибут директивы [`@on{EVENT}:stopPropagation`](xref:mvc/views/razor#oneventstoppropagation), чтобы остановить распространение событий.</span><span class="sxs-lookup"><span data-stu-id="b15df-196">Use the [`@on{EVENT}:stopPropagation`](xref:mvc/views/razor#oneventstoppropagation) directive attribute to stop event propagation.</span></span>

<span data-ttu-id="b15df-197">В следующем примере при установке флажка события щелчка мышью из второго дочернего элемента `<div>` перестают распространяться в родительский элемент `<div>`:</span><span class="sxs-lookup"><span data-stu-id="b15df-197">In the following example, selecting the check box prevents click events from the second child `<div>` from propagating to the parent `<div>`:</span></span>

```razor
<label>
    <input @bind="_stopPropagation" type="checkbox" />
    Stop Propagation
</label>

<div @onclick="OnSelectParentDiv">
    <h3>Parent div</h3>

    <div @onclick="OnSelectChildDiv">
        Child div that doesn't stop propagation when selected.
    </div>

    <div @onclick="OnSelectChildDiv" @onclick:stopPropagation="_stopPropagation">
        Child div that stops propagation when selected.
    </div>
</div>

@code {
    private bool _stopPropagation = false;

    private void OnSelectParentDiv() => 
        Console.WriteLine($"The parent div was selected. {DateTime.Now}");
    private void OnSelectChildDiv() => 
        Console.WriteLine($"A child div was selected. {DateTime.Now}");
}
```