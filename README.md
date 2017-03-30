# You don't need jQuery

> Моя шпаргалка по испольщованию нативного js вместо jQuery 

## Возвращает или изменяет текстовое содержимое выбранных элементов страницы.

// jQuery
$el.text();

// Native
el.textContext;

## Возвращает или изменяет значение атрибутов у выбранных элементов страницы.

// jQuery
$el.attr('data-my-attribute');

// Native
el.getAttribute('data-my-attribute')

## Возвращает или изменяет значения css-величин у выбранных элементов страницы.

// jQuery
$el.css({ color: '#ccc'});

// Native
el.style.color = '#ccc';

## Метод позволяет получать и изменять значения элементов форм.

// jQuery
$('#input-example').val();

// Native
document.getElementById('input-example').value;

## Возвращает все дочерние элементы выбранных элементов, а так же текстовое содержимое.

// jQuery
$('#iframe').contents();

// Native
document.getElementById('iframe').contentDocument;

## Возвращает или изменяет html-содержимое выбранных элементов страницы.

// jQuery
$el.html();

// Native
el.innerHtml;

## Конвертирует строку с json-данными в javascript-объект.

// jQuery
$.parseJSON('{ example: 123 }');

// Native

JSON.parse('{ example: 123 }');

## Добавляет класс(ы) выбранным элементам страницы.

// jQuery
$el.addClass('my-class');

// Native IE10+
el.classList.add('my-class');

// NAtive IE8+
el.className += ' my-class';

## С помощью этих функций можно плавно показывать и скрывать выбранные элементы на странице, за счет изменения размера и прозрачности.

// jQuery
$el.hide();

// Native
el.style.display = 'none';

## Метод создает копии выбранных элементов страницы и возвращает их в виде объекта.

// jQuery
$el.clone();

// Native
el.cloneNode(true);

## Находит дочерние элементы.

// jQuery
$el.children();

// Native
el.children;
