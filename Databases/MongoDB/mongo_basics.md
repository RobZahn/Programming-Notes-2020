# MongoDB Introduction

>IMPORTANT: **Never ever commit/push a file containing the MongoDB connection string to Github or anywhere else.** Anyone with access to this string can make changed to the database and it contains the plain text username and password. Always git ignore the file that contains this code!!!!!


* The Mongo connection string should be placed within \<root\>/config/keys.js.
* Add a file called .gitignore to the project.
* Within this file, list all the files to be ignored by git.

```javascript
// within keys.js

module.exports = {
    mongoURI: "mongodb://..."
}

// within .gitignore

/node_modules
keys.js
etc...
```
---

## Basic Mongo Commands

* mongod - Starts Mongo daemon.

* mongo - Starts Mongo shell.

* help - Lists basic features of Mongo.

* show dbs - Lists available DB's. 

* use \<name_of_db\> - Uses the specified DB or creates a new one if it does not exist.

* show collections - Shows available collections within the chosen DB.

* insert() - Inserts data into the specified collection within the chosen DB. Ex: db.dogs.insert({name: "Rusty", breed: "Mutt"})

* find() - Queries the DB. Ex: db.dogs.find() returns all objects within the dogs collection. db.dogs.find({name: "Rusty"}) returns all dogs with the name Rusty.

* update() - Updates the specified item. Takes two arguments: the first is the selection and the second is the edited data. Ex. db.dogs.update({name: "Rusty"}, {$set: {breed: "Poodle"}}) 

    >NOTE - $set prevents overwriting other data within the object. If we ONLY want to change breed, we need to use $set.

* remove() - Destroys the specified object(s) from a collection. Ex. db.dogs.remove({breed: "Poodle"}) By default it will remove all objects that match the specified attribute.

    >NOTE - .limit() will limit the number of matching objects to be destroyed. Ex. db.dogs.remove({breed: "Poodle"}).limit(1) will remove only the first matching object

* db.collection.drop() - Drops the specified collection from the DB.

> db.dogs.drop() removes the entire dogs collection.

---

## [Mongoose](https://mongoosejs.com/)

Mongoose is a schema-based solution to model your application data. It includes built-in type casting, validation, query building, business logic hooks and more, out of the box.

Mongoose is a tool that helps us interact with MongoDB from within JS files. Install it as a package using NPM.

Mongoose must be required in app.js. The Mongo connection string must also be required in app.js. 

```javascript
const mongoose = require('mongoose');
const db = require('./config/keys').mongoURI;
```

To connect Mongoose to the DB, we need to explicitly do so in app.js using the connect keyword. connect() takes two arguments: the first is the mongoURI and the second is a configuration object. Connect returns a promise. [useUnifiedTopology and useNewUrlParser must both be present and set to true to avoid deprecation errors.](https://mongoosejs.com/docs/deprecations.html)

```javascript
mongoose
	.connect(uri, { useUnifiedTopology: true, useNewUrlParser: true })
	.then(() => console.log('Connected to mongoDB'))
	.catch((err) => console.log(err));
```

### Schemas

[Schemas](https://mongoosejs.com/docs/guide.html) are useful even in the context of a non-relational database like MongoDB. To create a schema with Mongoose, we use new mongoose.Schema() and pass in an object of key value pairs.

```javascript
const catSchema = new mongoose.Schema({
	name: String,
	age: Number,
	temperament: String
});
```

We can then create a model based on the schema like so:

```javascript
const Cat = mongoose.model('Cat', catSchema);
```

New instances of the model can be created by using new \<modelName\>. With MongoDB, we have the freedom of adding additional key value pairs to any given model or even omitting the default pairs from the schema.

```javascript
let george = new Cat({
	name: 'George',
	age: 11,
	temperament: 'Grouchy'
});
```

To save an instance to the database we use .save(). This method takes a callback function that takes in a potential error as the first argument and a variable name as the second argument.

```javascript
george.save(function(err, cat) {
	if (err) {
		console.log('Something went wrong.');
	} else {
		console.log('We just saved a cat to the DB.');
		console.log(cat);
	}
});
```

To query the database, we use .find(). It takes two arguments: the first being an object with the search filter and the second being the same callback function that .save() takes. If the search filter object is empty, the return will be a list of ALL the items in the given collection (_all of the cats in our cats collection, for instance._)

```javascript
Cat.find({}, function(err, cats) {
	if (err) {
        console.log('Something went wrong.');
        console.log(err)
	} else {
        console.log("All the cats!")
		console.log(cats);
	}
});
```

We can create a new instance and save it to the DB simultaneously by using .create().

```javascript
Cat.create({
	name: 'Snow White',
	age: 15,
	temperament: 'Nice'
}, function(err, cat) {
    if (err) {
        console.log(err);
    } else {
        console.log(cat);
    }
});
```