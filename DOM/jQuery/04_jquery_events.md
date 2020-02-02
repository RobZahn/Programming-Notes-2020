# jQuery Events

### Common Event Methods

* [click()](https://api.jquery.com/click/) - quickly and easily add a click listener to element(s)

```javascript
//prints when item with id 'submit' is clicked
$('#submit').click(function() {
    console.log("Another Click")
});

//alerts when ANY button is clicked
$('button').click(function() {
    alert("Someone clicked a button")
});

//changes the background color of the clicked button
$('button').click(function() {
    $(this).css("background", "pink")
});
```
<br>

* [keypress()](https://api.jquery.com/keypress/) - quickly and easily add a keypress listener to element(s)

>NB - keydown() and keyup() provide a code indicating which key is pressed, while keypress() indicates which character was entered. For example, a lowercase "a" will be reported as 65 by keydown and keyup, but as 97 by keypress. An uppercase "A" is reported as 65 by all events. Because of this distinction, **when catching special keystrokes such as arrow keys, keydown() or keyup() is a better choice.**

```javascript
//listen for any keypress in any text input
$('input[type="text"]').keypress(function() {
    alert('text input keypress!');
});

//listens for keypress, only executes code if "Enter" is pressed
$('input[type="text"]').keypress(function(event) {
    if(event.which === 13) { // *
        alert("You hit enter!")
    }
});

//* Event objects have a "which" property that points to a key code. Every key on a standard keyboard has a corresponding key code in JS. 13 is the key code for Enter.
```
<br>

* [on()](https://api.jquery.com/on/) - works similarly to addEventListener. Allows us to specify the type of event to listen for. This is the most commonly used event method in jQuery.

```javascript
$('#submit').on('click', function() {
    console.log('Another click!');
});

$('button').on('dblclick', function() {
    console.log('Button double clicked!');
});

$('a').on('dragstart', function() {
    console.log('Drag started!');
});

$('input[type="text"]').on('keypress', function() {
    console.log('Key press in an input!');
});
```