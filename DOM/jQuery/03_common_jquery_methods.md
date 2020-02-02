# Common jQuery Methods

* [text()](https://api.jquery.com/text/) - Get the combined text contents of each element in the set of matched elements, including their descendants, or set the text contents of the matched elements. (*Works like textContent in vanilla JS.*)

```html
<h1>I am an h1!</h1>

<ul>
    <li>Skittles</li>
    <li>Starburst</li>
    <li>Twix</li>
</ul>
```

```javascript
$('ul').text() //'Skittles Starburst Twix'

$('h1').text('New Text!')
$('h1').text() // 'New Text!'
```
<br>

* [html()](https://api.jquery.com/html/) - Get the HTML contents of the first element in the set of matched elements or set the HTML contents of every matched element. (*Works like innerHTML in vanilla JS.*)

```javascript
$('ul').html(); //<li>Skittles</li> <li>Starburst</li> <li>Twix</li>

$('ul').html('<li>I hacked your UL!</li>')
```
<br>

* [attr()](https://api.jquery.com/attr/) - Get the value of an attribute for the first element in the set of matched elements or set one or more attributes for every matched element.

```html
<img src="https://i.imgur.com/some_picture.jpg">
```

---

```javascript
$('img').attr('src') // "https://i.imgur.com/some_picture.jpg"

$('img').attr('src', 'https://i.imgur.com/another_picture.jpg') //changes img src
```
<br>

* [val()](https://api.jquery.com/val/) - Get the current value of the first element in the set of matched elements or set the value of every matched element.

```html
<input type="text">
```

```javascript
$('input').val(); //gets the value that was typed into a text input

$('input').val('someUsername') //sets the value of a text input
```
---

* [addClass()](https://api.jquery.com/addClass/)
* [removeClass()](https://api.jquery.com/removeClass/)
* [toggleClass()](https://api.jquery.com/toggleClass/)

These methods work just like .classList.add/remove/toggle in vanilla JS. We can pass more than one argument to add/remove/toggle multiple classes at once.

```javascript
$('h1').addClass('demoClass') //adds demoClass to the h1

$('h1').removeClass('demoClass') //removes demoClass from the h1

$('h1').toggleClass('demoClass') //toggles demoClass on/off the h1
```