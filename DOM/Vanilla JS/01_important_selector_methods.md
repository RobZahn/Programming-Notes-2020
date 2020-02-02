# Important Selector Methods

![DOM Chart](https://www.w3schools.com/js/pic_htmltree.gif)

The entire DOM lives inside of the **Document**, which is the top level/root node.


```javascript
    document.URL; //shows URL of page
    document.head; //shows HTML head
    document.body; //shows entire HTML body
    document.links; //list of all a tags
```

The above commands give us access to some of the important properties of the **Document**.

---
<br>

## Built-In Methods

```javascript
    document.getElementById()
    document.getElementsByClassName()
    document.getElementsByTagName()
    document.querySelector()
    document.querySelectorAll()
```
<br>

### Example HTML:

```html
    <body>
        <h1>Hello</h1>
        <h1>Goodbye</h1>
        <ul>
            <li id="highlight">List Item 1</li>
            <li class="bolded">List Item 2</li>
            <li class="bolded">List Item 3</li>
        </ul>
    </body>
```
<br>

[getElementById()](https://developer.mozilla.org/en-US/docs/Web/API/Document/getElementById) - Takes a *string argument* and returns the one element with a matching ID.

```javascript
    const tag = document.getElementById("highlight")

    // returns a JS object representing the HTML <li> element with id="highlight"
```
<br>

[getElementsByClassName()](https://developer.mozilla.org/en-US/docs/Web/API/Document/getElementsByClassName) - Takes a *string argument* and returns a list of elements that have a matching class.

```javascript
    const tags = document.getElementsByClassName("bolded")
    
    // returns a NodeList of JS objects representing the HTML <li> elements with class="bolded"
```
<br>

[getElementsByTagName()](https://developer.mozilla.org/en-US/docs/Web/API/Document/getElementsByTagName) - Takes a *string* argument and returns a list of elements that have a matching HTML tag.

```javascript
    const tags = document.getElementsByTagName("li")
    
    // returns a NodeList of all <li> elements
```
<br>

[querySelector()](https://developer.mozilla.org/en-US/docs/Web/API/Document/querySelector) - Takes a *string* argument and returns the *first element* that matches a given CSS-style selector.

```javascript
    const hightlight = document.querySelector("#highlight")

    const bolded = document.querySelector(".bolded")
    // returns only the first <li> with class="bolded"

    const h1 = document.querySelector("h1")
    // returns only the first <h1>
```
<br>

[querySelectorAll()](https://developer.mozilla.org/en-US/docs/Web/API/Document/querySelectorAll) - Takes a *string* argument and returns a list of all matching elements for a given CSS-style selector.

```javascript
    const allBolded = document.querySelectorAll(".bolded")
    // returns all elements with class="bolded"

    const allH1s = document.querySelectorAll("h1")
    // returns all <h1> elements
```