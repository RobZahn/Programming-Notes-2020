# jQuery Basics

## Adding jQuery

1. Download jQuery and link to it locally:

```html
<script type="text/javascript" src="jquery.js"></script>
```

2. Link to a **CDN** (*Content Distributed Network* - a hosted copy)

```html
<script 
    type="text/javascript" 
    src="https://code.jquery.com/jquery-2.1.4.js">
</script>
```
<br>

## Syntax Preview

```javascript
//when a user clicks the button with id 'trigger'
$('#trigger').click(function() {

    //change the body's background to yellow
    $('body').css('background', 'yellow');

    //fade out all imgs over 3 seconds
    $('img').fadeOut(3000, function() {

        //remove imgs from page when fadeOut is done
        $(this).remove();
    });
});
```

