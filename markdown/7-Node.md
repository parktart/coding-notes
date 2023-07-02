# Node.js

Node.js is a JavaScript runtime environment that allows you to run JavaScript outside of your web browser

often used for web servers, REST APIs, and microservices



a **runtime environment** is where your program will be executed

this determines which global objects your program can access

and can impact how your program runs



there are **two** JavaScript runtime environments..

- the **browser** runtime environment (Chrome, Firefox, etc)
- the **Node** runtime environment



#### Browser Runtime Environment

is the most common place JavaScript code is executed

when you use a browser to open a local `html` file containing a `<script>`..

that script will execute in the browser's runtime environment

which means your program will have access to the `window` object and all of its methods - like `alert` `prompt` etc

applications created for and executed in the browser are known as **front-end applications**

for a long time JavaScript code could only be executed in a browser and was used exclusively for creating front-end applications

in order to create back-end applications that could run on a computer WITHOUT a browser you would need to use other languages such as Java or PHP



#### Node Runtime Environment

in 2009, the Node runtime environment was created for the purpose of executing JavaScript code without a browser, thus enabling programmers to create full-stack (front-end and back-end) applications using only the JavaScript language



Node is open-source

Node executes JavaScript using the V8 JavaScript engine (same as Google Chrome)

Node is an entirely different runtime environment though

meaning that browser-environment data values and functions - like `alert()` - can’t be used

instead the Node runtime environment gives back-end applications access to a variety of features unavailable in a browser

such as access to the server’s file system, database, and network

the Node runtime is commonly used to create **command line tools** and **web servers**



#### Installing Node

`nvm` - Node Version Manager - used to change Node versions and upgrade Node

`nvm ls` for details

`nvm` for more details

[install](https://www.theodinproject.com/lessons/foundations-installing-node-js) (odin)

[docs](https://github.com/nvm-sh/nvm) (github readme)

to tell `nvm` which version of Node to use when we run `node`, use..

```bash
nvm use --lts
```

which in this case tells `nvm` to use the most recent LTS version of Node installed on our computer



`npm` - Node Package Manager - used to install various libraries and tools for JavaScript environments

`npm version` for details



#### Using Node

Node provides an interactive console which lets you run and edit your javascript code right in your terminal

```bash
node  # opens the Node terminal console
```



#### Node Project

`npm` is used to install 3rd party packages - all dependencies required to run a node project are listed in a `package.json` file

`npm init` generates the `package.json` file

`npm install express` installs express (or any package) locally and will update the `package.json` file automatically

`npm install -g express` installs express globally



And so node is so useful because you can utilize all of these modules (also called packages) in building your project

There are three basic types of modules..

1. The "core" node modules - including `path`, `fs`, `http`, etc - do not need to be installed

2. Third-party modules - created by others - installed via npm (like `express`)

3. Custom modules - created by you - used to store functions, variables, objects, classes, etc - created locally



to use any of these module types in our main file we would need to import them using..

```javascript
const path = require('path'); // path is one of the "core" node modules
const myModule = require('./myModule.js'); // a custom module
```



#### Creating A Node Project

so the first thing you do to make it a node project is, inside your project folder..

`npm init`

this will walk you through setting up the project and create the `packages.json` file

now if you `npm install <package>` in your project directory - that dependency will automatically be added to `packages.json`

Note you can declare a module to be a `devDependencies` with the `-D` flag which just distinguishes them from dependencies needed to run the project vs work on it (for developers)

`npm install -D <package>`

for example `nodemon` is a package that reloads the server on save automatically

note the `node_modules` folder holds all the project dependencies and *their* dependencies and so it gets rather large

and if we were going to deploy our project to a host, we wouldn't want to send this huge folder, and so

we can delete the entire `node_modules` folder before we deploy our project

in fact you can do this locally for fun and then just run `npm install` in the project directory to get it back!



or instead, it's probably a good idea to add a `.gitignore` file that contains `node_modules`

so the `node_modules` folder wont be pushed to GitHub!



#### Simple deployment to Render.com

the free trial of Render.com offers very little storage - so APIs will have to be small

build a new web service - select the GitHub repo

Runtime `Node`

Build Command `npm install`

Start Command `node index.js`



ELSE try..

and if you need a database: Railway, Planetscale, CockroachDB

AWS/GCP is the hard mode option for everything



#### Custom Modules

Now we have a main `js` file usually called `index.js` `app.js` or `main.js` and then many other `js` files which are the 'modules'

And we can create custom modules so that our main code doesn't get bloated for example if we wanted to store an object that may get really big we can store it in a seperate `js` file like..

```javascript
// person.js
const person = {
  name: 'John Doe',
  age: 30
}

module.exports = person;
```

and we use `module.exports` so that when `person.js` file is imported into our `index.js` file we will have access to the `person` object

which we import using..

```javascript
// index.js
const person = require('./person.js');
```



note that when a module file like `person.js` is processed by node,

node actually wraps the code in the 'Module Wrapper Function'

```javascript
function (exports, require, module, __filename, __dirname) {
    // person.js
}
```

and so we have access to these parametes in the module file!

which we can see with..

```javascript
// person.js
console.log(__filename) // /home/parker/repos/test/person.js
```



#### Core Modules

to use a node "core" module (see Node docs for info on each one) we simply require them in our file..

```java
// index.js
const path = require('path');
    
console.log(path); // view all methods that come with the path object
```

path, for example, is used to **manipulate path strings** like `/home/parker/repos/test/script.js`

for example we can extract just the filename..

```javascript
console.log(path.basename(__filename)) // script.js
```



lets **make a new directory** called `test` in the current directory utilizing the file-system `fs` "core" module

```javascript
const fs = require('fs');
const path = require('path');

fs.mkdir(path.join(__dirname, 'test'), {}, (err) => {
  if (err) {
    console.error(err);
    return;
  }
  console.log('Directory created successfully!');
});

```



or **create and write to a file**..

```javascript
const fs = require('fs');
const path = require('path');

const content = 'This will be the content';

fs.writeFile(path.join(__dirname, 'test', 'newFile.txt'), content, (err) => {
  if (err) {
    console.error(err);
    return;
  }
  console.log('File created and written successfully!');
});
```

Note that if the file already exists, the `writeFile` method will overwrite its content

If you want to append content to an existing file, use the `fs.appendFile` method instead



and then **read the file**..

```javascript
const fs = require('fs');

fs.readFile('/path/to/newFile.txt', 'utf8', (err, data) => {
  if (err) {
    console.error(err);
    return;
  }
  console.log(data);
});
```



and **work with URLs** - with the first step usually being to take a URL string and make

a URL object to access the indiviual properties..

```javascript
const url = require('url');

const myUrl = url.parse('http://mywebsite.com:5500/hello.html?id=100&status=active');
console.log(myUrl);
```

from this `console.log` you can see the different properties of the URL you can work with



however, since Node v10, a newer method was introduced that does not require the url module

and instead utilizes a URL class to construct a URL object..

```javascript
const url = require('url'); // imports all methods, functions, and classes from the url module

const myURL = new URL('http://mywebsite.com:5500/hello.html?id=100&status=active');
console.log(myURL);
```

this has the added advantage of extracting the search parameters..

```javascript
console.log(myURL.searchParams); // URLSearchParams { 'id' => '100', 'status' => 'active' }
console.log(myURL.searchParams.get('id')); // 100
```



#### Events

**events** is maybe the most important "core" module of Node

side note - a **class**, in JavaScript, is just a template for creating objects that have similar properties and methods

Much of the Node.js core API is built around an idiomatic asynchronous event-driven architecture in which certain kinds of objects (called "emitters") emit named events that cause `Function` objects ("listeners") to be called.

All objects that emit events are instances of the `EventEmitter` class. These objects use a `.on()` function that allows one or more functions to be attached to named events emitted by the object. 

When the `EventEmitter` object emits an event, all of the functions attached to that specific event are called *synchronously*. Any values returned by the called listeners are *ignored* and discarded.

The following example shows a simple `EventEmitter` instance with a single listener. The `.on()` method is used to register listeners, while the `.emit()` method is used to trigger the event.

```javascript
const EventEmitter = require('events'); // here we import the EventEmitter class

// Init object
const myEmitter = new EventEmitter(); // myEmitter is an object of the EventEmitter class

// Event listener
myEmitter.on('event', () => console.log('event fired!'));

// Init event
myEmitter.emit('event');
```



sometimes developers create a class that "extends" the `EventEmitter` class so that they can add

custom methods and properties to the class before using it to make their emitter objects..

```javascript
// Create class
class MyEmitter extends EventEmitter { }; // and then customize this MyEmitter class as desired

// Init object
const myEmitter = new MyEmitter(); // myEmitter is an object of class MyEmitter
```

when an object is created from the `MyEmitter` class, it will have access to all of the properties and methods defined in the `MyEmitter` class, as well as any properties and methods inherited from the `EventEmitter` class



#### Third-Party Modules

you just install them and use them