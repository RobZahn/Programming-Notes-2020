# [API](https://en.wikipedia.org/wiki/Application_programming_interface)

API stands for Application Programming Interface. An API is an interface or communication protocol between different parts of a computer program intended to simplify the implementation and maintenance of software.

An API may be for a web-based system, operating system, database system, computer hardware, or software library.

## Web APIs
Generally communicate via HTTP

* Twitter API - Give me all the tweets that mention 'ice cream'
* Facebook API - Send me the current user's profile picture
* Weather API - what is the weather in Missoula Montata?
* Reddit API - what is the current top post?
* GooglePlaces API - what gas stations are near the user?
* Yelp API - give me 10 restaurants in the zipcode 94110

---

<br>

## JSON & XML

APIs don't respond with HTML. HTML contains information about the structure of a page. APIs respond with data not structure; they use simpler data formats like XML and JSON.

### [JSON](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Objects/JSON) - JavaScript Object Notation

JSON looks exactly like JavaScript objects but everything is a string. JSON is far more popular than XML today because of the prevalence of JS on the web. Note that keys are wrapped in quotes.

```javascript
{
    "person": {
        "age": "21",
        "name": "Travis",
        "city": "Los Angeles"
    }
}
```

### [XML](https://developer.mozilla.org/en-US/docs/Web/XML/XML_introduction) - Extensible Markup Language

XML is syntacticly similar to HTML but it does not describe presentation like HTML does.

```xml
<person>
    <age>21</age>
    <name>Travis</name>
    <city>Los Angeles</city>
</person>
```

<br>

## Making an API Request in Node.js

To make a request for an API, we need to install a package like [request](https://github.com/request/request). The basic syntax for the request library looks like this:

```javascript
const request = require('request');

request('http://www.google.com', function (error, response, body) {
    // Print the error if one occurred
    console.error('error:', error); 
    // Print the response status code if a response was received
    console.log('statusCode:', response && response.statusCode);
    // Print the HTML for the Google homepage.
    console.log('body:', body); 
});
```

When we make a request for an API, the body of the response that is sent back is a String. We need to convert it to JSON using [JSON.parse](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/parse) before we can access it.

```javascript
request('https://apiurl.com', function(error, response, body) {
    if (!error && response.statusCode == 200) {
        const parsedData = JSON.parse(body); 
        //by default, the body will be a String. JSON.parse turns it into
        //a JSON object so we can key into it.
    }
});
```