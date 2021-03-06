---
title: Создание приложения Blazor со списком дел
author: guardrex
description: Узнайте, как создать приложение Blazor по шагам.
monikerRange: '>= aspnetcore-3.0'
ms.author: riande
ms.custom: mvc
ms.date: 12/14/2020
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
uid: tutorials/build-a-blazor-app
ms.openlocfilehash: 6659b075f54292d9546466919f6842b920e6ece1
ms.sourcegitcommit: 3593c4efa707edeaaceffbfa544f99f41fc62535
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/04/2021
ms.locfileid: "97808742"
---
# <a name="build-a-no-locblazor-todo-list-app"></a>Создание приложения Blazor со списком дел

Авторы: [Дэниэл Рот (Daniel Roth)](https://github.com/danroth27) и [Люк Лэтем (Luke Latham)](https://github.com/guardrex)

В этом учебнике показано, как создать и изменить приложение Blazor. Вы научитесь:

> [!div class="checklist"]
> * создавать проект приложения Blazor со списком задач;
> * изменять компоненты Razor;
> * использовать обработку событий и привязку данных в компонентах;
> * Использование маршрутизации в приложении Blazor

Когда вы выполните задачи из этого руководства, у вас будет работающее приложение списка задач.

## <a name="prerequisites"></a>Предварительные требования

::: moniker range=">= aspnetcore-5.0"

[!INCLUDE[](~/includes/5.0-SDK.md)]

::: moniker-end

::: moniker range="< aspnetcore-5.0"

[!INCLUDE[](~/includes/3.1-SDK.md)]

::: moniker-end

## <a name="create-a-todo-list-no-locblazor-app"></a>Создание приложения Blazor со списком задач

1. Создайте в командной строке новое приложение Blazor с именем `TodoList`:

   ```dotnetcli
   dotnet new blazorserver -o TodoList
   ```

   Предыдущая команда создает папку с именем `TodoList` и параметром `-o|--output` для хранения приложения. Папка `TodoList` находится в *корневой папке* проекта. Перейдите в папку `TodoList` с помощью следующей команды:

   ```dotnetcli
   cd TodoList
   ```

1. Добавьте в приложение новый компонент Razor `Todo` с помощью следующей команды.

   ```dotnetcli
   dotnet new razorcomponent -n Todo -o Pages
   ```

   Параметр `-n|--name` в предыдущей команде задает имя нового компонента Razor. Новый компонент создается в папке `Pages` проекта с параметром `-o|--output`.

   > [!IMPORTANT]
   > Имена файлов компонентов Razor должны начинаться с прописной буквы. Откройте папку `Pages` и убедитесь, что имя файла компонента `Todo` начинается с заглавной буквы `T`. Имя файла должно быть `Todo.razor`.

1. Откройте компонент `Todo` в любом редакторе файлов и добавьте директиву `@page` Razor в начало файла с относительным URL-адресом `/todo`.

   `Pages/Todo.razor`:

   [!code-razor[](build-a-blazor-app/samples_snapshot/Todo0.razor?highlight=1)]

   Сохраните файл `Pages/Todo.razor`.

1. Добавьте компонент `Todo` на панель навигации.

   Компонент `NavMenu` используется в макете этого приложения. Макетами называются компоненты, которые избавляют от дублирования содержимого в приложении. Когда в приложении загружается URL-адрес компонента, компонент `NavLink` предоставляет соответствующее указание в пользовательском интерфейсе.

   В неупорядоченном списке (`<ul>...</ul>`) компонента `NavMenu` добавьте указанный ниже элемент списка (`<li>...</li>`) и компонент `NavLink` для компонента `Todo`.

   В `Shared/NavMenu.razor`:

   [!code-razor[](build-a-blazor-app/samples_snapshot/NavMenu.razor?highlight=5-9)]

   Сохраните файл `Shared/NavMenu.razor`.

1. Скомпилируйте и запустите приложение, выполнив команду [`dotnet watch run`](/aspnet/core/tutorials/dotnet-watch) в командной оболочке из папки `TodoList`. После запуска приложения перейдите на страницу списка дел, щелкнув ссылку **`Todo`** на панели навигации приложения. В результате будет загружена страница по адресу `/todo`.

   Оставьте приложение выполняться в командной оболочке. При каждом сохранении файла приложение автоматически перестраивается. Браузер временно утрачивает подключение к приложению на время компиляции и перезапуска. При восстановлении подключения страница в браузере автоматически перезагружается.

1. Добавьте в корень проекта (папка `TodoList`) файл `TodoItem.cs`, который будет содержать класс для элемента списка дел. Используйте следующий код C# для класса `TodoItem`.

   `TodoItem.cs`:

   [!code-csharp[](build-a-blazor-app/samples_snapshot/TodoItem.cs)]

1. Вернитесь к компоненту `Todo` и выполните указанные ниже задачи.

   * Добавьте поле для элементов списка дел в блоке `@code`. Компонент `Todo` использует это поле для сохранения состояния списка дел.
   * Добавьте разметку неупорядоченного списка и цикл `foreach` для отображения каждого элемента списка дела в виде элемента списка (`<li>`).

   `Pages/Todo.razor`:

   [!code-razor[](build-a-blazor-app/samples_snapshot/Todo2.razor?highlight=5-10,13)]

1. Приложению необходимы элементы пользовательского интерфейса для добавления элементов в список дел. Добавьте текстовое поле (`<input>`) и кнопку (`<button>`) под неупорядоченным списком (`<ul>...</ul>`).

   [!code-razor[](build-a-blazor-app/samples_snapshot/Todo3.razor?highlight=12-13)]

1. Сохраните файл `TodoItem.cs` и обновленный файл `Pages/Todo.razor`. При сохранении файлов в командной оболочке будет автоматически выполнена повторная сборка приложения. Браузер временно утратит подключение к приложению, но когда подключение будет восстановлено, браузер перезагрузит страницу.

1. При нажатии кнопки **`Add todo`** ничего не происходит, так как к кнопке не подключен обработчик событий.

1. Добавьте метод `AddTodo` в компонент `Todo` и зарегистрируйте его для нажатий кнопки с помощью атрибута `@onclick`. Теперь при нажатии кнопки вызывается метод C# `AddTodo`:

   [!code-razor[](build-a-blazor-app/samples_snapshot/Todo4.razor?highlight=2,7-10)]

1. Чтобы получить заголовок нового элемента списка дел, добавьте строковое поле `newTodo` в начало блока `@code`.

   [!code-razor[](build-a-blazor-app/samples_snapshot/Todo5.razor?highlight=3)]

   Измените текстовый элемент `<input>`, чтобы привязать `newTodo` с помощью атрибута `@bind`.

   ```razor
   <input placeholder="Something todo" @bind="newTodo" />
   ```

1. Обновите метод `AddTodo`, чтобы добавить `TodoItem` с указываемым названием в список. Очистите значение текстового поля, задав пустую строку в качестве значения для `newTodo`.

   [!code-razor[](build-a-blazor-app/samples_snapshot/Todo6.razor?highlight=19-26)]

1. Сохраните файл `Pages/Todo.razor`. В командной оболочке будет автоматически выполнена повторная сборка приложения. После повторного подключения браузера к приложению страница в браузере перезагрузится.

1. Вы можете сделать текст заголовка для каждого элемента списка дел редактируемым, а по дополнительному флажку пользователь сможет отслеживать завершение задач. Добавьте флажок для каждого элемента списка дел и привяжите его значение к свойству `IsDone`. Замените `@todo.Title` элементом `<input>`, который привязан к `todo.Title` с помощью `@bind`.

   [!code-razor[](build-a-blazor-app/samples_snapshot/Todo7.razor?highlight=4-7)]

1. Обновите заголовок `<h3>`, чтобы в нем отображалось количество незавершенных дел в списке (`IsDone` имеет значение `false`).

   ```razor
   <h3>Todo (@todos.Count(todo => !todo.IsDone))</h3>
   ```

1. Готовый компонент `Todo` (`Pages/Todo.razor`):

   [!code-razor[](build-a-blazor-app/samples_snapshot/Todo1.razor)]

1. Сохраните файл `Pages/Todo.razor`. В командной оболочке будет автоматически выполнена повторная сборка приложения. После повторного подключения браузера к приложению страница в браузере перезагрузится.

1. Добавьте элементы, измените их и пометьте элементы списка дел как завершенные, чтобы протестировать компонент.

1. По окончании завершите работу приложения в командной оболочке. Многие командные оболочки принимают команду клавиатуры <kbd>CTRL</kbd>+<kbd>C</kbd> для остановки приложения.

## <a name="next-steps"></a>Дальнейшие действия

В этом руководстве вы узнали, как выполнять следующие задачи:

> [!div class="checklist"]
> * создавать проект приложения Blazor со списком задач;
> * изменять компоненты Razor;
> * использовать обработку событий и привязку данных в компонентах;
> * Использование маршрутизации в приложении Blazor

Подробные сведения об инструментах для ASP.NET Core Blazor:

> [!div class="nextstepaction"]
> <xref:blazor/tooling>
