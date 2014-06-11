# Требования к верстке контентных блоков

_Данные правила распространяются на все контентные блоки подлежащие оформлению, будь то текст на контентной странице или превью в списке новостей, обычно такие тексты оформляются и выглядят совершенно одинаково, поэтому логично использовать для всех текстовых блоков единый класс._

Блоки оформленного текста должны обрамляться в тег с классом `text-block`. Текст должен располагаться в тегах `<p></p>`. Абзацы должны иметь отступ друг от друга без дополнительной вставки `<br />`. Например:
```html
<div class="text-block">
    <p>Пример текста</p>
</div>
```

```css
.text-block {font-size:13px; line-height:1.2; color:#000;}
.text-block * + p {padding-top:10px;}
```

### Стандартные HTML теги
Теги `<strong>`, `<b>`, `<em>`, `<i>`, `<u>`, `<s>` должны правильно оформлять текст в соответствии с предназначением даже без указания класса. Если используется `reset.css`, сбрасывающий эти стили, незабываем их назначить. Например:
```css
.text-block b, .text-block strong {font-weight:bold;}
.text-block i, .text-block em {font-style:italic;}
```

### Стилизованные элементы
Списки `<ul>`, `<ol>`, таблицы `<table>`, изображения `<img>`, а так же остальные элементы оформление которых задается исключительно макетом должны стилизоваться внутри текстового блока только при наличии класса `stylized`. Например:
```html
<div class="text-block">
    <!-- Этот список будет стилизоваться -->
    <ul class="stylized">
        <li>Пример</li>
    </ul>

    <!-- Этот список стилизоваться не будет, его оформление полностью сбрасывается в reset.css -->
    <ul>
        <li>Пример</li>
    </ul>
</div>
```

Дополнительное оформление задается дополнительными классами. Стилизация по умолчанию выбирается на усмотрение разработчика. Например, у нас есть два типа маркированного списка `<ul>` один из которых маркируется кружками, а другой квадратами. В таком случае это будет выглядеть так:
```html
<div class="text-block">
    <!-- Этот список будет стилизоваться кружками (по-умолчанию) -->
    <ul class="stylized">
        <li>Пример</li>
    </ul>

    <!-- Этот список будет стилизоваться квадратами (доп. класс square) -->
    <ul class="stylized square">
        <li>Пример</li>
    </ul>
</div>
```

Обязательно нужно предусмотреть автоматические отступы у списков и таблиц:
```css
.text-block * + ul {margin-top:10px;}
.text-block * + ol {margin-top:10px;}
.text-block * + table {margin-top:10px;}
```

### Оформление изображений
Изображения выравниваются в трех направлениях с помощью трех классов:
- Влево: `visual-left`
- Вправо: `visual-right`
- По центру: `visual-center`

Например:
```html
<div class="text-block">
    <!-- Эти изображения стилизуются и выравниваются -->
    <img class="stylized visual-left" src="image.png">
    <img class="stylized visual-right" src="image.png">
    <img class="stylized visual-center" src="image.png">

    <!-- А это не стилизуется совсем -->
    <img src="image.png">
</div>
```
```css
.text-block img.stylized {border:5px solid #fff;}
.text-block img.visual-left {float:left; margin:0 20px 12px 0;}
.text-block img.visual-center {display:block; margin:0 auto 0 auto;}
.text-block img.visual-right {float:right; margin:0 0 12px 20px;}
```

Так же желательно стилизовать `float:left/right` изображения, например так:
```css
.text-block img[style*="float:left"], .text-block img[style*="float: left"] {float:left; margin:0 20px 12px 0;}
.text-block img[style*="float:right"], .text-block img[style*="float: right"] {float:right; margin:0 0 12px 20px;}
```
