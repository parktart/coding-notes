# React

## Intro





## Components

Applications built with React are made with (reusable) components. Components are your “building blocks.” To gain confidence using React, you should learn to divide your application or project into these separate components.

For example, a simple website could be divided into the following components:

- `App` - your main application and the parent of all other components
- `Navbar` - navbar component
- `MainArticle` - main content component
- `NewsletterForm` - user input component



In React, each component is defined in an ES6 (ECMAScript 2015) module. ES6 introduced the `import` statement which allows you to import code from one module into another module. This allows us to write each component in a separate file and import all components into the parent component like so:

```jsx
// App.js
import ExampleComponent from "./components/ExampleComponent"
```

React components, in general, usually have parent and/or child components. This system of structuring your applications helps to keep your code organized.



#### Class Components

```jsx
import React, { Component } from 'react'

class App extends Component {
    constructor() {
        super()
    }

    {/* Javascript functions can be written here */}

    render() {
        return (
            <div className="App">
            Hello World!
            </div>
        )
    }
}

export default App
```

let's break this down..

```jsx
import React, { Component } from 'react'
```

Import React and React's 'Component' class from the React library.
Default exports are imported without curly brackets; everything else must be wrapped in curly brackets.

```jsx
class App extends Component {
```

This gives our App component all of the fun methods and properties every React component should have.

Note React components, like all classes and object constructors, should always be declared with a capital letter at the beginning (PascalCase)

```jsx
{/* Javascript functions can be written here */}
```

In React, you write comments within curly brackets and /* */

```jsx
render() {
    return (
        <div className="App">
        Hello World!
        </div>
    )
}
```

This looks like HTML, but is actually **JSX**. 

JSX is an HTML-like syntax that is "transpiled" (or converted) into JavaScript so a browser is able to process it

Note in JSX you can't use some JavaScript protected words as html attributes, and instead..

`class` = `className`

`onchange` = `onChange`

`for` = `htmlFor`

All attributes in JSX are written in camelCase and some have their names changed completely

The `render()` function is the most used React "lifecycle" function.

Every React class component needs a render function, which returns *one* top-level JSX element.

```jsx
// BAD - will throw an error!
render() {
    return (
        <h1>Hello world</h1>
        <h2>Welcome to my React page!</h2>
    )
}

// GOOD
render() {
    return (
        <div>
            <h1>Hello world</h1>
            <h2>Welcome to my React page!</h2>
        </div>
    )
}
```



So that we can reuse our component in other files of our project, we export the component..

```jsx
export default App;
```



#### Functional Components

Declaring a component using functional, rather than class, syntax, is the more modern approach to defining components

```jsx
import React from 'react';

function App() {
  return <div className="App">Hello World!</div>;
}

// OR (arrow-function syntax)

const App = () => {
  return <div className="App">Hello World!</div>;
};

// OR (implicit return)

const App = () => <div className="App">Hello World!</div>;

export default App;
```

with functional components..

1. You don't have to import and extend "Component" from React
2. You don't need a constructor.
3. You don't need the render function, instead we put the return statement right at the end of the function body.



## Create-react-app

Developers at Facebook came up with a great tool called `create-react-app`, which sets up a complete React application for you. By running one command, it does all the necessary setup and configuration for you to immediately start working on your project.

Create React App is recommended by the React community for building single-page applications (SPAs)

`npx create-react-app my-app`

`npm start` launches the app



create-react-app..

- abstracts away the complex configurations that come with creating a new React project
- comes with a built-in development server that allows you to see changes in real time as you make them
- includes a comprehensive set of development tools, such as linting and testing, out-of-the-box



#### index.js

`index.js` is the "entry point" of your application by default

```jsx
const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>
);
```

In short, this line of code tells React to render the App component into the DOM, and more specifically, into the element with the id "root" (which you'll find in the created index.html file).



#### index.html

is ultimately the main file served on the browser



#### manifest.json

This is a web app manifest describes your application, and it's used by mobile devices if a shortcut is added to the home screen

The metadata in `manifest.json` determines what icons, names, and branding colors to use when the web app is displayed on someone's favorites or home screen in say Google Chrome, on Android or Safari on iOS

Basically, the information read from this file is used to populate the web app’s icons, colors, names, etc.



#### Webpack and Bundled Scripts

Think of webpack as a tool that bundles up all your source files and creates a single `bundle.js` file that can be served from the `index.html` file inside a `<script>` tag in the `<body>` element

This reduces the number of HTTP requests made within the app which improves performance

All your `js` files (react components) will be bundled into `bundle.js` using webpack

the configuration for how webpack will bundle your `js` files can be found here:

` .\node_modules\react-scripts\config\webpack.config.js`



#### Hot Module Replacement (HMR)

In a create-react-app project, Hot Module Replacement (HMR) is automatically enabled during development by default.

Hot Module Replacement (HMR) is a feature in webpack to inject updated modules into the active runtime.

With a browser reload, the state of your application will be reset, meaning you will have to redo any process or changes to get back to the state you were viewing.

With HMR, the reload is avoided. HMR allows you to exchange, add, or remove JavaScript modules and CSS while the application is still running, all without having to reload the browser.



#### package.json

This file, along with `package-lock.json` lists the packages your project depends on and which versions of a package your project can use.

This makes your build reproducible and, therefore, easier to share with other developers.

The `scripts` field is of particular interest here. The `start`, `build`, `test`, and `eject` commands point to react-scripts' version of `start`, `build`, `test`, and `eject`. This specifies that when you run `npm` commands like `npm start`, it will actually run `react-scripts start`

react-scripts is a set of scripts from the Create React App starter pack. `react-scripts start` sets up the development environment and starts a server, as well as convenient development features such as hot module reloading









ok
