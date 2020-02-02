# DOM Events

### Events are everywhere:
* Clicking on a button
* Hovering over a link
* Dragging and Dropping
* Pressing the Enter key

---
## The Process

We select an **element** and then add an [EventListener](https://developer.mozilla.org/en-US/docs/Web/API/EventListener).

Elements can listen for keystrokes, mouse hovers, clicks, and scrolls, and more. When the EventListener hears a
corresponding action, some JavaScript code is executed.

---

## The Syntax

To add a listener we use a method called [addEventListener](https://developer.mozilla.org/en-US/docs/Web/API/EventTarget/addEventListener). It takes two arguments: 

1. the type of event we are listening for 
2. the code that will run when that event happens.

```javascript
    element.addEventListener(type, functionToCall);
```

```javascript
    const button = document.querySelector("button");
    button.addEventListener("click", function() {
        console.log("SOMEONE CLICKED THE BUTTON!")
    })
```

