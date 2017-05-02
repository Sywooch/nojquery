# You don't need jQuery

> Моя шпаргалка по использованию нативного js вместо jQuery 

### Браузер полностью загрузил HTML, и построил DOM-дерево.

```javascript

// jQuery
$(document).ready(function() { 
    alert('ready');
});

// Native
document.addEventListener("DOMContentLoaded", function(){
    alert('Load');
});

```

### Возвращает все элементы с заданным тегом 

```javascript

// jQuery
$('div');

// Native
document.getElementsByTagName('div');

```

### Возвращает элемент с идентификатором

```javascript

// jQuery
$('#id')

// Native
document.getElementById('id');

```

### Возвращает все элементы с заданным name

```javascript

// jQuery
$('[name = name]')

// Native
document.getElementsByName('name');

```

### Возвращает все элементы с заданным классом

```javascript

// jQuery
$('.class')

// Native
document.getElementsByClassName('class');

```

### Возвращает не все, а только первый элемент, соответствующий CSS-селектору

```javascript

// Native
document.querySelector(':hover');

```

### Возвращает все элементы удовлетворяющие CSS-селектору

```javascript

// jQuery
$(':hover')

// Native
document.querySelectorAll(':hover');

```

### Ajax запрос методом GET

```javascript

// jQuery
$.ajax('myservice/username', {
    data: {
        id: 'some-unique-id'
    }
})
.then(
    function success(name) {
        alert('User\'s name is ' + name);
    },

    function fail(data, status) {
        alert('Request failed.  Returned status of ' + status);
    }
);

// Native
var xhr = new XMLHttpRequest();
xhr.open('GET', 'myservice/username?id=some-unique-id');
xhr.onload = function() {
    if (xhr.status === 200) {
        alert('User\'s name is ' + xhr.responseText);
    }
    else {
        alert('Request failed.  Returned status of ' + xhr.status);
    }
};
xhr.send();

```

### Ajax запрос методом POST

```javascript

// jQuery
var newName = 'John Smith';

$.ajax('myservice/username?' + $.param({id: 'some-unique-id'}), {
    method: 'POST',
    data: {
        name: newName
    }
})
.then(
    function success(name) {
        if (name !== newName) {
            alert('Something went wrong.  Name is now ' + name);
        }
    },

    function fail(data, status) {
        alert('Request failed.  Returned status of ' + status);
    }
);

// Native
var newName = 'John Smith',
    xhr = new XMLHttpRequest();

xhr.open('POST', 'myservice/username?id=some-unique-id');
xhr.setRequestHeader('Content-Type', 'application/x-www-form-urlencoded');
xhr.onload = function() {
    if (xhr.status === 200 && xhr.responseText !== newName) {
        alert('Something went wrong.  Name is now ' + xhr.responseText);
    }
    else if (xhr.status !== 200) {
        alert('Request failed.  Returned status of ' + xhr.status);
    }
};
xhr.send(encodeURI('name=' + newName));

```

### Ajax отправка и получение JSON

```javascript

// jQuery
$.ajax('myservice/user/1234', {
    method: 'PUT',
    contentType: 'application/json',
    processData: false,
    data: JSON.stringify({
        name: 'John Smith',
        age: 34
    })
})
.then(
    function success(userInfo) {
        // userInfo will be a JavaScript object containing properties such as
        // name, age, address, etc
    }
);

// Native
var xhr = new XMLHttpRequest();
xhr.open('PUT', 'myservice/user/1234');
xhr.setRequestHeader('Content-Type', 'application/json');
xhr.onload = function() {
    if (xhr.status === 200) {
        var userInfo = JSON.parse(xhr.responseText);
    }
};
xhr.send(JSON.stringify({
    name: 'John Smith',
    age: 34
}));

```

### Ajax кросс-доменный запрос

```javascript

// jQuery
$.ajax('http://someotherdomain.com', {
    method: 'POST',
    contentType: 'text/plain',
    data: 'sometext',
    beforeSend: function(xmlHttpRequest) {
        xmlHttpRequest.withCredentials = true;
    }
});

// Native
var xhr = new XMLHttpRequest();
xhr.open('POST', 'http://someotherdomain.com');
xhr.withCredentials = true;
xhr.setRequestHeader('Content-Type', 'text/plain');
xhr.send('sometext');

```

### Возвращает или изменяет текстовое содержимое выбранных элементов страницы.

```javascript

// jQuery

$el.text();

// Native

el.textContext;

```

### Возвращает или изменяет значение атрибутов у выбранных элементов страницы.

```javascript

// jQuery

$el.attr('data-my-attribute');

// Native

el.getAttribute('data-my-attribute')

```

### Возвращает или изменяет значения css-величин у выбранных элементов страницы.

```javascript

// jQuery

$el.css({ color: '#ccc'});

// Native

el.style.color = '#ccc';

```

### Метод позволяет получать и изменять значения элементов форм.

```javascript

// jQuery

$('#input-example').val();

// Native

document.getElementById('input-example').value;

```

### Возвращает все дочерние элементы выбранных элементов, а так же текстовое содержимое.

```javascript

// jQuery

$('#iframe').contents();

// Native

document.getElementById('iframe').contentDocument;

```

### Возвращает или изменяет html-содержимое выбранных элементов страницы.

```javascript

// jQuery

$el.html();

// Native

el.innerHtml;

```

### Конвертирует строку с json-данными в javascript-объект.

```javascript

// jQuery

$.parseJSON('{ example: 123 }');

// Native

JSON.parse('{ example: 123 }');

```

### Добавляет класс(ы) выбранным элементам страницы.

```javascript

// jQuery

$el.addClass('my-class');

// Native IE10+

el.classList.add('my-class');

// NAtive IE8+

el.className += ' my-class';

```

### С помощью этих функций можно плавно показывать и скрывать выбранные элементы на странице, за счет изменения размера и прозрачности.

```javascript

// jQuery

$el.hide();

// Native

el.style.display = 'none';

```

### Метод создает копии выбранных элементов страницы и возвращает их в виде объекта.

```javascript

// jQuery

$el.clone();

// Native

el.cloneNode(true);

```

### Находит дочерние элементы.

```javascript

// jQuery

$el.children();

// Native

el.children;

```

### Обработка события.

```javascript

// jQuery

$('.js-target-minus').on();

$( "body" ).on( "click", "#id", function(e) {
    console.log('test');
    e.preventDefault();
});

// Native

document.getElementById('id').addEventListener('click', function(e){
    console.log('test');
    e.preventDefault();
});

```