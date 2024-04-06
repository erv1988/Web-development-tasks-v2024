# Работа с фреймворком React

# `01` Начало

Сегодня самая большая проблема для фронтенд-разработчиков — это **работа с DOM для создания динамического HTML**, и `React.js` справляется с этим лучше всего.

`React.js` — это библиотека рендеринга, созданная для оптимизации DOM: разработчики экономят время, а браузер работает быстрее.

Библиотека поставляется с функцией `ReactDOM.render`, которую можно рассматривать как замену классическому свойству [InnerHTML](https://www.w3schools.com/jsref/prop_html_innerhtml.asp) .

Функция `ReactDOM.render` получает два параметра:

+  Что отображать (внутренний HTML).

+  Где его визуализировать (элемент DOM).

Например:

```jsx
import React from 'react'; // импорт библиотеки
import ReactDOM from 'react-dom'; // импорт react-dom для генерации html

// ЧТО: переменная содержит HTML, который необходимо рендерить
let output = <span>James is 12 years old</span>

// ГДЕ: DOM-элемент, который будет содержать сгенерированный HTML
const myDiv = document.querySelector('#myDiv');

               //что   //где
ReactDOM.render(output, myDiv);
```

Функция  `ReactDOM.render` установит для внутреннего HTML `myDiv` (элемента DOM) значение, `output` содержащееся в переменной. Функционал очень похож  `innerHTML` :

```jsx
// Способ сделать без React
myDiv.innerHTML = '<span>James is 12 years old</span>';

// Способ через React
ReactDOM.render(<span> James is 12 years old </span>, myDiv);
```

## Задание:

1. Изучите файл `app.jsx` и потратьте некоторое время, чтобы понять его:

```jsx
import React from 'react'; // импорт библиотеки
import ReactDOM from 'react-dom'; // импорт react-dom для генерации html

// ЧТО: переменная содержит HTML, который необходимо рендерить
let output = <span>James is 12 years old</span>

// ГДЕ: DOM-элемент, который будет содержать сгенерированный HTML
const myDiv = document.querySelector('#myDiv');

               //что   //где
ReactDOM.render(output, myDiv);
```

2. Измените переменную `output` на:

```jsx
<span>James is <strong>12</strong> years old</span>
```

JSX также позволяет легко включать переменные в HTML. Например, предположим, что у вас есть следующая переменная:

```js
let age = 12;
```

Если вы хотите динамически включить значение этой переменной в свой HTML-код, вы можете сделать это следующим образом:

```jsx
let output = <span> James is { age } years old </span>
```

Обратите внимание на положение фигурных скобок `{` и `}` перенос переменной.

Затем мы можем визуализировать все содержимое веб-сайта, используя `ReactDOM.render` следующее:

```jsx
// импорт react-dom для генерации html
import ReactDOM from 'react-dom';
               //ЧТО                //где: через вызов функции #myDiv
ReactDOM.render(output,             document.querySelector('#myDiv'));
```

Итоговый HTML-документ веб-сайта будет выглядеть следующим образом:

```html
<div id="myDiv">
    <span>James is 12 years old</span>
</div>
```

По сути, теперь мы можем смешивать HTML и JS в одном файле без необходимости объединения и использования строк.

В файле app.jsx есть переменная, `name` которая может содержать имя.

app.jsx:

```jsx
import React from "react";
import ReactDOM from "react-dom";

// Переменные
let age = "12";
let name = "John";

// Применение переменных
let output = <span>James is {age} years old</span>;

// отрисовка
ReactDOM.render(output, document.querySelector("#myDiv"));
```

## Задание:

1. Создайте переменную внутри `output` переменной. Замените жестко запрограммированное слово `James` переменной `name`(помните о фигурных скобках `{}`).

# `02` Рендер объектов

Теперь давайте воспользуемся более сложной переменной для визуализации нашего HTML. Допустим, у нас есть следующий объект JS, содержащий информацию о клиенте:

```js
const customer = {
    first_name: 'Bob',
    last_name: 'Dylan'
};
```

Чтобы получить какое-либо свойство объекта, `customer` нам нужно использовать `.` оператор точки, например:

```js
console.log(customer.first_name); 
```

## 📝 Instructions:

Откройте `app.jsx`

```jsx
import React from "react";
import ReactDOM from "react-dom";

const customer = {
	first_name: "Bob",
	last_name: "Dylan"
};

//              Вставляем внуть <div> тега
const output = <div></div>;

ReactDOM.render(output, document.querySelector("#myDiv"));
```

и создайте необходимый код, чтобы ваш файл отображал следующий вывод в DOM:


```html
<div>
    <h1>My name is Bob</h1>
    <h2>My last name is Dylan</h2>
</div>
```

# `03` Построение макета

Давайте еще немного попрактикуемся в использовании JSX для создания HTML.

Теперь у нас есть еще один объект, немного более сложный, чем предыдущий.

У вас есть `data` объект, содержащий информацию о Бобе Дилане (изображение, заголовок и т. д.).

```js
const data = {
  image: "img/Dylan.png?raw=true",
  cardTitle: "Bob Dylan",
  cardDescription: "Bob Dylan (born Robert Allen Zimmerman, May 24, 1941) is an American singer/songwriter, author, and artist who has been an influential figure in popular music and culture for more than five decades.",
  button: {
    url: "https://en.wikipedia.org/wiki/Bob_Dylan",
    label: "Go to wikipedia"
  }
};
```

## Задание:

1. Используйте информацию, содержащуюся в , `data` для визуализации карты начальной загрузки. Например: Название карты будет `data.cardTitle` и т.д.

## Ожидаемый результат:
  
![Bob Dylan Card](img/01.png?raw=true)

## Подсказки:

+ HTML-код для создания карточки в начальной загрузке:

```html
<div class="card m-5">
  <img class="card-img-top" src="..." alt="Card image cap" />
  <div class="card-body">
    <h5 class="card-title">Card title</h5>
    <p class="card-text">Some quick example text to build on the card title and make up the bulk of the cards content.</p>
    <a href="#" class="btn btn-primary">Go somewhere</a>
  </div>
</div>
```

+ [Bootstrap Card](https://getbootstrap.com/docs/5.0/components/card/#example)


# `04` Построение из массивов

С помощью `JSX` вы также можете создавать массивы элементов HTML. Например, если у нас есть массив, `<li>` мы можем включить их все в документ сразу, вот так:

```jsx
const namesInHTML = [
  <li>Bob Dust</li>,
  <li>Freddie Mercury</li>,
  <li>Shazam Nikola</li>,
  <li>Wilibin Walabam</li>
];

const content = <ul>{namesInHTML}</ul>;

ReactDOM.render(content, document.querySelector("#myDiv"));
```

Итоговый HTML-код на веб-сайте будет:

```html
<div id="myDiv">
  <ul>
    <li>Bob Dust</li>
    <li>Freddie Mercury</li>
    <li>Shazam Nikola</li>
    <li>Wilibin Walabam</li>
  </ul>
</div>
```

Допустим, мы хотим, чтобы React отображал в документе следующий вывод:

```html
<ul class="nav">
  <li class="nav-item">
    <a class="nav-link" href="#">Link to google.com</a>
  </li>
  <li class="nav-item">
    <a class="nav-link" href="#">Link to facebook.com</a>
  </li>
  <li class="nav-item">
    <a class="nav-link" href="#">Link to amazon.com</a>
  </li>
</ul>
```

## Задания:

1. Обновите `navlinkItems` массив, чтобы текущий код выводил то, что мы хотим.

```jsx
import React from "react"; 
import ReactDOM from "react-dom"; 

// Обновляем это
const navlinkItems = [];

const content = <ul className="nav">{navlinkItems}</ul>;

ReactDOM.render(content, document.querySelector("#myDiv"));
```

## Подсказки:

+ Вам нужно только обновить `navlinkItems` массив и ничего больше.

+ React попросит вас использовать ключи для каждого элемента массива. Подробнее об этом можно прочитать здесь: [https://react.dev/learn/rendering-lists#keeping-list-items-in-order-with-key](https://react.dev/learn/rendering-lists#keeping-list-items-in-order-with-key).

+ Не забудьте использовать `className` вместо `class`.

# `05` Отображение массива в `<li>`

Теперь давайте построим массив динамически...

Допустим, у вас есть массив животных:

```js
const animals = [ 'Horse', 'Turtle', 'Elephant', 'Monkey' ];
```

## Задания:

1. Обновите [map() function](https://medium.com/poka-techblog/simplify-your-javascript-use-map-reduce-and-filter-bd02c593cc2d) кода , чтобы создать новый массив <li>, соответствующий каждому животному из исходного массива. Результирующий массив должен быть примерно таким: 

```jsx
const animalsInHTML = [
  <li>Horse</li>,
  <li>Turtle</li>,
  <li>Elephant</li>,
  <li>Monkey</li>
];
```

2. Включите их все вместе на свой сайт.

## Ожидаемый результат:

![expected result of li's](img/02.png?raw=true)

## Подсказки:

+ Вы можете использовать второй параметр функции `key` для уникальной идентификации каждого элемента HTML.


# `06` Отображение массива объектов в `<li>`

Используя знания, полученные из предыдущего примера, давайте `map()` снова исправим функцию, но на этот раз начиная с массива объектов.

```js
const animals = [ { label: 'Horse' }, { label: 'Turtle' }, { label: 'Elephant' }, { label: 'Monkey' } ];
```

## Задания:

1. Обновите код [map() function](https://medium.com/poka-techblog/simplify-your-javascript-use-map-reduce-and-filter-bd02c593cc2d), чтобы создать новый массив  `<li>`', соответствующий каждому животному из исходного массива. Результирующий массив должен быть примерно таким:

```jsx
const animalsInHTML = [
  <li>Horse</li>,
  <li>Turtle</li>,
  <li>Elephant</li>,
  <li>Monkey</li>
];
```

2. Включите их все вместе на свой сайт.

## Подсказки:

+ Вы можете использовать второй параметр функции `key` для уникальной идентификации каждого элемента HTML.

## Ожидаемый результат:

![expected result of li's](img/02.png?raw=true)

Когда вы сопоставляете массив данных для преобразования его в массив HTML, вам необходимо указать «функцию сопоставления» , которая будет получать каждый элемент из исходного массива, преобразовывать его и вставлять в новый массив.

Например:

```js
const originalData = [];

const mappingFunction = (item, index) => {
  // return something in JSX
};

const htmlList = originalData.map(mappingFunction);
// The htmlList variable now contains a new array
```

## Задания:

1. Используйте [list-group bootstrap](https://getbootstrap.com/docs/5.0/components/list-group/#basic-example) компонент для отображения списка планет из заданного массива:

```js
const planets = [ 'Mars', 'Venus', 'Jupiter', 'Earth', 'Saturn', 'Neptune' ];
```

2. Используйте [map() function](https://medium.com/poka-techblog/simplify-your-javascript-use-map-reduce-and-filter-bd02c593cc2d) и заставьте свой алгоритм выводить следующий HTML-код:

```jsx
<ul class="list-group m-5">
  <li class="list-group-item">Mars</li>
  <li class="list-group-item">Venus</li>
  <li class="list-group-item">Jupiter</li>
  <li class="list-group-item">Earth</li>
  <li class="list-group-item">Saturn</li>
  <li class="list-group-item">Neptune</li>
</ul>
```

3. Включите их все вместе на сайт.

## Ожидаемый результат:

![list-group expected result](img/03.png?raw=true)

# `07` Рендеринг с помощью функций

JSX позволяет использовать функции для рендеринга HTML.

Это настоятельно рекомендуемая практика, поскольку она позволяет создавать шаблоны и повторно использовать код.

Например:

```js
// WHAT: This function returns a string that will be rendered
const PrintHello = () => {
    return <h1>Hello World</h1>;
}
                 //what       //where
ReactDOM.render(PrintHello(), myDiv);
```

## Задания:

1. Сделайте так, чтобы функция `PrintHello` возвращала `<h1>I Love React</h1>` вместо `<h1>Hello World</h1>`.

# `08` Первый функциональный компонент

Когда вы создаете функции, возвращающие HTML, JSX позволит вам рассматривать их как **компоненты** . По сути, они станут вашими собственными HTML-тегами.

Одна из вещей, которую мы можем делать благодаря JSX, — это вызывать функции так, как будто они являются тегами HTML, например:

```js
// если объявлена функция MyFunction
const MyFunction = () => {
    return <h1>I Love React</h1>;
}

// Мы можем вызвать функцию, будто это HTML тег:
<MyFunction />

// Вместо вызова функции
MyFunction();
```

Когда вы вызываете такую ​​функцию, она становится компонентом `React` , который представляет собой функцию, которая динамически генерирует (возвращает) HTML. Все, что возвращает функция, будет заменено в том же месте, где `<MyFunction/>` был помещен оригинал.

В прошлом упражнении мы создали наш первый компонент под названием `PrintHello` и узнали, что можно использовать его как HTML-тег.


```jsx
<PrintHello />
```

Теперь давайте создадим еще один компонент (функцию), `<BootstrapCard />` который выводит следующий HTML-код:

```jsx
<div class="card m-5">
  <img class="card-img-top" src="img/Dylan.png?raw=true" alt="Card image cap" />
  <div class="card-body">
    <h5 class="card-title">Bob Dylan</h5>
    <p class="card-text">Bob Dylan (born Robert Allen Zimmerman, May 24, 1941) is an American singer/songwriter, author, and artist who has been an influential figure in popular music and culture for more than five decades.</p>
    <a href="https://en.wikipedia.org/wiki/Bob_Dylan" class="btn btn-primary">Go to wikipedia</a>
  </div>
</div>
```

## Задания:

1. Создайте функцию, `BootstrapCard` которая возвращает код карты, используйте эту `ReactDOM.render` функцию и `<BootstrapCard />` добавьте ее на веб-сайт внутри `#myDiv`.

То, что `BootstrapCard` вы только что сделали, жестко запрограммировано только для Боба Дилана .

Но что, если мы захотим повторно использовать тот же `<BootstrapCard />` компонент для Пола Маккартни или любого другого человека? Как лучше всего это сделать? Используйте реквизит!

## Использование свойств в HTML

Когда вы кодируете HTML, вы постоянно используете `<tag>` свойства для изменения поведения тега, например, когда вы используете тег привязки `<a>`, вам необходимо указать свойство `href` следующим образом:

```html
<a href="http://google.com">Take me to google</a>
<a href="http://twitter.com">Take me to twitter</a>
```

## Использование свойств в React.js

В React.js мы также можем создавать собственные теги и использовать собственные изобретенные свойства. Например, мы могли бы указать `title` свойство нашего `<BootstrapCard />`, вот так:

```jsx
               // For Paul McCartney
<BootstrapCard title="Paul McCartney" />

               // For Bob Dylan
<BootstrapCard title="Bob Dylan" />
```

Наш `component` получит все свои свойства (включая заголовок) через первый параметр, который мы можем вызвать `props`.

```jsx
const BootstrapCard = (props) => {
  return <div class="card">
    ...
      <h5 class="card-title">{props.title}</h5>
    ...
  </div>;
}
```

Чтобы иметь возможность работать со свойствами компонента, вам необходимо указать, какие свойства получит компонент (имя и тип данных каждого свойства), [здесь вы можете прочитать больше о prop-types](https://reactjs.org/docs/typechecking-with-proptypes.html).

Например: 

```jsx
// Здесь мы указываем, что этот компонент получит свойство «title» и это будет строка.
BootstrapCard.propTypes = {
	title: PropType.string
};
```

## Задания:

1. Используйте `imageUrl`, `description`, `buttonUrl` и `buttonLabel` свойства компонента `BootstrapCard` и тега `<BootstrapCard />` по аналогии с `title`.

```jsx
import React from "react";
import ReactDOM from "react-dom";
import PropType from "prop-types";

const BootstrapCard = props => {
	// 1) Replace the hard-coded image, description, link, etc. With their property variable
	return (
		<div className="card m-5">
			<img className="card-img-top" src="img/Dylan.png?raw=true" alt="Card image cap" />
			<div className="card-body">
				<h5 className="card-title">{props.title}</h5>
				<p className="card-text">Bob Dylan (born Robert Allen Zimmerman, May 24, 1941) is an American singer-songwriter.</p>
				<a href="https://en.wikipedia.org/wiki/Bob_Dylan" className="btn btn-primary">
					Go to wikipedia
				</a>
			</div>
		</div>
	);
};
BootstrapCard.propTypes = {
	title: PropType.string
	// 2) Add here the new properties into the proptypes object
};


// 3) Use ReactDOM to add the component into then DOM element #myDiv
```

## Подсказки:

+ Вам придется отредактировать 3 части файла (помощь можно найти в комментариях).

+ Первым шагом будет замена жестко закодированных свойств свойствами внутри компонента.

+ Вторым шагом будет определение этих свойств в объекте prop-types в строке 23.

+ Третьим шагом будет использование ReactDOM для добавления `<BootstrapCard />` объявления тега, включая 5 свойств и их соответствующие значения.

+ Вам не нужно визуализировать компонент дважды, достаточно один раз.

2. Создайте `Hero` компонент, который получит следующие свойства:


```jsx
<Hero
  title="Welcome to react"
  description="React is the most popular rendering library in the world"
  buttonLabel="Go to the official website"
  buttonURL="https://reactjs.org/"
/>
```

## Ожидаемый результат:

![Hero](img/04.png?raw=true)

## Подсказки:

- Не забудьте использовать типы свойств для проверки свойств вашего компонента.

- Ваш HTML-компонент должен выглядеть примерно так:

```html
<div class="container m-5">
  <h1 class="display-4">Welcome to react</h1>
  <p class="lead">React is the most popular rendering library in the world</p>
  <a class="btn btn-primary btn-lg" href="https://reactjs.org/" role="button"
    >Go to the official website</a
  >
</div>
```
3. Создайте `<Alert />` компонент, который получает 1 свойство `text: PropTypes.string` и отображает [bootstrap alert](https://getbootstrap.com/docs/5.0/components/alerts/#examples) :

## Ожидаемый результат:

Вот что компонент должен вывести в формате HTML:

```html
<div class="alert alert-danger" role="alert">
  OMG! Something really bad has happened!
</div>
```
## Подсказки:

+ Вот как следует использовать компонент:

```jsx
<Alert text="OMG! Something really bad has happened!" />
```
# `09` Условный рендеринг

Вы также можете использовать свойства компонента, чтобы изменить его поведение, например показать или скрыть свое изображение `<Alert />` на основе свойства с именем `show`.

```jsx
{/* Ваше оповещение будет отображаться */}
<Alert text="Are you sure?" show={true}>

{/* Это сделает ваше оповещение скрытым. */}
<Alert text="Are you sure?" show={false}>
```

Мы можем добиться этого, добавив `if...else` оператор внутри метода рендеринга следующим образом:

```jsx
const Alert = (props) => {
    if(props.show === false){
        return null;
    }
    else{
        // return here the component html
    }
};
```

> Подробнее [conditional rendering](https://react.dev/learn/conditional-rendering).

## Задания:

1. Реализуйте условный рендеринг в `<Alert />` компоненте, чтобы отображать компонент, когда `show` свойство имеет значение, `true` и скрывать его, когда оно равно `false`.

## Подсказки:

Компонент должен иметь возможность получать следующие 2 свойства:

+ `show` (bool): True или  false.

+ `text` (string): сообщение, которое будет включено в оповещение.

Давайте сделаем наш `<Alert />` компонент немного умнее.

При использовании JSX вам доступны все функции JavaScript: переменные, циклы, условные выражения и т. д.

Например, следующий код отображает красное или желтое предупреждение, в зависимости от `color` свойства.

```jsx
const colorClasses = {
    'red': 'alert-danger',
    'yellow': 'alert-warning'
}

<div class={`alert ${colorClasses[props.color]}`} role="alert">
  This is an alert - check it out!
</div>
```

Мы объявляем переменную `colorClasses` , которая будет содержать все имена классов, которые будут применены к оповещению.

## Задания:

1. Создайте  `<Alert />` компонент, который меняет свой цвет, изменив `color` свойство: [bootstrap's alert color names](https://getbootstrap.com/docs/5.0/components/alerts/#examples).

## Подсказки:

Компонент должен иметь возможность получать следующие 2 свойства:

+ `text` (string): текстовое содержимое, которое будет отображаться в оповещении.

+ `color` (string): красный или желтый цвета.

```jsx
{/* For red color */}
<div class="alert alert-danger" role="alert">
  This is a danger alert - check it out!
</div>

{/* For yellow color */}
<div class="alert alert-warning" role="alert">
  This is a warning alert - check it out!
</div>
```
2. Добавьте, пожалуйста, возможность указать **зеленый** цвет .

## Ожидаемый результат:

Ваш сайт должен выглядеть примерно так:

![3 Color Alert](img/05.png?raw=true)

# `10` Добавление стилей к компонентам

Наиболее рекомендуемый способ создания стилей в React — использование CSS-in-JS.

По сути, вы создаете объект со своими стилями следующим образом:

```jsx
const mySuperStyles = {
    color: "blue",
    fontSize: "14px",
    border: "1px solid black"
};
```

А затем вы можете применить эти стили к своему HTML следующим образом:

```jsx
<div style={mySuperStyles}>I am an alert</div>
```

## Задания:

1. В текущем упражнении есть объект, к которому уже применены стили. Обновите стили следующим образом:

    + Размер шрифта должен быть `16px`

    + Цвет фона должен быть `black`.

    + Желтая сплошная граница с  `1px`.

2. Теперь давайте изменим стили компонента Badge, чтобы он выглядел следующим образом:

![Alert in bootstrap](img/06.png?raw=true)

## Подсказки:

+ Вам следует стилизовать только цвета фона, цвета текста и границы.
  
+ Значок имеет  `border-radius` `50%`

# `11` Прослушивание событий

События в React работают почти так же, как в Vanilla JS: если вы хотите прослушивать пользовательские действия `Click`, все, что вам нужно сделать, это добавить свое `onClick` свойство (или любое другое событие) в HTML-тег, как это обычно делается.

Текущий код имеет один компонент, который `I was clicked!` при нажатии выводит на консоль.

## Задания:

1. Обновите `<Alert />` компонент, чтобы он правильно прослушивал `onClick` событие с `handleClick` функцией, а затем проверьте консоль.


