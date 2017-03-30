# You don't need jQuery

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


