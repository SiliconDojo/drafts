Javascript Intro
===

# What is Javascript

Javascript is a clientside language that the web browser uses to create interactivity with web apps.

* HTML - Creates the basic frame of the user interface. (Frame or House)
* CSS - Makes the user iterface pretty. (Paint and Siding on House)
* Javascript - Provides interactivity for app. (Dish washer or Garbage Disposal in house) 
* OS - Provides basic systems connectivity for app to connect to network and storage. (Plumbing and Electrical in house)
* Python - Provides backend logic and connectivity to API's (Municiple Water or Electric)
* SQL - Provides the actual storge and retreival of data. (Power Plant or Water Reservior)

**script.html**
```
<button onclick="alert('hello world')">Button</button>
```

```
<script>
  document.write(Date());
</script>
```

## Security

All data is sent to the client and then the client runs the script to determine what the user sees.  The user can either store the text data from the server or simply "show source" in the browser to see all data sent to the browser. Do not send confidential or extraneous data for JavaScript to parse.  Use your backend language to send only the data that is actually needed.

# Embedding Javascript

## <script> tag and src reference

**test.html**
```
<script>
    let message = "hello world";
    document.write(message)
</script>

<script src="script.js"></script>
```

**script.js**
```
document.write(' -- and hello to you too');
```

## Inline Event Handler

```
<button onclick="alert('hello world')">Button</button>
```

# DOM - Document Object Model

The DOM (Document Object Model) allows you to identify and manipulate specfic elements within an HTML document.

There can only be one unique **id** within a document.

Numerous elemenst can shae the same **name**

```
<h1 name="heading" id="title">This is the Title</h1>

<p>Words, words, and some more words</p>

<h2 name="heading" id="next-title">This is another layer</h2>

<p>And more words</p>

<script>
    document.getElementById("title").innerHTML = 'a new message';

    // document.querySelectorAll("p").forEach(function (element) {
    //     element.style.backgroundColor = "green";
    // });

    // document.querySelectorAll('[name="heading"]').forEach(function (element) {
    //     element.style.color = "red";
    // });
</script>
```

# Elements

```
const element = document.getElementById("intro");

const element = document.getElementById("myElement");

const elements = document.getElementsByClassName("myClass");

const elements = document.getElementsByTagName("div");


```

# HTML Properties

```
document.getElementById(id).innerHTML = 'hello world';

document.getElementById("p2").style.color = "blue";

```

# Events
```
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
```

# Variables

Javascript does not have datatypes

**let** and **const** are the current way to declare a variable
```
var x = 1;
let y = 2;
const z = 3;
```


```
<script>
  if (true) {
    var x = 10;
    let y = 20;
  }
  console.log(x); // 10 (accessible because var is function-scoped)
  console.log(y); // ReferenceError: y is not defined (y is block-scoped)
</script>
```

# Concatenation

**Template Literals**

**Note** Backticks not Single Quotation Marks
```
<script>
  let message = 'Hello World';
  document.write(`<h1>${message}</h1>`);
</script>
```

**With +**
```
<script>
  let greeting = 'Hello';
  let message = 'World';
  document.write('<h1>' + greeting + ' ' + message + '</h1>');
</script>
```

## Loops

**For Loop**
```
<script>
    let message = "";
    for (let i = 0; i < 5; i++) {
        message += ("This is iteration number " + i + "<br>");
    }
    document.write(message)
</script>
```

**While Loops**
```
<script>
    let i = 0;
    let message = "";
    while (i < 15) {
        message += ("This is iteration number " + i + "<br>");
        i++;
    }
    document.write(message)
</script>
```

**Do While**
```
<script>
    let i = 0;
    let message = "";
    do {
        message += ("This is iteration number " + i + "<br>");
        i++;
    } while (i < 5);
    document.write(message)
</script>
```
