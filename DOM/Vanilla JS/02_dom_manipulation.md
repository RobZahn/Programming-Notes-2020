# DOM Manipulation

* changing an element's style
* adding/removing classes
* changing the content of a tag
* changing attributes(src, href, etc.)

---
<br>

## Style
The [style](https://developer.mozilla.org/en-US/docs/Web/API/HTMLElement/style) property is one way to manipluate the element's style. When the DOM is constructed an object is made for every single HTML element. Each object has a style property which is a huge object with hundreds of its own properties. We can alter the CSS properties of an element by calling methods that are built into the style property.

```javascript
    //SELECT
    const tag = document.getElementById('highlight');

    //MANIPULATE
    tag.style.color = "blue";
    tag.style.border = "10px solid red";
    tag.style.fontSize = "70px";
    tag.style.background = "yellow";
    tag.style.marginTop = "200px";

    //NB - The value must be formatted as a string!
```
---

<br>

## Separation of Concerns

![Separation of Concerns](https://i.imgur.com/bk3Me.jpg)

>It is recommended for styles to be defined in a separate file for files. The style property allows for quick styling for example for testing purposes. -MDN

<br>

Rather than directly manipulating style with JS, it is usually preferable to define a CSS class and then toggle it on or off with JS.

```javascript
    //INSTEAD OF THIS:
    const tag = document.getElementById("highlight");
    tag.style.color = "blue";
    tag.style.border = "10px solid red";
```

```css
    /*DEFINE A CLASS IN CSS*/
    .some-class {
        color: blue;
        border: 10px solid red;
    }
```

```javascript
    const tag = document.getElementById("highlight");

    //ADD THE NEW CLASS TO THE SELECTED ELEMENT
    tag.classList.add("some-class")
```
<br>

[Element.classList](https://developer.mozilla.org/en-US/docs/Web/API/Element/classList) - Read-only list that contains the classes for a given element. It is **NOT** an array.

```css
    .another-class {
        color: purple;
        font-size: 76px;
    }
```
```javascript
    const tag = document.querySelector("h1")

    //ADD A CLASS TO THE SELECTED ELEMENT
    tag.classList.add("another-class");

    //REMOVE A CLASS
    tag.classList.remove("another-class");

    //TOGGLE A CLASS
    tag.classList.toggle("another-class")

```
<br>

[Node.textContent](https://developer.mozilla.org/en-US/docs/Web/API/Node/textContent) - Returns a string of all the text contained in a given element.

```html
    <p>This is an <strong>awesome</strong> paragraph.</p>
```

```javascript
    //Select the <p> tag:
    const tag = document.querySelector("p");

    //Retrieve the textContent:
    tag.textContent //"This is an awesome paragraph"

    //alter the textContent:
    tag.textContent = "blah blah blah";
```
<br>

[innerHTML](https://developer.mozilla.org/en-US/docs/Web/API/Element/innerHTML) - Similar to textContent, except it returns a string of all the HTML contained in a given element.

```html
    <p>This is an <strong>awesome</strong> paragraph.</p>
```

```javascript
    //Select the <p> tag:
    const tag = document.querySelector("p")

    tag.innerHTML //"This is an <strong>awesome</strong> paragraph"

```
<br>

## Manipulating Attributes
---

Use [getAttribute()](https://developer.mozilla.org/en-US/docs/Web/API/Element/getAttribute) and [setAttribute()](https://developer.mozilla.org/en-US/docs/Web/API/Element/setAttribute) to read and write attributes like *src* or *href*.

```html
    <a href="www.google.com">I am a link</a>
    <img src="logo.png">
```

```javascript
    const link = document.querySelector("a");
    link.getAttribute("href"); //"www.google.com"
    
    //CHANGE HREF ATTRIBUTE
    link.setAttribute("href", "www.dogs.com");
    //<a href="www.dogs.com">I am a link</a>

    //TO CHANGE THE IMAGE SRC
    const img = document.querySelector("img");
    img.setAttribute("src", "corgi.png");
    //<img src="corgi.png">
```