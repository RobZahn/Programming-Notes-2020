# [Node.js](https://nodejs.org/en/docs/) & [Express](https://expressjs.com/)

## Basic Shell Commands
* node - Starts the node REPL.
* .exit or  ctrl+z (x2) - Closes the node REPL.
* node \<filename\> - Run a JS file.

---

## Node Package Manager

Interface for installing and managing JS libraries server-side.

* npm install \<packageName\> - Install a package.

* require("\<packageName\>") - Include a package.

* npm init - Creates a new package.json file.

* npm install \<packageName\> --save - Installs package and adds it to the package.json as a dependency.

>NB - After installing a package, a file called package.json is created that contains all of the metadata associated with a given package, including all the dependencies that a package requires to work.

---

[Nodemon](https://github.com/remy/nodemon#nodemon) - nodemon is a tool that helps develop node.js based applications by automatically restarting the node application when file changes in the directory are detected.

nodemon - Instead of running node \<app name>, run nodemon for automatic server updates. The file that will run is whatever is assigned to "main" in the package.json. So if app.js is assigned to "main", nodemon will run that file.

---

## [Basic Routing](https://expressjs.com/en/starter/basic-routing.html)

\* - Splat route matcher will act as a catch-all for requests that are sent to routes that have not been defined. Useful if you want an error page that will display to a user if they try to access a route that is not defined. NB - If the splat route matcher comes first in the list of routes, no other routes will be accessible; route order is very important.

<br>

### Route Order

When a get request is sent, express will evaluate all possible routes in the order they are defined in the main app.js file. Once a match is found, that is the code that will be executed.

### Route Parameters

We can use parameters to define a pattern in a route that doesn't have to be matched word for word or character for character.

```javascript
//The colons : placed before strings act as a sort of wildcard.
app.get('/r/:subredditName/comments/:id/:title/' function(req, res) {
    res.send('Welcome to the comments page')
})
```

The req (request) argument will be an object containing all of the data passed in with the request. req.params will return a list of all of the params entered via the query string.

<br>

## View Templates & EJS

[res.render()](https://expressjs.com/en/api.html#res.render) - Renders a view and sends the rendered HTML string to the client. The argument must exist within the /views directory - express will look here for the file.

To pass a local variable from app.js to a view, that variable must be passed in as an object. See below:

```javascript
// send the rendered view to the client
res.render('index')

// if a callback is specified, the rendered HTML string has to be sent explicitly
res.render('index', function (err, html) {
  res.send(html)
})

// pass a local variable to the view
res.render('user', { name: 'Tobi' }, function (err, html) {
  // ...
})

//pass a variable that we get from the params:
app.get('/fallinlovewith/:thing', function(req, res) {
	const thing = req.params.thing;
	res.render('love.ejs', { thingVar: thing });
});
```
<br>

Express uses [ejs](https://ejs.co/#docs) embedded javascript templates, just like how Rails uses embedded ruby erb templates. 

>Note that we need to install ejs independently using npm install ejs --save.


><%= %> - Renders the value of the returned JS to the page as HTML.
>
><% %> - Runs the code without printing to the page.

<br>

To tell express that we want to use EJS ahead of time, include the following in the app.js file:

```javascript
app.set('view engine', 'ejs')
```

This will save us from having to specify .ejs when setting up our routes.

```javascript
app.get('/', function(req, res) {
    res.render('home'); //no longer need to specify .ejs extension
});
```

---

## Styles & Partials

>NB - CSS files are conventionally kept in the /public directory. By default, express only serves files from the /views directory. To tell express to serve the contents of another directory, include the following within the app.js file:

```javascript
//argument refers to the directory we want access to
app.use(express.static('public'));
```

Partials are template files that we can include in other templates to keep code DRY. They are conventionally kept in /views/partials. Typically we want two partial files to contain our HTML boilerplate like so:

```html
<!-- header.ejs -->
<!DOCTYPE html>
<html>
    <head>
        <title>
        <link rel="stylesheet" href="/app.css">
    </head>
    <body>

    <!-- Note we are using /app.css and not just app.css. If we omit the /, express will look for the stylesheet in the same directory as the view and it will not be able to find it -->
```

```html
<!-- footer.ejs -->
    </body>
</html>
```

To include partials in a view:

```html
<%- include('partials/header') %>

<!-- HTML CONTENT -->

<%- include('partials/footer')%>
```

## Post Requests

```javascript
app.post('/friends', function(req, res) {
    //req.body is an object containing the body of the request form
    console.log(req.body); 
})
```

Without the package body-parser, req.body would be undefined. Body-parser is included as a dependency in express 4.16+. It needs to be required in app.js:

```javascript
const bodyParser = require('body-parser');

app.use(bodyParser.urlencoded({ extended: true }));
```

The [redirect](http://expressjs.com/en/5x/api.html#res.redirect) keyword can be used in place of send or render. It redirects to the URL derived from the specified path, with specified status, a positive integer that corresponds to an HTTP status code . If not specified, status defaults to “302 “Found”.