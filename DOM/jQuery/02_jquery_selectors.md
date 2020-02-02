# Selecting with jQuery

## Overview

* Select elements with [$()](https://api.jquery.com/jQuery/)
* Use [.css()](https://api.jquery.com/css/) to style elements

Selecting with jQuery is very similar to *querySelectorAll* in that we provide a CSS style selector and jQuery will return all matching elements.

```javascript
$('selectorGoesHere')

//to select all img tags
$('img')

//to select all elements class 'sale'
$('.sale')

//to select all elements with id 'bonus'
$('#bonus')

//to select all a tags inside of li's
$('li a')
```

<br>

The .css() method is jQuery's interface to styling.

```javascript
//This method takes two arguments.
.css(property, value)

//select element with id 'special' and give it a border
$('#special').css('border', '2px solid red')

//we can also pass in an object with styles
let styles = {
    backgroundColor : 'pink',
    fontWeight      : 'bold'
};

$('#special').css(styles);
```