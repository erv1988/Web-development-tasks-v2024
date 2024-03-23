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