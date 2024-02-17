# Практическая работа № 1. Базовая HTML+CSS верстка

Для выполнения задания потребуется редактор, например, VSCode и браузер, например, Chrome. Выполнение происходит с периодическим сохранением с системой контроля версий Git.

# Задания:

---------------

1. Изучить файл [html-basic.pdf](/01/files/html-basic.pdf)
   
---------------

2. Составить страницу ***index-1.html*** следующего вида используя теги: *head*, *body*, *h***X**, *p*, *em*, *s*, *strong*, *br*, *u*, *ul*, *li*, *ol*, *dl*, *dt*, *dd* и др.

![Итоговый дизайн страницы](/01/img/img1.png)

---------------

3. Используя теги *a*, *img* вставить ссылку на другую страницу и изображение на страницу. Добавить ссылку на скачивание файла с диска (используя атрибут *download* тега *a*). Изображение и файл для скачивания разместить в ресурсах (подпапке) *img* и *files*.

![Расположение папок проекта](/01/img/img2.png)

![Итоговый дизайн страницы с изображениями](/01/img/img3.png)

Проверить, что скачивание работает:

![Скачивание работает](/01/img/img4.png)

---------------

4. Изучить формат файла svg (https://www.w3schools.com/graphics/svg_intro.asp). 
   
* Вставить SVG-изображение следующего содержания:

```
<svg xmlns="http://www.w3.org/2000/svg" height="400" width="450">
  <path d="M100 350 250 50m0 0 150 300" stroke="red" stroke-width="3" fill="none" />
  <path d="M175 200h150" stroke="green" stroke-width="3" fill="none" />
  <path d="M100 350q150-300 300 0" stroke="#00f" stroke-width="5" fill="none" />
  <!-- Mark relevant points -->
  <g stroke="#000" stroke-width="3">
    <circle cx="100" cy="350" r="3" />
    <circle cx="250" cy="50" r="3" />
    <circle cx="400" cy="350" r="3" />
  </g>
  <!-- Label the points -->
  <g font-size="30" font-family="sans-serif" text-anchor="middle">
    <text x="100" y="350" dx="-30">A</text>
    <text x="250" y="50" dy="-10">B</text>
    <text x="400" y="350" dx="30">C</text>
  </g>
</svg>
```

Должно получиться следующее:

![Вставленное SVG изображение](/01/img/img5.png)

* Реализовать генерацию следующих фигур с различной раскраской, абрисом, заполнением и прозрачностью:
  - круг
  - прямоугольник
  - полигон + звезда
  - текст
  - кривая произвольной формы
  - комбинация фигур с наложением
   
   Новые изображения разместить на текущей странице.

---------------

5. Добавление видео и аудио в разметку HTML

Подготовить краткий ролик и аудиодорожку и сохранить их в каталог *media*. С использованием тегов *video* и *audio* и их атрибутов добавить их на страницу. Исследовать возможности автопроигрывания и скачивания: *controls*, *autoplay*, *preload*, *loop*, *poster*.
Изучить контейнер *iframe*.

---------------

6. Изучить файл [css-basic.pdf](/01/files/css-basic.pdf)

---------------

7. Используя стили, представленные ниже, составить страницу ***index2.html***, изображенную на картинке. Стиль расположить в каталоге *css*.

```
body {
    font-family: Arial, sans-serif;
    font-size: 15px;
    line-height: 1.5;
    color: #333;
}

p {
    text-indent: 20px;
}

.title {
    font-family: Tahoma, sans-serif;
    text-align: center;
    font-weight: 700;
    letter-spacing: -2px;
    text-decoration: line-through;
    text-transform: uppercase;
}

.justify {
    text-align: justify;
    font-weight: 700;
    font-style: italic;
    text-transform: capitalize;
}

ul {
    list-style-type: square;
    list-style-position: outside;

    color: #114eaf;
}

ol {
    list-style-type: decimal-leading-zero;
}
```

![Текст с использованием стилей CSS](/01/img/img6.png)

---------------

8. Используя теги таблиц *table*, *td*, *tr* построить таблицу вида:

![Таблица](/01/img/img7.png)

Используя разные стили расположения элементов в таблице изменить макет страницы, дополнив нужными данными. Реализовать три варианта по номеру студнета в списке по модулю 15 по схеме: например, № студента = 1, тогда таблицы 1, 6, 11, № студента 14: таблицы: 14, 4, 9,  № студента 18 => 3: таблицы  3, 8, 13 и т.д.

Варианты:

- 1  ![1](/01/img/table1.jpg)
- 2  ![1](/01/img/table2.jpg)
- 3  ![1](/01/img/table3.jpg)
- 4  ![1](/01/img/table4.jpg)
- 5  ![1](/01/img/table5.jpg)
- 6  ![1](/01/img/table6.jpg)
- 7  ![1](/01/img/table7.jpg)
- 8  ![1](/01/img/table8.jpg)
- 9  ![1](/01/img/table9.jpg)
- 10 ![1](/01/img/table10.jpg)
- 11 ![1](/01/img/table11.jpg)
- 12 ![1](/01/img/table12.jpg)
- 13 ![1](/01/img/table13.jpg)
- 14 ![1](/01/img/table14.jpg)
- 15 ![1](/01/img/table15.jpg)


---------------

# Материалы

[1][Основы HTML](https://www.w3schools.com/html/default.asp)
[2][Основы CSS](https://www.w3schools.com/css/default.asp)
[3][Основы SVG](https://www.w3schools.com/graphics/svg_intro.asp)