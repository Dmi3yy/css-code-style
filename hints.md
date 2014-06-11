Полезные приемы в верстке
=========================

### Оформление нумерованных списков

![Пример списка](http://screenshoots.very-good.ru/upload/2014-06-11/47a959173f6dc1d0dc8e8170e498a70f.png)

```css
ol {counter-reset:li; list-style:none; *list-style:decimal;}
    ol > li {display:block;}
    ol > li:before {display:inline-block; content:counters(li, ".")")"; font-weight:bold; margin-right:3px; counter-increment:li;}
```
