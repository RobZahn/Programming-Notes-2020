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