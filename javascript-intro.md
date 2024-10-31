Javascript Intro
===

# What is Javascript

**script.html**
```
<button onclick="alert('hello world')">Button</button>
```

# DOM - Document Object Model

# Elements

```
const element = document.getElementById("intro");

const element = document.getElementById("myElement");

const elements = document.getElementsByClassName("myClass");

const elements = document.getElementsByTagName("div");


```

# HTML Properties

``
document.getElementById(id).innerHTML = new HTML

document.getElementById("p2").style.color = "blue";

``

<script>
document.write(Date());
</script>



# Events

Mouse Events
click - Fired when an element is clicked.
dblclick - Fired when an element is double-clicked.
mousedown - Fired when a mouse button is pressed on an element.
mouseup - Fired when a mouse button is released over an element.
mouseenter - Fired when the mouse pointer enters an element.
mouseleave - Fired when the mouse pointer leaves an element.
mousemove - Fired when the mouse pointer is moving over an element.
mouseover - Fired when the mouse pointer is moved onto an element or one of its children.
mouseout - Fired when the mouse pointer moves out of an element.
contextmenu - Fired when the right mouse button is clicked (usually opens the context menu).
2. Keyboard Events
keydown - Fired when a key is pressed down.
keypress - Fired when a key is pressed (deprecated; prefer keydown or keyup).
keyup - Fired when a key is released.
3. Form Events
submit - Fired when a form is submitted.
reset - Fired when a form is reset.
focus - Fired when an element (such as input) receives focus.
blur - Fired when an element loses focus.
change - Fired when the value of an element changes.
input - Fired when the value of an <input>, <textarea>, or <select> element is changed.
select - Fired when some text is selected.

# Variables

<script>
if (true) {
var x = 10;
let y = 20;
}
console.log(x); // 10 (accessible because var is function-scoped)
console.log(y); // ReferenceError: y is not defined (y is block-scoped)

</script>
