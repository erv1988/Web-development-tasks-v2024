# Работа с ASP.Net

# Часть I

# `01` Подготовительный этап

Минимальный набор инструментов для разработки на ASP.Net:

- [.NET SDK x64](https://dotnet.microsoft.com/en-us/download)
- [Visual studio code](https://code.visualstudio.com/download)

Для более удобной разработки потребуется:

- [Visual Studio 2022](https://visualstudio.microsoft.com/ru/downloads/)

# `02` Немного о технологии

`ASP.NET Core` — это кроссплатформенная высокопроизводительная платформа с открытым исходным кодом для создания современных облачных приложений, подключенных к Интернету.

С помощью `ASP.NET Core` вы можете:

- Создавать веб-приложения и сервисы, приложения Интернета вещей (IoT) и мобильные серверные части.
- Использовать разнообразные инструменты разработки в Windows, macOS и Linux.
- Развертывать в облаке или локально.
- Вести разработку на `.NET`.

ASP.NET Core MVC предоставляет функции для создания веб-API и веб-приложений:

- Шаблон `Модель-Представление-Контроллер` (MVC) помогает сделать ваши веб-API и веб-приложения пригодными для тестирования.
- `Razor Pages` — это модель программирования на основе страниц, которая упрощает и повышает продуктивность создания веб-интерфейса.
- Разметка `Razor` обеспечивает эффективный синтаксис для страниц `Razor` и представлений MVC.
- Вспомогательные тег-функции позволяют серверному коду участвовать в создании и отображении HTML-элементов в файлах Razor.
- Встроенная поддержка нескольких форматов данных и согласование контента позволяют вашим веб-API работать с широким кругом клиентов, включая браузеры и мобильные устройства.
- Привязка модели автоматически сопоставляет данные из HTTP-запросов с параметрами метода действия.
- Проверка модели автоматически выполняет проверку на стороне клиента и на стороне сервера.

`ASP.NET Core` включает `Blazor` для создания интерактивного веб-интерфейса пользователя, а также интегрируется с другими популярными интерфейсными платформами `JavaScript`, такими как `Angular`, `React`, `Vue` и `Bootstrap`.

Ориентация на `.NET` имеет несколько преимуществ, и эти преимущества увеличиваются с каждым выпуском. Некоторые преимущества `.NET` перед `.NET Framework` включают в себя:

- Кроссплатформенность. Работает на **Windows**, **macOS** и **Linux**.
- Улучшенная производительность
- Параллельное управление версиями
- Новые API
- Открытый источник


# `03` Разработка нового веб-интерфейса на стороне сервера

## `03.1` Создание проекта:

- открыть терминал (**cmd.exe** или **powershell.exe**)
- с использованием команды **cd** перейти в папку с будущим проектом

```dotnetcli
dotnet new webapp -o RazorPagesApp
```

Команда `dotnet new` создает новый проект Razor Pages в папке RazorPagesApp.

Откройте проект с использованием VSCode или Visual Studio.

Изучите файлы проекта:

* Папка страниц

    Содержит страницы Razor и вспомогательные файлы. Каждая страница Razor представляет собой пару файлов:

    Файл `.cshtml` с разметкой HTML с кодом C# с использованием синтаксиса Razor.

    Файл `.cshtml.cs`, содержащий код C#, обрабатывающий события страницы.

    Имена вспомогательных файлов начинаются с подчеркивания. Например, `_Layout.cshtml` файл настраивает элементы пользовательского интерфейса, общие для всех страниц. `_Layout.cshtml` настраивает меню навигации вверху страницы и уведомление об авторских правах внизу страницы. 

* корневая папка www
    Содержит статические ресурсы, такие как файлы HTML, файлы JavaScript и файлы CSS. 

* appsettings.json

    Содержит данные конфигурации, например строки подключения. 

* Program.cs
    Содержит следующий код:

    ```cs
    var builder = WebApplication.CreateBuilder(args);

    // Регистрация сервисов.
    builder.Services.AddRazorPages();

    var app = builder.Build();
    // конфигурация обработчиков HTTP запросов.
    if (!app.Environment.IsDevelopment())
    {
        app.UseExceptionHandler("/Error");
        app.UseHsts();
    }

    // Настройка функционала сервера
    app.UseHttpsRedirection();
    app.UseStaticFiles();

    app.UseRouting();

    app.UseAuthorization();

    app.MapRazorPages();

    app.Run();
    ```

Следующие строки кода в этом файле создают файл `WebApplicationBuilder` с предварительно настроенными значениями по умолчанию, добавляют поддержку Razor Pages в контейнер внедрения зависимостей и собирают приложение:

    ```cs
    var builder = WebApplication.CreateBuilder(args);
    builder.Services.AddRazorPages();
    var app = builder.Build();
    ```

Страница исключений разработчика включена по умолчанию и предоставляет полезную информацию об исключениях. Рабочие приложения не следует запускать в режиме разработки, поскольку страница исключений разработчика может привести к утечке конфиденциальной информации.

Следующий код устанавливает конечную точку исключения /Errorи включает протокол HTTP Strict Transport Security (HSTS), когда приложение не работает в режиме разработки:

    ```cs
    if (!app.Environment.IsDevelopment())
    {
        app.UseExceptionHandler("/Error");
        app.UseHsts();
    }
    ```

Например, приведенный выше код выполняется, когда приложение находится в рабочем или тестовом режиме. 

Следующий код включает различные промежуточные программы:

`app.UseHttpsRedirection();`: перенаправляет HTTP-запросы на HTTPS.
`app.UseStaticFiles();` : позволяет обслуживать статические файлы, такие как HTML, CSS, изображения и JavaScript. 
`app.UseRouting();`: добавляет сопоставление маршрутов в конвейер промежуточного программного обеспечения. 
`app.MapRazorPages();`: настраивает маршрутизацию конечной точки для Razor Pages.
`app.UseAuthorization();`: разрешает пользователю доступ к защищенным ресурсам. Это приложение не использует авторизацию, поэтому эту строку можно удалить.
`app.Run();`: запускает приложение.

## `03.2` Запуск приложения

Запуск приложения в VSCode через терминал:

```dotnetcli
dotnet run
```

Запуск приложения в Visual Studio:

- `Ctrl`+`F5` - запуск без отлажчика
- `F5` - запуск с отладчиком

> В Visual Studio есть возможность запуска отладчика с открытием браузера.

В терминале / окне Output отображается информация об адресе сервера, по которому доступно приложение:

```
info: Microsoft.Hosting.Lifetime[14]
      Now listening on: http://localhost:5111
info: Microsoft.Hosting.Lifetime[0]
      Application started. Press Ctrl+C to shut down.
info: Microsoft.Hosting.Lifetime[0]
      Hosting environment: Development
info: Microsoft.Hosting.Lifetime[0]
      Content root path: ...\RazorPagesApp
info: Microsoft.Hosting.Lifetime[0]
      Application is shutting down...
```

Открыв в браузере адрес `http://localhost:5111`  откроется :

![webapp](img/01.png?raw=true)

## Задание 

1. Откройте и отредактируйте файл `Index.cshtml`, замени фразу `Welcome` на `Привет, мир!`:

```cshtml
@page
@model IndexModel
@{
    ViewData["Title"] = "Home page";
}

<div class="text-center">
    <h1 class="display-4">Привет, Мир!</h1>
    <p>Learn about <a href="https://docs.microsoft.com/aspnet/core">building Web apps with ASP.NET Core</a>.</p>
</div>
```

Ознакомьтесь с результатом.

2. Проэспериментируйте с файлами `Index.cshtml`, `Privacy.cshtml` и `site.css`, изменив содержимое и дизайн страниц по своему выбору.

## `03.3` Создание модели данных

> Перед выполнением следующих шагов, сохраните все изменения в системе GIT


1. В обозревателе решений щелкните правой кнопкой мыши проекта > `Добавить` > `Новая папка` . Назовите папку **Models**.

2. Щелкните на папку **Models** правой кнопкой мыши. Выберите `Добавить` > `Класс` . Назовите класс **Movie**. Содержимое класса **Movie**:

```csharp
using System.ComponentModel.DataAnnotations;

namespace RazorPagesApp.Models
{
    public class Movie
    {
        public int Id { get; set; }
        public string? Title { get; set; }
        [DataType(DataType.Date)]
        public DateTime ReleaseDate { get; set; }
        public string? Genre { get; set; }
        public decimal Price { get; set; }
    }
}
```

Класс **Movie** содержит:

- Поле `ID` требуется базе данных для первичного ключа.
- Атрибут `[DataType]`, указывающий тип данных свойстве `ReleaseDate`. С этим атрибутом:
    - Пользователю не требуется вводить информацию о времени в поле даты.
    - Отображается только дата, а не информация о времени.
- Знак вопроса после `string` указывает, что свойство имеет значение `NULL`. 

> Задание: Выполните вышеописанные действия и убедитесть в работоспособности проекта.

3.  С использованием инструмента формирования шаблонов (создания, чтения, обновления и удаления - CRUD) создать представление модели данных для класса `Movie`.

    3.1. Создайте папку «Pages/Movies» :
        - Щелкните правой кнопкой мыши папку «Pages» > «Добавить» > «Новая папка» .
        - Назовите папку «Movies» .
    3.2. Щелкните правой кнопкой мыши папку «Pages/Movies» > «Добавить» > «Новый элемент шаблона» .

![new](img/02.png?raw=true)
    
    3.3. В диалоговом окне «Добавить новый шаблон» выберите «Razor Pages using Entity Framework (CRUD)» > «Добавить» .

![new](img/03.png?raw=true)

    3.4. Заполните диалоговое окно «Добавить страницы Razor с помощью Entity Framework (CRUD)» :

        - В раскрывающемся списке Класс модели выберите Movie (RazorPagesMovie.Models) .
        - В строке Класс контекста данных выберите знак + (плюс).
        - В диалоговом окне «Добавить контекст данных»RazorPagesMovie.Data.RazorPagesMovieContext создается имя класса .
        - В раскрывающемся списке «Поставщик базы данных» выберите SQL Server .
        - Выберите Добавить .

![new](img/05.png?raw=true)

> В `appsettings.json` файл добавляется строка подключения, используемая для подключения к локальной базе данных.

4.  С использованием системы Git проанализируйте изменения в кодах проекта

5.  Для инициализации базы данных используется утилита фрейморка EntityFramework `dotnet ef`. Утилита позволяет

    - Создать исходную схему базы данных.
    - Постепенно обновлять схему базы данных, обеспечивать ее синхронизацию с моделью данных приложения. Существующие данные в базе данных сохраняются.

    5.1. Откройте терминал (cmd или Powershell). Терминал можно открыть с использованием контекстного меню Visual Studio `Открыть в терминале` (меню открывает при нажатии правой клавишей мыши по проекту). При необходимости треуется командами `cd` перейти в каталог, содержащий файл `Program.cs`.

    5.2. Выполнить команды:

    ```dotnetcli
    dotnet ef migrations add InitialCreate
    dotnet ef database update
    ```
    Команда `migrations` генерирует код для создания исходной схемы базы данных. Схема основана на модели, указанной в **DbContext**. Аргумент **InitialCreate** используется для именования миграций. Можно использовать любое имя, но по соглашению выбирается имя, описывающее миграцию. При последующих изменениях модели базы данных необходимо использовать новое имя.

    Команда `update` запускает **Up** метод в миграциях, которые не были применены. В этом случае `update` запускается **Up** метод в `Migrations/<time-stamp>_InitialCreate.cs` файле, который создает базу данных.

    > Изучите исходный код получившегося файла. Этот код пришлось бы писать, если бы вы решили инициализировать базу данных без использования утилиты `dotnet ef`.

    > Если в консоли сообщение вида: "Не удалось выполнить, так как не найдены указанная команда или указанный файл.", то необходимо установить утилиту с использованием следующей команды:

    ```dotnetcli
    dotnet tool install --global dotnet-ef
    ```

    Контекст данных `RazorPagesMovieContext` (см. файл `Data\RazorPagesAppContext.cs`) является производным классом от  `Microsoft.EntityFrameworkCore.DbContext` и выполняет следующий функционал:
        - Указывает, какие сущности включены в модель данных. 
        - Координирует функции EF Core, такие как создание, чтение, обновление и удаление, для модели данных **Movie**.

    ```csharp
    using Microsoft.EntityFrameworkCore;

    namespace RazorPagesApp.Data
    {
        public class RazorPagesAppContext : DbContext
        {
            public RazorPagesAppContext (DbContextOptions<RazorPagesAppContext> options)
                : base(options)
            {
            }

            public DbSet<RazorPagesApp.Models.Movie> Movie { get; set; } = default!;
        }
    }
    ```

    Приведенный выше код создает свойство `DbSet<Movie>` для набора сущностей. В терминологии Entity Framework набор сущностей обычно соответствует таблице базы данных. Сущность соответствует строке в таблице.

    Имя строки подключения передается в контекст путем вызова метода объекта **DbContextOptions** . При локальной разработке система конфигурации считывает строку подключения из `appsettings.json` файла. Подробнее о строках подключения можете узнать из курса Баз данных, либо в интернете.

    ## Задание

    1. Запустите приложение и добавьте **/Movies** URL-адрес в браузере (http://localhost:port/movies).

    Если вы получили следующую ошибку:
    ```
    SqlException: Cannot open database "RazorPagesMovieContext-GUID" requested by the login. The login failed.
    Login failed for user 'User-name'.
    ```

    то вы пропустили этап миграции.

    2. Проверьте ссылку «Create New» .
    
    ![new](img/06.png?raw=true)
    
    3. Проверьте ссылки «Edit» , «Details» и «Delete».

    ![new](img/07.png?raw=true)

    4. Отредактируйте сайт, заменим англоязычные команды на русский язык: "Новый", "Редактировать", "Детали", "Удалить".
    5. Изучите контекст, зарегистрированный с помощью внедрения зависимостей. ASP.NET Core построен с использованием внедрения зависимостей. Службы, такие как контекст базы данных EF Core, регистрируются с помощью внедрения зависимостей во время запуска приложения. Компоненты, которым требуются эти службы (например, Razor Pages), предоставляются через параметры конструктора. Код конструктора, который получает экземпляр контекста базы данных, показан позже в этом руководстве.
    
    Инструмент формирования шаблонов автоматически создал контекст базы данных и зарегистрировал его в контейнере внедрения зависимостей. Следующий выделенный код добавляется в файл `Program.cs`:

    ```csharp
    builder.Services.AddDbContext<RazorPagesMovieContext>(options =>
    options.UseSqlite(builder.Configuration.GetConnectionString("RazorPagesMovieContext") ?? throw new InvalidOperationException("Connection string 'RazorPagesMovieContext' not found.")));
    ```

    5.3. Изучите модель страницы `Pages/Movies/Index.cshtml.cs` :

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using System.Threading.Tasks;
    using Microsoft.AspNetCore.Mvc;
    using Microsoft.AspNetCore.Mvc.RazorPages;
    using Microsoft.EntityFrameworkCore;
    using RazorPagesApp.Data;
    using RazorPagesApp.Models;

    namespace RazorPagesApp.Pages.Movies
    {
        public class IndexModel : PageModel
        {
            private readonly RazorPagesApp.Data.RazorPagesAppContext _context;

            public IndexModel(RazorPagesApp.Data.RazorPagesAppContext context)
            {
                _context = context;
            }

            public IList<Movie> Movie { get;set; } = default!;

            public async Task OnGetAsync()
            {
                if (_context.Movie != null)
                {
                    Movie = await _context.Movie.ToListAsync();
                }
            }
        }
    }
    ```

    Страницы Razor Pages являются производными от `PageModel`. По соглашению производный от `PageModel` класс называется *PageName**Model***. Например, индексная страница называется *Index**Model***.

    Конструктор использует внедрение зависимостей для добавления RazorPagesMovieContextна страницу:

    ```csharp
        public class IndexModel : PageModel
        {
            private readonly RazorPagesApp.Data.RazorPagesAppContext _context;

            public IndexModel(RazorPagesApp.Data.RazorPagesAppContext context)
            {
                _context = context;
            }
    ```

    Когда делается `GET` запрос на страницу, метод `OnGetAsync` возвращает список фильмов на страницу Razor. На странице Razor вызывается `OnGetAsync` или `OnGet` для инициализации состояния страницы. В этом случае `OnGetAsync` получает список фильмов и отображает их.

    Метод `OnGet` возвращает `void`, `OnGetAsync` возвращает `Task`. 

    5.4. Изучите страницу `Pages/Movies/Index.cshtml`:

    ```html
    @page
    @model RazorPagesApp.Pages.Movies.IndexModel

    @{
        ViewData["Title"] = "Index";
    }

    <h1>Index</h1>

    <p>
        <a asp-page="Create">Create New</a>
    </p>
    <table class="table">
        <thead>
            <tr>
                <th>
                    @Html.DisplayNameFor(model => model.Movie[0].Title)
                </th>
                <th>
                    @Html.DisplayNameFor(model => model.Movie[0].ReleaseDate)
                </th>
                <th>
                    @Html.DisplayNameFor(model => model.Movie[0].Genre)
                </th>
                <th>
                    @Html.DisplayNameFor(model => model.Movie[0].Price)
                </th>
                <th></th>
            </tr>
        </thead>
        <tbody>
    @foreach (var item in Model.Movie) {
            <tr>
                <td>
                    @Html.DisplayFor(modelItem => item.Title)
                </td>
                <td>
                    @Html.DisplayFor(modelItem => item.ReleaseDate)
                </td>
                <td>
                    @Html.DisplayFor(modelItem => item.Genre)
                </td>
                <td>
                    @Html.DisplayFor(modelItem => item.Price)
                </td>
                <td>
                    <a asp-page="./Edit" asp-route-id="@item.Id">Edit</a> |
                    <a asp-page="./Details" asp-route-id="@item.Id">Details</a> |
                    <a asp-page="./Delete" asp-route-id="@item.Id">Delete</a>
                </td>
            </tr>
    }
        </tbody>
    </table>
    ```

    Razor может перейти от HTML к C# или к разметке, специфичной для Razor. Если за символом `@` следует зарезервированное ключевое слово Razor, он переходит в разметку, специфичную для Razor, в противном случае он переходит в разметку C#.

    * Директива `@page` - декларирует поддержку MVC, что означает, что он может обрабатывать запросы. `@page` должна быть первой директивой Razor на странице. `@page` и `@model` являются примерами перехода на разметку, специфичную для Razor. Дополнительные сведения можно изучить в справке по **Синтаксису Razor**.
    * Директива `@model` - определяет тип модели, передаваемой на страницу Razor. Указанный производный класс становится доступным для страницы Razor. Модель используется в помощниках HTML `@Html.DisplayNameFor` и `@Html.DisplayFor`.

    Изучите лямбда-выражение, используемое в следующем помощнике HTML:

    ```csharp
    @Html.DisplayNameFor(model => model.Movie[0].Title)
    ```

    Помощник HTML `DisplayNameFor` в лямбда-выражении описывает доступ к свойству `Title` для определения отображаемого имени. Лямбда-выражение скорее проверяется, чем оценивается. Это означает, что не будет нарушений прав доступа, когда **model**, **model.Movie** или **model.Movie[0]** равны null. Когда вычисляется лямбда-выражение, например, с помощью `@Html.DisplayFor(modelItem => item.Title)`, то оцениваются значения свойств модели.

    5.5. Страница макета
    Выберите ссылки меню **RazorPagesMovie** , **Home** и **Privacy** . На каждой странице отображается один и тот же макет меню. Расположение меню реализовано в файле `Pages/Shared/_Layout.cshtml`.

    Шаблоны макетов позволяют макету HTML-контейнера :

    - описываться в одном месте.
    - применяться на нескольких страницах сайта.
    
    Найдите строку **@RenderBody()** . **RenderBody** - это оператор-заполнитель, в котором отображаются все представления, специфичные для страницы, заключенные в страницу макета. Например, на странице «Privacy» содержимое `Pages/Privacy.cshtml`  будет отображено внутри метода **RenderBody**.

    Свойство **Layout** задается в файле `Pages/_ViewStart.cshtml` :

    ```html
    @{
       Layout = "_Layout";
    }
    ```

    Разметка устанавливает файл макета `Pages/Shared/_Layout.cshtml` для всех файлов Razor в папке Pages .

    5.6. ViewData и макет

    Рассмотрим разметку файла `Pages/Movies/Index.cshtml`:

    ```csharp
    @page
    @model RazorPagesApp.Pages.Movies.IndexModel

    @{
        ViewData["Title"] = "Index";
    }
    ```

    Предыдущая выделенная разметка является примером перехода Razor на C#. Символы `{` и `}` заключают в себе блок кода C#.

    Базовый класс `PageModel`  содержит свойство словаря **ViewData**, которое можно использовать для передачи данных в представление. Объекты добавляются в словарь **ViewData** с использованием пары [*ключ*]=*значение*. В предыдущем примере свойство **Title**  добавляется в словарь **ViewData**.

    Свойство **Title** используется в файле `Pages/Shared/_Layout.cshtml`. Следующая разметка показывает первые несколько строк файла `_Layout.cshtml`.

    ```html
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="utf-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1.0" />
        <title>@ViewData["Title"] - RazorPagesApp</title>
        <link rel="stylesheet" href="~/lib/bootstrap/dist/css/bootstrap.min.css" />
        <link rel="stylesheet" href="~/css/site.css" asp-append-version="true" />
        <link rel="stylesheet" href="~/RazorPagesApp.styles.css" asp-append-version="true" />
    </head>
    ```

    ## Задание

    1. Проверьте все страницы и переименуйте англоязычные элементы на русский язык.
    2. Найдите следующий элемент привязки в `Pages/Shared/_Layout.cshtml` файле.

    ```html
    <a class="navbar-brand" asp-area="" asp-page="/Index">RazorPagesApp</a>
    ```

    3. Замените предыдущий элемент следующей разметкой:

    ```html
    <a class="navbar-brand" asp-page="/Movies/Index">Фильмотека</a>
    ```

    Указанный элемент привязки — это вспомогательный тег-элемент (Tag Helper). Атрибут и значение тега `asp-page="/Movies/Index"`  создают ссылку на страницу `/Movies/Index`. Значение атрибута **asp-area** отсутствует, поэтому данная область не используется в ссылке. 
    
    4. Сохраните изменения и протестируйте приложение. Проверьте ссылки Home, , Create , Edit и Delete . Каждой странице задается заголовок, который вы можете увидеть во вкладке браузера. Когда вы добавляете страницу в закладки, для закладки используется заголовок.

    5.7. Страница создания

    Проверьте файл страницы `Pages/Movies/Create.cshtml`:

    - Элемент <form method="post"> представляет собой элемент для ввода данных.
    - Вспомогательные функции тегов **Validation** (`<div asp-validation-summary` и `<span asp-validation-for`) отображают ошибки проверки.
    - Вспомогательная функция тега **Label** (`<label asp-for="Movie.Title" class="control-label"></label>`) создает подпись к метке и атрибут `[for]` для свойства Title.
    - Вспомогательная функция тега **Input** (`<input asp-for="Movie.Title" class="form-control">`) использует атрибуты **DataAnnotations** и создает HTML-атрибуты, необходимые для проверки `jQuery` на стороне клиента.

    С использованием отладчика проанализируйте работу страницы создания.

    5.8. Работа с БД

    Объект `RazorPagesMovieContext` обрабатывает задачу подключения к базе данных и сопоставления объектов **Movie** с записями базы данных. Контекст базы данных регистрируется с помощью контейнера внедрения зависимостей в файле `Program.cs`:

    ```csharp
    builder.Services.AddDbContext<RazorPagesMovieContext>(options =>
    options.UseSqlServer(builder.Configuration.GetConnectionString("RazorPagesMovieContext") ?? throw new InvalidOperationException("Connection string 'RazorPagesMovieContext' not found.")));

    ```

    Система конфигурации ASP.NET Core считывает ключ **ConnectionString**. Для разработки на локальном уровне конфигурация получает строку подключения из файла `appsettings.json`.

    ```json
    "ConnectionStrings": {
        "RazorPagesAppContext": "Server=(localdb)\\mssqllocaldb;Database=RazorPagesAppContext-6b55f102-6d00-4389-9168-ff61f7c8749e;Trusted_Connection=True;MultipleActiveResultSets=true"
    }
    ```

    **SQL Server Express LocalDB**  — это упрощенная версия ядра СУБД **SQL Server Express**, предназначенная для разработки программ. **LocalDB** запускается по запросу в пользовательском режиме, поэтому настройки не слишком сложны. По умолчанию база данных LocalDB создает файлы ***.mdf** в каталоге `C:\Users\<user>\`

    ![LocalDB](img/08.png?raw=true)

    Щелкните правой кнопкой мыши таблицу **Movie** и выберите пункт Конструктор представлений:

    ![LocalDB](img/09.png?raw=true)
    ![LocalDB](img/10.png?raw=true)

    Обратите внимание на значок с изображением ключа рядом с **ID**. По умолчанию EF создает свойство с именем **ID** для первичного ключа.

    Щелкните правой кнопкой мыши таблицу **Movie** и выберите пункт Просмотреть данные

    ![LocalDB](img/11.png?raw=true)

    5.9. Заполнение базы данных

    Создайте класс SeedData в папке Models со следующим кодом:

    ```csharp
    using Microsoft.EntityFrameworkCore;
    using RazorPagesMovie.Data;

    namespace RazorPagesMovie.Models;

    public static class SeedData
    {
        public static void Initialize(IServiceProvider serviceProvider)
        {
            using (var context = new RazorPagesAppContext(
                serviceProvider.GetRequiredService<
                    DbContextOptions<RazorPagesAppContext>>()))
            {
                if (context == null || context.Movie == null)
                {
                    throw new ArgumentNullException("Null RazorPagesAppContext");
                }

                // Look for any movies.
                if (context.Movie.Any())
                {
                    return;   // DB has been seeded
                }

                context.Movie.AddRange(
                    new Movie
                    {
                        Title = "When Harry Met Sally",
                        ReleaseDate = DateTime.Parse("1989-2-12"),
                        Genre = "Romantic Comedy",
                        Price = 7.99M
                    },

                    new Movie
                    {
                        Title = "Ghostbusters ",
                        ReleaseDate = DateTime.Parse("1984-3-13"),
                        Genre = "Comedy",
                        Price = 8.99M
                    },

                    new Movie
                    {
                        Title = "Ghostbusters 2",
                        ReleaseDate = DateTime.Parse("1986-2-23"),
                        Genre = "Comedy",
                        Price = 9.99M
                    },

                    new Movie
                    {
                        Title = "Rio Bravo",
                        ReleaseDate = DateTime.Parse("1959-4-15"),
                        Genre = "Western",
                        Price = 3.99M
                    }
                );
                context.SaveChanges();
            }
        }
    }
    ```

    Обновите следующий выделенный `Program.cs` код:

    ```csharp
    var app = builder.Build();

    using (var scope = app.Services.CreateScope())
    {
        var services = scope.ServiceProvider;

        SeedData.Initialize(services);
    }

    if (!app.Environment.IsDevelopment())
    {
        app.UseExceptionHandler("/Error");
        app.UseHsts();
    }
    ```

    В предыдущем коде было изменено, `Program.cs` чтобы выполнить следующие действия:

    - Получение экземпляра контекста базы данных из контейнера внедрения зависимостей (DI).
    - Вызовите метод seedData.Initialize, передав ему экземпляр контекста базы данных.
    - Высвобождение контекста после завершения работы метода заполнения. Оператор using гарантирует удаление контекста.
    
    Если **Update-Database** не выполнится, возникает следующее исключение:

    ```
    SqlException: Cannot open database "RazorPagesMovieContext-" requested by the login. The login failed. Login failed for user 'user name'.
    ```

    Для тестирования удалите все записи в базе данных для запуска метода seed. Остановите и запустите приложение, чтобы начать заполнение базы данных. Если база данных не заполнена, установите точку останова в if (context.Movie.Any()) и пошагово выполните код.

    В приложении должны отобразиться заполненные данные:

    ![LocalDB](img/12.png?raw=true)

    5.10.  Изменение созданных страниц в приложении ASP.NET Core

    Приложение для работы с фильмами подготовлено, но представление данных далеко от идеала. Вместо **ReleaseDate** должно стоять **Дата выпуска**, то есть два слова.

    Обновите `Models/Movie.cs` следующий выделенный код:

    ```csharp
    using System.ComponentModel.DataAnnotations;
    using System.ComponentModel.DataAnnotations.Schema;

    namespace RazorPagesApp.Models
    {
        public class Movie
        {
            public int Id { get; set; }
            public string? Title { get; set; }
            [Display(Name = "Дата выпуска")]
            [DataType(DataType.Date)]
            public DateTime ReleaseDate { get; set; }
            public string? Genre { get; set; }
            [Column(TypeName = "decimal(18, 2)")]
            public decimal Price { get; set; }
        }
    }
    ```

    В предыдущем коде:

    - Заметка к данным `[Column(TypeName = "decimal(18, 2)")]` позволяет `Entity Framework Core` корректно сопоставить **Price** с валютой в базе данных.
    - Атрибут `[Display]` указывает на отображаемое имя поля. В приведенном выше коде **"Дата выпуска"** вместо **ReleaseDate**.
    - Атрибут `[DataType]` указывает тип данных (Date). Сведения о времени, хранящиеся в поле, не отображаются.
    
    
    Перейдите к `Pages/Movies` и наведите указатель мыши на ссылку Edit (Изменение), чтобы просмотреть целевой URL-адрес.

    ![LocalDB](img/14.png?raw=true)

    Ссылки *Edit*, *Details* и *Delete* создаются вспомогательной функцией тегов привязки в файле `Pages/Movies/Index.cshtml`.

    ```html
    <td>
        <a asp-page="./Edit" asp-route-id="@item.Id">Edit</a> |
        <a asp-page="./Details" asp-route-id="@item.Id">Details</a> |
        <a asp-page="./Delete" asp-route-id="@item.Id">Delete</a>
    </td>
    ```

    Вспомогательные функции тегов позволяют серверному коду участвовать в создании и отображении HTML-элементов в файлах Razor.

    В приведенном выше коде вспомогательные функции привязки тегов динамически создают значения атрибута HTML `href` на основе Razor Page (маршрут является относительным), атрибут `asp-page` и идентификатор маршрута `asp-route-id`.

    Для проверки созданной разметки используйте в браузере параметр Просмотреть исходный код. Ниже показана часть созданного кода HTML:

    ```html
    <td>
        <a href="/Movies/Edit?id=1">Edit</a> |
        <a href="/Movies/Details?id=1">Details</a> |
        <a href="/Movies/Delete?id=1">Delete</a>
    </td>
    ```

    Динамически созданные ссылки передают идентификатор фильма строкой запроса. Например, `?id=1` в `https://localhost:5001/Movies/Details?id=1`.

    5.11. Добавление шаблона маршрута
    
    Обновите страницы Razor Pages Edit, Details и Delete так, чтобы использовался шаблон маршрута `{id:int}`. Измените директиву страницы для каждой из этих страниц c `@page` на `@page "{id:int}"`. Запустите приложение и просмотрите исходный код.

    Созданный код HTML добавляет идентификатор в путь URL-адреса:

    ```html
    <td>
    <a href="/Movies/Edit/1">Edit</a> |
    <a href="/Movies/Details/1">Details</a> |
    <a href="/Movies/Delete/1">Delete</a>
    </td>
    ```

    Запрос на страницу с шаблоном `{id:int}` маршрута, который не включает целое число, возвращает ошибку HTTP 404 (не найдена). Например, `https://localhost:5001/Movies/Details` возвращает ошибку 404. Чтобы сделать идентификатор необязательным, добавьте ? к ограничению маршрута:

    ```cshtml
    @page "{id:int?}"
    ```

    Чтобы проверить поведение `@page "{id:int?}"`:

    - Задайте директиву страницы в `Pages/Movies/Details.cshtml` как `@page "{id:int?}"`.
    - Установите точку останова в `public async Task<IActionResult> OnGetAsync(int? id)`, в `Pages/Movies/Details.cshtml.cs`.
    - Перейдите к https://localhost:5001/Movies/Details/.
  
    Из-за директивы `@page "{id:int}"` точка останова не достигается. Механизм маршрутизации возвращает ошибку HTTP 404. При использовании `@page "{id:int?}"` метод **OnGetAsync** возвращает `NotFound (HTTP 404)`:

    ```cs
    public async Task<IActionResult> OnGetAsync(int? id)
    {
        if (id == null)
        {
            return NotFound();
        }

        Movie = await _context.Movie.FirstOrDefaultAsync(m => m.ID == id);

        if (Movie == null)
        {
            return NotFound();
        }
        return Page();
    }
    ```

    5.12. Проверка обработки исключений нежесткой блокировки

    Просмотрите **OnPostAsync**  метод в файле `Pages/Movies/Edit.cshtml.cs`:

    ```cs
    public async Task<IActionResult> OnPostAsync()
    {
        if (!ModelState.IsValid)
        {
            return Page();
        }

        _context.Attach(Movie).State = EntityState.Modified;

        try
        {
            await _context.SaveChangesAsync();
        }
        catch (DbUpdateConcurrencyException)
        {
            if (!MovieExists(Movie.Id))
            {
                return NotFound();
            }
            else
            {
                throw;
            }
        }

        return RedirectToPage("./Index");
    }

    private bool MovieExists(int id)
    {
    return _context.Movie.Any(e => e.Id == id);
    }
    ```

    Код обнаруживает исключения параллелизма, когда один клиент удаляет фильм, а другой вносит изменения в фильм.

    Чтобы протестировать блок catch, выполните указанные ниже действия.

    - Задайте точку останова в catch (DbUpdateConcurrencyException).
    - Выберите команду Изменить у фильма, внесите изменения, но не вводите Сохранить.
    - В другом окне браузера щелкните ссылку Delete для этого же фильма, а затем удалите его.
    - В первом окне браузера опубликуйте изменения для фильма.

    Коду в рабочей среде может потребоваться обнаружение конфликтов параллелизма.

    5.13. Проверка публикации и привязки
    
    Просмотрите файл `Pages/Movies/Edit.cshtml.cs`.

    ```cs
    public class EditModel : PageModel
    {
        private readonly RazorPagesApp.Data.RazorPagesAppContext _context;

        public EditModel(RazorPagesApp.Data.RazorPagesAppContext context)
        {
            _context = context;
        }

        [BindProperty]
        public Movie Movie { get; set; } = default!;

        public async Task<IActionResult> OnGetAsync(int? id)
        {
            if (id == null || _context.Movie == null)
            {
                return NotFound();
            }

            var movie =  await _context.Movie.FirstOrDefaultAsync(m => m.Id == id);
            if (movie == null)
            {
                return NotFound();
            }
            Movie = movie;
            return Page();
        }

        // To protect from overposting attacks, enable the specific properties you want to bind to.
        // For more details, see https://aka.ms/RazorPagesCRUD.
        public async Task<IActionResult> OnPostAsync()
        {
            if (!ModelState.IsValid)
            {
                return Page();
            }

            _context.Attach(Movie).State = EntityState.Modified;

            try
            {
                await _context.SaveChangesAsync();
            }
            catch (DbUpdateConcurrencyException)
            {
                if (!MovieExists(Movie.Id))
                {
                    return NotFound();
                }
                else
                {
                    throw;
                }
            }

            return RedirectToPage("./Index");
        }

        private bool MovieExists(int id)
        {
        return (_context.Movie?.Any(e => e.Id == id)).GetValueOrDefault();
        }
    }
    ```

    При выполнении HTTP-запроса `GET` к странице `Movies/Edit`, например `https://localhost:5001/Movies/Edit/3`, происходит следующее:

    - Метод **OnGetAsync** извлекает запись фильма из базы данных и возвращает метод **Page**.
    - Метод **Page** отображает страницу `Pages/Movies/Edit.cshtml`. Файл `Pages/Movies/Edit.cshtml` содержит директиву `@model RazorPagesMovie.Pages.Movies.EditModel` модели, которая делает модель фильма доступной на странице.
    - Отображается форма **Edit** со значениями из записи фильма.

    При публикации страницы Movies/Edit происходит следующее:

    - Значения формы на странице привязываются к свойству Movie. Атрибут [BindProperty] обеспечивает привязку модели.

    ```csharp
    [BindProperty]
    public Movie Movie { get; set; }
    ```
    
    - При наличии ошибок в состоянии модели, например ReleaseDate невозможно преобразовать в дату, форма отображается повторно с предоставленными значениями.
    - Если ошибки модели отсутствуют, данные фильма сохраняются.

    Методы HTTP `GET` на страницах `Index`, `Create` и `Delete` работают аналогично. Метод HTTP `POST` **OnPostAsync** на странице `Create` работает аналогично методу **OnPostAsync** на странице `Edit`.

    5.14. Добавление поиска в Razor Pages в ASP.NET Core

    Добавим поиск фильмов по жанру или имени.

    Добавьте выделенный ниже код в `Pages/Movies/Index.cshtml.cs`:

    ```csharp
    public class IndexModel : PageModel
    {
        private readonly RazorPagesMovie.Data.RazorPagesMovieContext _context;

        public IndexModel(RazorPagesMovie.Data.RazorPagesMovieContext context)
        {
            _context = context;
        }

        public IList<Movie> Movie { get;set; }  = default!;

        [BindProperty(SupportsGet = true)]
        public string? SearchString { get; set; }

        public SelectList? Genres { get; set; }

        [BindProperty(SupportsGet = true)]
        public string? MovieGenre { get; set; }
    ```

    В предыдущем коде:

    - `SearchString`: содержит текстовые пользователи, вводимые в текстовое поле поиска. `SearchString` также имеет атрибут `[BindProperty]`. `[BindProperty]` связывает значения из формы и строки запроса с тем же именем, что и у свойства. `[BindProperty(SupportsGet = true)]` требуется для привязки в запросах HTTP GET.
    - `Genres`: содержит список жанров. `Genres` дает пользователю возможность выбрать жанр в списке. Для `SelectList` требуется `using Microsoft.AspNetCore.Mvc.Rendering;`.
    - `MovieGenre`: содержит определенный жанр, который выбирает пользователь. 

    Обновите метод **OnGetAsync** страницы `Index`, добавив следующий код:

    ```csharp
    public async Task OnGetAsync()
    {
        var movies = from m in _context.Movie
                    select m;
        if (!string.IsNullOrEmpty(SearchString))
        {
            movies = movies.Where(s => s.Title.Contains(SearchString));
        }

        Movie = await movies.ToListAsync();
    }
    ```

    В первой строке метода **OnGetAsync** создается запрос `LINQ` для выбора фильмов:

    ```csharp
    var movies = from m in _context.Movie
                select m;
    ```

    Этот запрос только ***определяется*** в этой точке и ***не выполняется*** для базы данных.

    **SearchString** Если свойство не null является или пусто, запрос фильмов изменяется для фильтрации в строке поиска:

    ```csharp
    if (!string.IsNullOrEmpty(SearchString))
    {
        movies = movies.Where(s => s.Title.Contains(SearchString));
    }
    ```

    Код `s => s.Title.Contains()` представляет собой лямбда-выражение. Лямбда-выражения используются в запросах `LINQ` на основе методов в качестве аргументов стандартных методов операторов запроса, таких как метод `Where` или `Contains`. Запросы `LINQ` не выполняются, если они определяются или изменяются путем вызова метода, например `Where`, `Contains` или `OrderBy`. Вместо этого выполнение запроса откладывается. Вычисление выражения откладывается до тех пор, пока не будет выполнена итерация его реализованного значения или не будет вызван метод `ToListAsync`. 
    
    > Метод **Contains** выполняется в базе данных, а не в коде C#. Регистр символов запроса учитывается в зависимости от параметров базы данных и сортировки. В **SQL Server** метод **Contains** сопоставляется с **SQL LIKE**, в котором регистр символов не учитывается. **SQLite** с параметрами сортировки по умолчанию — это смесь параметров с учетом регистра и параметров, которые ***НЕ*** учитывают регистр, в зависимости от запроса.

    Перейдите на страницу `Movies` и добавьте строку запроса, например `?searchString=Ghost`, к URL-адресу. Например, `https://localhost:5001/Movies?searchString=Ghost`. Отображаются отфильтрованные фильмы.

    ![search](img/15.png?raw=true)

    Если на страницу `Index` добавлен следующий шаблон маршрута, строку поиска можно передать в виде сегмента URL-адреса. Например, `https://localhost:5001/Movies/Ghost`.

    ```html
    @page "{searchString?}"
    ```

    Предыдущее ограничение маршрута разрешало поиск названия в виде данных маршрута (сегмент URL-адреса) вместо значения строки запроса. Символ ? в "{searchString?}" означает, что этот параметр является необязательным.

    ![search](img/16.png?raw=true)

    Среда выполнения ASP.NET Core использует привязку модели, чтобы присвоить значение свойства `SearchString` по строке запроса (`?searchString=Ghost`) или данным маршрута (`https://localhost:5001/Movies/Ghost`). Привязка модели не учитывает регистр символов.

    Однако пользователи не могут изменять URL-адрес для поиска фильма. На этом шаге добавляется пользовательский интерфейс для поиска фильмов. Если было добавлено ограничение маршрута "`{searchString?}`", удалите его.

    Откройте файл `Pages/Movies/Index.cshtml` и добавьте разметку, которая выделена в следующем коде:

    ```html
    @page
    @model RazorPagesApp.Pages.Movies.IndexModel

    @{
        ViewData["Title"] = "Index";
    }

    <h1>Index</h1>

    <p>
        <a asp-page="Create">Create New</a>
    </p>

    <form>
        <p>
            Title: <input type="text" asp-for="SearchString" />
            <input type="submit" value="Filter" />
        </p>
    </form>


    <table class="table">
    ```

    Тег HTML `<form>` при отправке формы  отправляет на страницу `Pages/Movies/Index` строку фильтра в строке запроса.

    Сохраните изменения и проверьте работу фильтра.

    ![search](img/17.png?raw=true)

    Для поиска по жанру обновите метод **OnGetAsync** страницы `Movies/Index.cshtml.cs`  следующим кодом:

    ```csharp
    public async Task OnGetAsync()
    {
        // Use LINQ to get list of genres.
        IQueryable<string> genreQuery = from m in _context.Movie
                                        orderby m.Genre
                                        select m.Genre;

        var movies = from m in _context.Movie
                    select m;

        if (!string.IsNullOrEmpty(SearchString))
        {
            movies = movies.Where(s => s.Title.Contains(SearchString));
        }

        if (!string.IsNullOrEmpty(MovieGenre))
        {
            movies = movies.Where(x => x.Genre == MovieGenre);
        }
        Genres = new SelectList(await genreQuery.Distinct().ToListAsync());
        Movie = await movies.ToListAsync();
    }    
    ```

    Следующий код определяет запрос LINQ, который извлекает все жанры из базы данных.

    ```csharp
    IQueryable<string> genreQuery = from m in _context.Movie
                                    orderby m.Genre
                                    select m.Genre;
    ```

    Список жанров SelectList создается путем проецирования отдельных жанров.

    ```csharp
    Genres = new SelectList(await genreQuery.Distinct().ToListAsync()); 
    ```

    Обновите `Index.cshtml` элемент `<form>`, как показано в следующей разметке:

    ```html
    @page
    @model RazorPagesMovie.Pages.Movies.IndexModel

    @{
        ViewData["Title"] = "Index";
    }

    <h1>Index</h1>

    <p>
        <a asp-page="Create">Create New</a>
    </p>

    <form>
        <p>
            <select asp-for="MovieGenre" asp-items="Model.Genres">
                <option value="">All</option>
            </select>
            Title: <input type="text" asp-for="SearchString" />
            <input type="submit" value="Filter" />
        </p>
    </form>
    ```

    Проверьте работу приложения, выполнив поиск по жанру, по названию фильма и по обоим этим параметрам.

    ## 5.15 Добавление свойства Rating в модель Movie

    Entity Framework Code First Migrations используется для выполнения следующих задач:

    - Добавление нового поля в модель.
    - Перенос изменений в схеме нового поля в базу данных.

    Если вы используете EF Code First для автоматического создания и отслеживания базы данных, Code First:

    - Добавляет в базу данных таблицу __EFMigrationsHistory, которая позволяет отслеживать синхронизацию схемы базы данных с классами модели, на основе которой она была создана.
    - Если классы модели не синхронизированы с базой данных, выдает исключение.

    Автоматическая проверка синхронизации схемы и модели упрощает поиск несогласованных проблем в коде базы данных.

    1. Откройте файл `Models/Movie.cs` и добавьте свойство **Rating**:
   
    ```csharp
    public class Movie
    {
        public int Id { get; set; }
        public string? Title { get; set; }
        [Display(Name = "Дата выпуска")]
        [DataType(DataType.Date)]
        public DateTime ReleaseDate { get; set; }
        public string? Genre { get; set; }
        [Column(TypeName = "decimal(18, 2)")]
        public decimal Price { get; set; }
        public string Rating { get; set; } = string.Empty;
    }
    ```


    2. Отредактируйте `Pages/Movies/Index.cshtml` и добавьте поле **Rating**:

    ```html
    <form>
        <p>
            <select asp-for="MovieGenre" asp-items="Model.Genres">
                <option value="">All</option>
            </select>
            Title: <input type="text" asp-for="SearchString" />
            <input type="submit" value="Filter" />
        </p>
    </form>


    <table class="table">
        <thead>
            <tr>
                <th>
                    @Html.DisplayNameFor(model => model.Movie[0].Title)
                </th>
                <th>
                    @Html.DisplayNameFor(model => model.Movie[0].ReleaseDate)
                </th>
                <th>
                    @Html.DisplayNameFor(model => model.Movie[0].Genre)
                </th>
                <th>
                    @Html.DisplayNameFor(model => model.Movie[0].Price)
                </th>
                <th>
                    @Html.DisplayNameFor(model => model.Movie[0].Rating)
                </th>
                <th></th>
            </tr>
        </thead>    
    ```

    3.  Обновите следующие страницы, добавив поле Rating:
        - Pages/Movies/Create.cshtml.
        - Pages/Movies/Delete.cshtml.
        - Pages/Movies/Details.cshtml.
        - Pages/Movies/Edit.cshtml.

    Для работы приложения необходимо обновить базу данных, включив в нее новое поле. При запуске приложения без обновления базы данных возникает **SqlException**:

    ```
    SqlException: Invalid column name 'Rating'.
    ```

    Исключение **SqlException** связано с тем, что обновленный класс модели **Movie** отличается от схемы таблицы **Movie** в базе данных. В таблице базы данных нет столбца **Rating**.

    4. Обновите класс **SeedData** так, чтобы он предоставлял значение нового столбца. Ниже приведен пример изменения, которое необходимо реализовать для каждого блока `new Movie`:

    ```csharp
    context.Movie.AddRange(
        new Movie
        {
            Title = "When Harry Met Sally",
            ReleaseDate = DateTime.Parse("1989-2-12"),
            Genre = "Romantic Comedy",
            Price = 7.99M,
            Rating = "R"
        },
    ```

    5. В терминале последовательно выполните следующие команды:
   
    ```dotnetcli
    dotnet build
    dotnet ef migrations add rating
    dotnet ef database update
    ```

    Команда `dotnet-ef migrations add rating` задает следующие инструкции для платформы:

    - Сравнивает модель **Movie** со схемой базы данных **Movie**.
    - Создает код для переноса схемы базы данных в новую модель.
    
    В качестве имени файла переноса используется произвольное имя rating. Рекомендуется присваивать этому файлу понятное имя.

    Команда `dotnet-ef database update` указывает платформе, что к базе данных нужно применить изменения схемы, а также сохранить существующие данные.

    Если удалить все записи из базы данных, при инициализации она будет заполнена начальными значениями и в нее будет включено поле **Rating**.

    6. Запустите приложение и проверьте возможность создания, редактирования и отображения фильмов с использованием поля **Rating**. Если база данных не заполнена начальными значениями, задайте точку останова в методе `SeedData.Initialize`.

    # 5.16. Добавление правил проверки к модели фильма

    Пространство имен `System.ComponentModel.DataAnnotations` предоставляет:

    - Набор встроенных атрибутов проверки, которые декларативно применяются к классу или свойству.
    - Атрибуты форматирования (такие как `[DataType]`), которые обеспечивают форматирование и не предназначены для проверки.
    - Обновите класс **Movie**, чтобы использовать преимущества встроенных атрибутов проверки `[Required]`, `[StringLength]`, `[RegularExpression]` и `[Range]`.

    ```csharp
    public class Movie
    {
        public int Id { get; set; }
        [StringLength(60, MinimumLength = 3)]
        [Required]
        public string? Title { get; set; }
        [Display(Name = "Дата выпуска")]
        [DataType(DataType.Date)]
        public DateTime ReleaseDate { get; set; }
        [RegularExpression(@"^[A-Z]+[a-zA-Z\s]*$")]
        [Required]
        [StringLength(30)]
        public string? Genre { get; set; }
        [Range(1, 100)]
        [DataType(DataType.Currency)]
        [Column(TypeName = "decimal(18, 2)")]
        public decimal Price { get; set; }
        [RegularExpression(@"^[A-Z]+[a-zA-Z0-9""'\s-]*$")]
        [StringLength(5)]
        [Required]
        public string Rating { get; set; } = string.Empty;
    }
    ```

    Атрибуты проверки определяют поведение для свойств модели, к которым они применяются:

    - Атрибуты `[Required]` и `[MinimumLength]` означают, что свойство должно иметь значение. Пользователь может свободно вводить пробелы для выполнения этой проверки.

    - Атрибут `[RegularExpression]` ограничивает набор допустимых для ввода символов. В приведенном выше коде в Genre:

        - должны использоваться только буквы;
        - первая буква должна быть прописной. Пробелы разрешены, в то время как числа и специальные символы не допускаются.
    - `RegularExpressionRating`:

        - первый символ должен быть прописной буквой;
        - допускаются специальные символы и цифры, а также последующие пробелы. значение "PG-13" допустимо для рейтинга, но недопустимо для Genre;
    - Атрибут `[Range]` ограничивает значения указанным диапазоном.

    - Атрибут `[StringLength]` может задавать максимальную и, при необходимости, минимальную длину строкового свойства.

    Типы значений (например, `decimal`, `int`, `float`, `DateTime`) по своей природе являются обязательными и не требуют атрибута `[Required]`.

    Указанные выше правила проверки используются для демонстрации, они не являются оптимальными для рабочей системы. Например, предыдущее исключение не позволяет ввести модель **Movie** с двумя символами и не допускает специальные знаки в **Genre**.

    Наличие правил проверки, которые автоматически применяются ASP.NET Core, помогает:

    - сделать приложение более надежным;
    - сократить возможность сохранения недопустимых данных в базе данных.

    Запустите приложение и перейдите в раздел "Pages/Movies".

    Щелкните ссылку **Create New** (**Создать**). Введите в форму какие-либо недопустимые значения. Если функция проверки `jQuery` на стороне клиента обнаруживает ошибку, сведения о ней отображаются в соответствующем сообщении.

    ![search](img/18.png?raw=true)

    Обратите внимание, что для каждого поля, содержащего недопустимое значение, в форме автоматически отображается сообщение об ошибке проверки. Эти ошибки применяются как на стороне клиента (с помощью `JavaScript` и `jQuery`), так и на стороне сервера (если пользователь отключает `JavaScript`).

    Основным преимуществом является то, что на страницах создания или редактирования не требуется изменять код. Пользовательский интерфейс проверки активируется после применения к модели атрибутов проверки достоверности. В Razor Pages, создаваемом в рамках этого руководства, правила проверки применяются автоматически (для этого к свойствам класса модели Movie применяются атрибуты проверки). При проверке страницы редактирования применяются те же правила.

    Данные формы передаются на сервер только после того, как будут устранены все ошибки проверки на стороне клиента. Чтобы убедиться, что данные формы не отправляются, используйте любой из следующих способов.

    Поместите точку останова в метод **OnPostAsync**. Отправьте форму, выбрав **Создать** или **Сохранить**. Точка останова не достигается ни при каких обстоятельствах.

    **DataAnnotation**, примененные к классу, изменяют схему. Например, **DataAnnotation**, примеренные к полю Title, выполняют следующее:

    ```csharp
        [StringLength(60, MinimumLength = 3)]
        [Required]
        public string Title { get; set; } = string.Empty;
    ```
        - ограничивают число символов до 60;
        - не допускают значение null.
        
    Сейчас таблица Movie имеет следующую схему:

    ```SQL
        CREATE TABLE [dbo].[Movie] (
            [ID]          INT             IDENTITY (1, 1) NOT NULL,
            [Title]       NVARCHAR (MAX)  NULL,
            [ReleaseDate] DATETIME2 (7)   NOT NULL,
            [Genre]       NVARCHAR (MAX)  NULL,
            [Price]       DECIMAL (18, 2) NOT NULL,
            [Rating]      NVARCHAR (MAX)  NULL,
            CONSTRAINT [PK_Movie] PRIMARY KEY CLUSTERED ([ID] ASC)
        );
    ``` 
    Предыдущие изменения схемы не приводят к созданию исключения EF. Но следует создать миграцию, чтобы схема соответствовала модели.

    ```dotnetcli
    dotnet build
    dotnet ef migrations add New_DataAnnotations
    dotnet ef database update
    ```

    Изучите метод Up:

    ```csharp
    public partial class New_DataAnnotations : Migration
    {
        /// <inheritdoc />
        protected override void Up(MigrationBuilder migrationBuilder)
        {
            migrationBuilder.AlterColumn<string>(
                name: "Title",
                table: "Movie",
                type: "nvarchar(60)",
                maxLength: 60,
                nullable: false,
                oldClrType: typeof(string),
                oldType: "nvarchar(max)");

            migrationBuilder.AlterColumn<string>(
                name: "Rating",
                table: "Movie",
                type: "nvarchar(5)",
                maxLength: 5,
                nullable: false,
                oldClrType: typeof(string),
                oldType: "nvarchar(max)");

            migrationBuilder.AlterColumn<string>(
                name: "Genre",
                table: "Movie",
                type: "nvarchar(30)",
                maxLength: 30,
                nullable: false,
                oldClrType: typeof(string),
                oldType: "nvarchar(max)");
        }
    ```

    Обновленная таблица Movie имеет следующую схему:

    ```SQL
    CREATE TABLE [dbo].[Movie] (
        [ID]          INT             IDENTITY (1, 1) NOT NULL,
        [Title]       NVARCHAR (60)   NOT NULL,
        [ReleaseDate] DATETIME2 (7)   NOT NULL,
        [Genre]       NVARCHAR (30)   NOT NULL,
        [Price]       DECIMAL (18, 2) NOT NULL,
        [Rating]      NVARCHAR (5)    NOT NULL,
        CONSTRAINT [PK_Movie] PRIMARY KEY CLUSTERED ([ID] ASC)
    );
    ```

    ## Задание:

    С использованием полученных знаний составить сайт, реализующий базу данных:

    1. Классы – человек (имя, дата рождения), абитуриент (количество баллов), студент (курс, группа, факультет), преподаватель (должность, кафедра).
    Запросы – имена студентов указанного курса, имена и должность преподавателей указанной кафедры.

    2. Классы –растение (название, вид), дерево (возраст), цветок (длина стебля), роза (цвет).
    Запросы – все чайные розы с длиной стебля большей, чем задал пользователь, количество роз заданного цвета.

    3. Классы – кадры (имя), рабочий (специальность, цех), инженер (квалификация, подразделение), администрация (должность).
    Запросы – имена рабочих заданного цеха, количество инженеров в заданном подразделении.

    4. Классы – ВУЗ (адрес), факультет (название), группа (номер,староста, курс), подгруппа (номер, количество студентов).
    Запросы – количество групп заданного курса, старост всех групп опредленного факультета.

    5. Классы – печатное издание (издательство, год, название), журнал (номер, месяц), книга (тематика, автор, количество страниц), учебник (назначение)
    Запросы – наименования всех книг в библиотеке (магазине), вышедших не ранее указанного года; суммарное количество учебников в библиотеке (магазине).

    6. Классы –млекопитающие (год), парнокопытные (среда обитания), птицы (хищники), животное (вид, род, вес).
    Запросы – средний вес животных заданного вида в зоопарке, количество хищных птиц.

    7. Классы – место (площадь, название), область (количество населенных пунктов, руководство), город (область, количество жителей, мэр), деревня (район).
    Запросы – названия всех городов заданной области, суммарное количество жителей всех городов в области.

    8. Классы – товар (название), радиотовары (назначение), продукт (отдел), молочный продукт (разновидность, дата изготовления), транзистор (тип, номер).
    Запросы – наименования всех товаров в заданном отделе магазина, суммарная стоимость товара заданного наименования.
    
    9. Классы – автомобиль (марка, номер), поезд (номер, количество вагонов, количество пассажиров в вагоне), транспортное средство (средняя скорость, вид топлива, год выпуска).
    Запросы – количество указанных транспортных средств в автопарке (на автостоянке), количество мест во всех вагонах поездов.

    10. Классы – республика (вид, правительство), монархия (вид, имя монарха), королевство (король), государство (название, денежная единица, символика).
    Запросы – имена всех монархов на заданном континенте, количество демократических государств.



# Часть II. SignalR на примере разработки чата






<!-- 6.    -->


<!-- 

# Разработка приложения MVC

# Разработка веб-интерфейса на стороне клиента

# RESTful HTTP-сервисы

# Приложение реального времени  -->