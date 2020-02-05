# [Node.js](https://nodejs.org/en/docs/)

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

\* - Splat route matcher will act as a catch-all for requests that are sent to routes that have not been defined. Useful if you want an error page that will display to a user if they try to access a route that is not defined. NB - If the splat route matcher comes first in the list of routes, no other routes will be accessible; route order is very important.

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
