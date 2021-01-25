---
pageTitle: Jquery to Javascript migration - Part 2
---
<!-- # Moving from Jquery to Javascript - Part 2 -->

## Querying, Adding & Removing classes

The query and handling of the classes works as easy as with jQuery. Only the spelling is a bit different. If you need a toggleClass() function, you can easily program it yourself.

``` js
// with jQuery
if($('.foo').hasClass('bar')) {
  /* ... */
}

// Vanilla JS
if(document.querySelector('.foo').classList.contains('bar')) {
  /* ... */
}
```

----

### Add a class

```js
// with jQuery
$('.foo').addClass('bar');

// Vanilla JS
document.querySelector('.foo').classList.add('bar');
```

----

### Remove a class

```js
// with jQuery
$('.foo').removeClass('bar');

// Vanilla JS
document.querySelector('.foo').classList.remove('bar');
```

----

## Querying attributes

The query of other attributes is also quite similar. Note that sometimes the output is different from the jQuery function.

```js
// with jQuery
console.log($('.foobar').attr('checked')); // Output: checked/undefined

// Vanilla JS
console.log(document.querySelector('.foobar').checked); // Output: true/false
```

```js
// with jQuery
$('.foobar').html();
$('.foobar').html('<span>Hello world!</span>');

// Vanilla JS
document.querySelector('.foobar').innerHTML;
document.querySelector('.foobar').innerHTML = '<span>Hello world!</span>';
```

----

## Styling of elements
For styles that are joined with a hyphen, you can use the Camel Case spelling. For example, justify-content becomes justifyContent.

```js

// with jQuery
$('.foobar').css('display', 'flex');
$('.foobar').css('margin-top', '3rem');
let displayProperty = $('.foobar').css('display');

// Vanilla JS
document.querySelector('.foobar').style.display = 'flex';
document.querySelector('.foobar').style.marginTop = '3rem';
let element = document.querySelector('.foobar');
let elementStyle = getComputedStyle(element, null);
let displayProperty = elementStyle.display;

```

----

## Create new elements

If you want to create new elements and add them to an element, you can do this as follows.

Individual attributes and classes must be added individually, described in more detail in the section Querying and changing attributes of elements.

```js

// with jQuery
$('.foo').append('<p class="child" id="child-id">bar</p>');

// Vanilla JS
let bar = document.createElement('p');
bar.classList.add('child');
bar.id = 'child-id';
bar.innerHTML = 'bar';
document.querySelector('.foo').appendChild(bar);

```