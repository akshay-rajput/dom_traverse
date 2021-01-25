---
pageTitle: Jquery to Javascript migration - Part 1
---
<!-- # Moving from Jquery to Javascript - Part 1 -->

## Document Ready Function
The function is called when the page is loaded. Thus, the execution of JavaScript does not block the page from loading.

```js
// with jQuery
$(function() {
  /* ... */
});

// Vanilla JS
function ready(fn) {
  if (document.readyState != 'loading'){
    fn();
  } else {
    document.addEventListener('DOMContentLoaded', fn);
  }
}
ready(() => {
  /* ... */
});

```

## Selecting elements
The biggest difference when selecting elements is that in pure JavaScript you have to create a loop if there are multiple elements.

```js
// with jQuery
// multiple elements
let buttons = $('button.red-btn');
// one element
let button = $('button.green-btn');

// Vanilla JS
// multiple elements
let buttons = document.querySelectorAll('button.red-btn');
// one element
let button = document.querySelector('button.green-btn');
```

### Finding parent of selected node

With parentNode you get the parent element. You can also string the statement together to get elements further up in the DOM – i.e. parentNode.parentNode

```js
// with jQuery
let foobarParent = $('#foobar-container').parent();
// Vanilla JS
let foobarParent = document.querySelector('#foobar-container').parentNode;
```

----

## Event handling

For event handling you have to look if you have one or more elements. JQuery doesn’t care, it just registers the event. Here is an example for both situations.

```js
// with jQuery
$('.link').click(function() {
  /* ... */
});

// Vanilla JS
// one element
document.querySelector('#link').addEventListener('click', event => {
  /* ... */
});
// more elements
document.querySelectorAll('.link').forEach(link => {
  link.addEventListener('click', event => {
    /* ... */
  });
});

```
----

## Show & Hide elements

To achieve show() and hide(), we simply change the CSS property display accordingly.

```js
// with jQuery
$('.foobar').show();

// Vanilla JS
document.querySelectorAll('.foobar').forEach(element => {
  element.style.display = 'block';
});
```
```js
// with jQuery
$('.foobar').hide();

// Vanilla JS
document.querySelectorAll('.foobar').forEach(element => {
  element.style.display = 'none';
});
```
