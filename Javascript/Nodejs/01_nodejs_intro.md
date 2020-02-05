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

After installing a package, a file called package.json is created that contains all of the metadata associated with a given package, including all the dependencies that a package requires to work.