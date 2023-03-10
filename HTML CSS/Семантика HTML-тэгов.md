# Семантика HTML-тэгов

## Элементы разметки контента документа

### `<div>`
Не имеет семантики. Используется для группировки других элементов, в том случае, когда ни один другой элемент не подходит по семантике.

### `<span>`
Не имеет семантики. Используется для **последовательной (inline)** группировки других элементов, в том случае, когда ни один другой элемент не подходит по семантике. Обычно используется для стилизации текста внутри `<p>` или `<h>`.

### `<dialog>`
Используется в случаях, когда ход программы останавливается для интеракции с пользователем в рамках окна.
```html
<dialog open>
  <summary>Вы уверены что хотите это сделать?</summary>
  <button>Нет</button>
  <button>Да</button>
</dialog>
```

### `<details> > <summary>`
Используется для отображения скрытого контента. При клике на `<summary>` открывается всё содержимое `<details>`. Семантика этого элемента - это *Spoiler*.
```html
<details>
  <summary>Что произойдет?</summary>
  <p>Скорее всего - ничего необычного.</p>
</details>
```

### `<data>, <time>`
Эти элементы используются для того, чтобы присвоить контенту документа машиночитаемое значение.
```html
<ul>
  <li><data value="398">Log 398 at <time datetime="2022-07-06">July 6</time></data></li>
  <li><data value="399">Log 399 at <time datetime="2022-07-07">July 7</time></data></li>
  <li><data value="400">Log 400 at <time datetime="2022-07-07">July 7</time></data></li>
</ul>
```

### `<main>, <article>, <section>`
Эти тэги являются основными тегами контента документа. Обычно страница документа состоит из одного `<main>`, который может содержать много `<article>`, который в свою очередь состоит из нескольких `<section>`. Это позволяет логически разбить документ на  блоки с контентом, которые пользователь может изучать не зависимо друг от друга.
```html
<main>
  <div>
    <article>
      <header>
        <h1>Пост 1</h1>
        <time>08.12.2014</time>
      </header>

      <p>Описание поста 1</p>
    </article>

    <article>
      <header>
        <h1>Пост 2</h1>
        <time>08.12.2014</time>
      </header>

      <section>
        <p>Описание поста 2</p>
      </section>

      <section>
        <p>Ещё описание поста 2</p>
      </section>
    </article>

    <article>
      <header>
        <h1>Пост 3</h1>
        <time>08.12.2014</time>
      </header>

      <details>
        <summary>Комментарии</summary>
        <article>
          Комментарий к посту 3
        </article>
      </details>
    </article>
  </div>
</main>
```
Семантика `<main>` - быть контейнером для основного контента на странице.
Семантика `<article>` - быть контейнером для контента, который может быть отдельно усвоен посетителем сайта. Если у вас блог, то каждый пост - это один `<article>`, потому что посетитель может изучить каждый из постов отдельно. Но `<article>` также может содержать контент который связан с родительским `<article>`, как показано в примере выше. Так происходит, потому что сам пост в блоге - это отдельно усваиваемый кусочек информации, но и комментарий к этому посту также является отдельно усваиваемым кусочком информации.
Семантика `<section>` - быть контейнером для частей `<article>` и, например, отделить галерею поста от его описания.

### `<aside>`
Представляет часть контента документа вне `<main>`. Сайдбары, fixed-кнопки и т.д.
```html
<aside>
  <nav>
    <a href="/main">Main page</a>
    <a href="/about">About</a>
  </nav>
</aside>
```

### `<nav>`
Представляет группу ссылок объединенных по смыслу.
```html
<nav>
  <a href="/html/">HTML</a>
  <a href="/css/">CSS</a>
</nav>
```

### `<header>, <footer>`
Элементы используются для маркировки начала и конца контента. Могут быть вложены в любой элемент. Могут содержать различные элементы, но эти элементы должны относиться/влиять на все последующие элементы или описывать их: изображения, формы, заголовки, текст и т.д.
```html
<article>
  <header>
    <h3>Нейронные сети победили</h3>
    <address>Автор: @spooky_lord</address>
  </header>
  
  <section>
    <!-- Контент поста -->
  </section>

  <footer>
    <nav class="flex flex-row">
      <a href="/home">Главная</a> >
      <a href="/home/author/spooky_lord">@spooky_lord</a> >
      <a href="/home/author/spooky_lord/145">Нейронные сети победили</a>
    </nav>
  </footer>
</article>
```

## Элементы форматирования контента документа

### Списки

#### Обычный список
Обычный список, каждый элемент которого имеет одинаковый семантический вес
```html
<ul>
  <li>Элемент списка</li>
</ul>
```

#### Нумерованный список
Каждый элемент списка пронумерован, содержит семантику порядка/последовательности (элементы списка расположены в порядке важности)
```html
<ol>
  <li>Элемент списка</li>
</ol>
```

#### Список с описанием
Каждый элемент списка содержит описание. Семантика идентична [обычному списку](#обычный-список)
```html
<dl>
  <dt>Наименование элемента списка</dt>
  <dd>Описание элемента списка</dd>
</dl>
```

### Формы

#### Группировка полей и наименование группы
```html
<fieldset>
  <legend>Наименование группы полей:</legend>
</fieldset>
```

#### Список подсказок автозаполнения для инпута
```html
<input list="browsers">

<datalist id="browsers">
  <option value="Chrome">
  <option value="Firefox">
</datalist>
```

### Медиа

#### Изображение с кликабельными областями
```html
<img src="image.jpg" usemap="#workmap" width="400" height="379">

<map name="workmap">
  <area shape="rect" coords="34,44,270,350" href="computer.htm">
  <area shape="rect" coords="290,172,333,250" href="phone.htm">
  <area shape="circle" coords="337,300,44" href="coffee.htm">
</map>
```

#### Вариации изображения
Позволяет задать набор изображений, при этом выводиться то изображение, которое подпадает под условия отображения
```html
<picture>
  <source media="(min-width:465px)" srcset="image_xs.jpg">
  <source media="(min-width:650px)" srcset="image_md.jpg">
  <img src="image_xl.jpg">
</picture>
```
