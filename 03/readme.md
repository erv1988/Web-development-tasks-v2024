# Способы разметки страницы

## 1. CSS разметка

# `01` Relative и Absolute позиционирование

Используя:

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8" />
		<meta name="viewport" content="width=device-width" />
		<title>4Geeks Academy</title>
		<link rel="stylesheet" href="styles.css" />
	</head>
	<body>
		<div id="firstDiv"></div>
		<div id="secondDiv" class="relativePositionExample"></div>
		<h2>This will be a secondary content</h2>
	</body>
</html>
```

и 

```css
body {
  background: gray;
}
#firstDiv {
  background: blue;
  width: 100px;
  height: 100px;
}
#secondDiv {
  background: yellow;
  width: 100px;
  height: 100px;
}
.absolutePositionExample {
  position: absolute;
  top: 20px;
  left: 20px;
}
.relativePositionExample {
  position: relative;
  top: 20px;
  left: 20px;
}
```

Обратим внимание на:

1. Оба `<div>` тега - фактически контейнеры.

2. Примените класс `.absolutePositionExample` к `#secondDiv` сравните результат.

3. Примените класс `.relativePositionExample` к `#secondDiv` сравните результат.

Ask yourself:

Позиция `relative` задается относительно начальной позиции элемента, при `absolute` начальная позиция полностью игнорируется.


# `02` Текст перед изображением

`z-index` является аналогом функции «На передний план» MS Office.

Элементы с большим значением `z-index` впереди элементов с меньшим значением `z-index`.

## Упражнение:

Используя `z-index` поместите текст перед изображением.


# `03` Float 

`float` позиционирует элемент (левее или правее).

Используя `float` расположите элементы следующим образом:

![float example](img/03.png?raw=true)

### Ещё:

Можно использовать `margin-right` для управления расстоянием между текстом и изображением.


# `04` Центрирование

Очень хорошая практика — помещать все содержимое вашего веб-сайта в один большой контейнер.

Поместите это содержимое в рамку с помощью `400px`, `width` а затем отцентрируйте ее по горизонтали.

## Упражнение:

1. Создайте `div` с классом `"myDiv"`
2. Используя CSS установите `div`-у ширину `400px`
3. Центрируйте `div` горизонтально относительно тега `body` 

## Ожидаемый результат:

![Center content](img/04.png?raw=true)

# `05` Боковая панель

Чтобы сделать боковую панель, все, что вам нужно сделать, это разместить 2 поля в одной строке, используя `flex` свойство, обернув их родительским элементом `div`.


## Упражнение:

Используя каркас

```html
<div id="wrapper">
			<div id="sidebar">This is my sidebar.</div>
			<div id="content">
				This is my content, This is my content, This is my content, This is my content, This is my content, This is my content, This is my
				content,
			</div>
		</div>
```
 
Создайте левую боковую панель и основной контент:

![Sidebar](img/05.png?raw=true)

1. Оболочка должна иметь высоту `100px` и ширину `100%`
2. Боковая панель долдна иметь ширину `30%`
3. Основной блок должен иметь ширину `70%`

Попробуйте изменять дизайн только за счет CSS.

# `06` Деление экрана на 3

## Упражнение:

Используйте каркас:

```html
<div id="wrapper">
    <div id="sectionA">A</div>
    <div id="sectionB">B</div>
    <div id="sectionC">C</div>
</div>
```

Используя `display: flex` разделите страницу на 3 верикальных столбца равной ширины.

+ Три контейнера должны встать на одну линию.

+ Используйте ширину 33%. 

+ Закрывающий тег любого из трех разделов должен находиться рядом с открывающим тегом следующего одноуровневого раздела; в противном случае браузер добавит небольшое разделение между ними.

# `07` Дизайним

Надо сделать страницу с указанным макетом:

![beautify](img/07.png?raw=true)

Используя знания о размещении элементов по вертикали и горизонатли сделйте сайт с указанным макетом. Содержимое можно использовать любое (покажите все на что способны).Для контроля разметки используйте цветовую схему с макета. 

Не забывайте про открывающий/закрывающий тег и пространство между ними.

+ Для начала, попробуйте именовать теги так: `div1`, `div2`, `div3`, `div4`, ..., `div6` .

# `08` Статическая разметка 

Используя необходимые класса `.wrapper`,`.secondWrapper`, `<header>`, `<nav>` и `<section>` постройте макет для страниц по приведенной нормальной схеме.

```html
<body>
    <div class="wrapper">
        <h1>Static Layout Example</h1>
        <header>HEADER</header>
        <div class="secondWrapper">
            <nav>NAV</nav>
            <section>SECTION</section>
        </div>
    </div>
</body>
```

+ `.secondWrapper` должен быть `flex` контейнером. Используйте `display: flex` для этого.

+ Не изменяйте каркас html.

+ Контейнер `section` примерно имеет ширину `80%`.

+ Между контейнерами отступы `10px`.

## Ожидаемый результат:

![Static Layout](img/08.png?raw=true)


## 2. Bootstrap

# `01` Add Bootstrap To Your Website

Существует два способа добавить Bootstrap на ваш веб-сайт: 
**Удаленный** or **Локальный** (как и любой другой файл CSS). Единственная разница будет заключаться в URL-пути, который вы указываете в `<link>` теге (для файлов .CSS Bootstrap) или `<script>` теге (для файлов .JS Bootstrap). файлы).

+ от как вы выполняете **удаленный** импорт CSS Bootstrap:

```html
<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-EVSTQN3/azprG1Anm3QDgpJLIm9Nao0Yz1ztcQTwFspd3yD65VohhpuuCOmLASjC" crossorigin="anonymous">
```


+ Вот как вы добавляете загрузочную загрузку из **локального** файла (то есть на вашем рабочем месте):

```html
<link href="path/to/your/file" rel="stylesheet">
```

### К сведению:

Рекомендуется убедиться, что ваш файл существует по этому URL-адресу. Вы можете проверить это, открыв новую вкладку браузера и вставив путь в URL-адрес браузера (вы увидите содержимое файла на своем экране).

Bootstrap состоит из двух файлов: таблицы стилей `CSS` и исходного кода `JavaScript`.

Таблица стилей CSS Bootstrap `<link>` вставляется в `<head>` тег перед любыми другими таблицами стилей CSS.

Теги исходного кода JavaScript `<script>` вставляются непосредственно перед закрывающим `</body>` тегом..

> Больше информации: https://getbootstrap.com/docs/5.0/getting-started/introduction/


## Задание:

1. Добавьте эти ссылки в свой файл для успешного импорта Bootstrap:

+ Таблица стилей Bootstrap CSS:

```html
<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-EVSTQN3/azprG1Anm3QDgpJLIm9Nao0Yz1ztcQTwFspd3yD65VohhpuuCOmLASjC" crossorigin="anonymous">
```


+ Исходный код JavaScript:

```html
<script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.9.2/dist/umd/popper.min.js" integrity="sha384-IQsoLXl5PILFhosVNubq5LC7Qb9DXgDA9i+tQ8Zj3iwWAwPtgFTxbJ8NT4GN1R8p" crossorigin="anonymous"></script>
<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/js/bootstrap.min.js" integrity="sha384-cVKIPhGWiC2Al4u+LWgxfKTRIcfu0JTxR+EQDz/bgldoEyl4H0zUF0QKbrJ0EcQF" crossorigin="anonymous"></script>
```

Каркас:

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8" />
		<meta name="viewport" content="width=device-width" />
		<!-- Your Bootstrap Link should always be before the CSS link -->
		
		<title>01 Add Bootstrap To Your Website</title>
	</head>
	<body>
		<button type="button" class="btn btn-danger">This should be a red button</button>
		<!-- Your Bootstrap Scripts should always be before the </body> closing tag -->
		
	</body>
</html>
```

+ Кнопка должна быть красной.


# `02` Bootstrap каркас

При использовании Bootstrap вам необходимо поместить весь свой контент в следующие классы -**контейнеры** :

```html
<div class="container"></div>
```
или

```html
<div class="container-fluid"></div>
```


## Задание:

С использованием каркаса выполните задание:

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8" />
		<meta name="viewport" content="width=device-width" />
		<!-- Your Bootstrap Link should always be before the CSS link -->
		
		<title>02 Bootstrap Skeleton</title>
	</head>
	<body>

		<h1>This is my first example using bootstrap</h1>
		<p>I can't believe that bootstrap is so easy, now HTML and CSS are a simple but very useful technology.</p>

		<!-- Bootstrap JS files DON'T REMOVE THESE FILES -->
		<script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.9.2/dist/umd/popper.min.js" integrity="sha384-IQsoLXl5PILFhosVNubq5LC7Qb9DXgDA9i+tQ8Zj3iwWAwPtgFTxbJ8NT4GN1R8p" crossorigin="anonymous"></script>
		<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/js/bootstrap.min.js" integrity="sha384-cVKIPhGWiC2Al4u+LWgxfKTRIcfu0JTxR+EQDz/bgldoEyl4H0zUF0QKbrJ0EcQF" crossorigin="anonymous"></script>
	</body>
</html>
```

1. Свяжите таблицу стилей Bootstrap `CSS` с документом, используя `<link>` тег.

2. Оберните содержимое веб-сайта с `<div>` помощью `container` и `bg-secondary` классов. 

3. **Создайте** и **просмотрите** упражнение, чтобы сравнить различия.

4. Теперь измените класс `<div>` только что созданного объекта на `container-fluid` и `bg-secondary` классы.

5. **Создайте** и **просмотрите** упражнение, чтобы сравнить различия.


## Важно:

Чтобы понять разницу между обоими containerклассами, вам придется `<div>` уменьшать и увеличивать контейнер. Есть `margin-left: auto` и `margin-right: auto` центрирование контейнера; тогда как содержимое класса `container-fluid` охватывает всю ширину страницы.


# `03` Bootstrap Grid

Теперь поговорим о сетке — как вы знаете, каждая строка имеет `12` ячеек , занимающих примерно `8,33%` ширины сайта, столбец может занимать от **1 до 12 ячеек ширины** , а все в пределах одной строки не может в сумме составлять более **12 слотов**.

![Static Layout](img/CSS-GRID-3.png?raw=true)

В Bootstrap 5 вам просто нужно добавить `.col` класс, и он автоматически равномерно распределит столбцы по **12** слотам в строке.

Если вы хотите, чтобы столбец занимал определенное количество слотов, вы должны указать это в `class` свойстве объекта `<div>`, содержащего столбец.

Например:

```html
<div class="col-2">.col-2</div>
<div class="col-4">.col-4</div>
<div class="col-6">.col-6</div>
```

В Bootstrap 5 `justify-content` к классам добавлено свойство перемещать столбцы в нужное положение.

> Дополнительная информация о сетке: https://getbootstrap.com/docs/5.0/layout/grid/


## Задание:

Используя каркас выполнить задание:

```html
<body>
		<div class="container">
			<h1>Let's test the grid baby!</h1>
			<div class="row">
				<div class="col-6">First col</div>
				<div class="col-6">Second col</div>
			</div>
			<div class="row">
				<div>Third col</div>
				<div>Fourth col</div>
			</div>
		</div>
	</body>
```

1. Сделайте так, чтобы во второй строке было 3 одинаковых столбца `width` (разделите строку на 3).

2. Добавьте третью строку только с одним столбцом из 12 слотов.

3. Измените номер `background-color` только что созданной строки на redи добавьте свое имя внутри файла `<div>`.

4. Измените класс main `<div>` с `container` на `container-fluid`.


## Подсказки:

+ Задайте свойства класса каждого столбца и укажите, сколько слотов должен занимать каждый столбец.

+ Проверьте документацию Bootstrap, чтобы изменить цвет фона на красный.


## Ожидаемый результат:

![Example Image](img/09.png?raw=true)

# `04` Навигационная панель

Меню, в целом, одинаково для всех проектов: используем `ul` теги, удаляем маркеры из списка `li`, отображаем список в строке и т. д.

Bootstrap нам очень помогает, представляя класс `nav`, который может вести себя несколькими способами.

В данном случае у нас есть стандартное меню, `ul` необходимое для создания меню, но без применения каких-либо стилей CSS.

> Дополнительная информация о навигации: https://getbootstrap.com/docs/5.0/components/navs-tabs/


## Задание:

Используя каркас, выполнить задания

```html
<html>
    <head>
        <meta charset="utf-8" />
        <meta name="viewport" content="width=device-width" />
        <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-EVSTQN3/azprG1Anm3QDgpJLIm9Nao0Yz1ztcQTwFspd3yD65VohhpuuCOmLASjC" crossorigin="anonymous">
        <title>04 Navbar</title>
    </head>
    <body>
        <ul>
            <li>
                <a href="#">Home</a>
            </li>
            <li>
                <a href="#">Profile</a>
            </li>
            <li>
                <a href="#">Messages</a>
            </li>
        </ul>
    </body>
</html>
```

1. **Создайте** и затем **просмотрите** упражнение.

2. Примените классы к коду, как в этом примере: https://getbootstrap.com/docs/5.0/components/navs-tabs/#base-nav

3. **Создайте**, а затем снова **просмотрите**, чтобы сравнить различия.

4. Теперь добавьте `nav-tabs` класс туда же `ul` (не удаляя навигацию по классам) и сравните результаты.

# `05` Боковая панель с меню

## Задание:

1. Повторите этот точный дизайн:

![Example Image](img/10.png?raw=true)

2. Первый столбец должен быть a `col-2`, а второй — `col-10`.

3. Заголовок второго столбца должен быть расширением `<h4>`.

## Подсказки:

+ Создайте строку с двумя столбцами. В столбце слева должно быть боковое меню.

+ Не забудьте цвет фона второго столбца (он очень светло-серый).

## К сведению:

Проверьте эту документацию:

- https://getbootstrap.com/docs/5.0/components/navs-tabs/#vertical
- https://getbootstrap.com/docs/5.0/layout/grid/
- https://getbootstrap.com/docs/5.0/components/buttons/
- https://getbootstrap.com/docs/5.0/utilities/spacing/
- https://getbootstrap.com/docs/5.0/utilities/background/

# `06` Трехколоночный дизайн

## Задания:

1. Воссоздайте этот точный HTML с помощью Bootstrap (вам вообще не нужен CSS):

![Example Image](img/11.png?raw=true)

## Подсказки:

- Используйте 1 основной контейнер с 2 рядами. Первая строка содержит `<h1>`, `<p>` и `<button>`, а вторая строка содержит `3` столбца.

- Во второй строке каждый столбец содержит `<h2>`, `<p>` и `<button>`.

## К сведению:

Проверьте эту документацию:

- https://getbootstrap.com/docs/5.0/layout/grid/
- https://getbootstrap.com/docs/5.0/utilities/spacing/

# `07` Кнопки, оповещения и таблица

Якорь, кнопка, оповещение, вспомогательные классы Bootstrap и другие элементы Bootstrap могут иметь 7 различных стилей (цветов):

![Example Image](img/12.png?raw=true)

Это не только эстетика: каждый стиль призван служить определенной цели на вашем веб-сайте в зависимости от контекста.

## Задания:

1. Воссоздайте этот точный HTML с помощью Bootstrap: 

- Кнопки.
- Предупреждение.
- Таблица `table`.
- И, конечно же, строки и столбцы для макета.
+ НИКАКОГО `CSS`!
  
![Example Image](img/13.png?raw=true)

## Проверьте эту документацию:

- https://getbootstrap.com/docs/5.0/components/buttons/
- https://getbootstrap.com/docs/5.0/components/alerts/
- https://getbootstrap.com/docs/5.0/content/tables/#striped-rows


# `08` Bootstrap формы

## Задание:

1. Используйте стили формы Bootstrap, чтобы воссоздать точно такую ​​же форму входа:

![Example Image](img/14.png?raw=true)

2. Форма должна иметь темно-серый цвет фона.

3. Форма должна иметь закругленные границы.

4. Заголовок должен быть в формате `<h2>`.

5. Ввод электронной почты должен иметь расширение `type="email"`.

6. Ввод пароля должен иметь `type="password"`.

7. Ввод флажка должен иметь `type="checkbox"`.

8. Кнопка должна иметь ширину 100%.

9. НИКАКОГО `CSS`!

## Проверьте эту документацию:

- Forms: https://getbootstrap.com/docs/5.0/forms/form-control/

- Buttons: https://getbootstrap.com/docs/5.0/components/buttons/#examples


# `09` CSS Flexbox

CSS Flexbox — это технология для создания сложных гибких макетов за счёт правильного размещения элементов на странице. В целом, ничего нового. Изучите материал и повторите дизайн `05` и `06` с использованием `flexbox`.

## Проверьте эту документацию:

- Как работает CSS Flexbox: https://tproger.ru/translations/how-css-flexbox-works

- Основные понятия Flexbox: https://developer.mozilla.org/ru/docs/Web/CSS/CSS_flexible_box_layout/Basic_concepts_of_flexbox

- Песочница: https://tpverstak.ru/flex-cheatsheet/
