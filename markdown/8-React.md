# React

## Intro





## Create-react-app

Developers at Facebook came up with a great tool called `create-react-app`, which sets up a complete React application for you. By running one command, it does all the necessary setup and configuration for you to immediately start working on your project.

Create React App is recommended by the React community for building single-page applications (SPAs)

`npx create-react-app my-app`

`npm start` launches the app



create-react-app..

- abstracts away the complex configurations that come with creating a new React project
- comes with a built-in development server that allows you to see changes in real time without a browser refresh
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

In short, this line of code tells React to render the App component into the DOM, and more specifically, into the element with the id "root" (which you'll find in the index.html file)



#### index.html

is ultimately the main file served on the browser



#### manifest.json

This is a web app manifest that describes your application, and may be used by mobile devices or in other places

The metadata in `manifest.json` determines what icons, names, and branding colors to use when the web app is displayed on someone's favorites or home screen in say Google Chrome on Android, or Safari on iOS

Basically, the information read from this file is used to populate the web app's icons, colors, names, etc.



#### Webpack and Bundled Scripts

A create-react-app project comes with webpack configured

Think of webpack as a tool that bundles up all your `js` source files and creates a single `bundle.js` file that can be served from the `index.html` file inside a `<script>` tag within the `<body>` element

This reduces the number of HTTP requests made within the app, which improves performance

All your `js` files (react components) will be bundled into `bundle.js` using webpack

the configuration for how webpack will bundle your `js` files can be found here:

` .\node_modules\react-scripts\config\webpack.config.js`



#### Hot Module Replacement (HMR)

A create-react-app project comes with Hot Module Replacement (HMR) enabled by default (for developement).

Hot Module Replacement (HMR) is a feature in webpack to inject updated modules into the active runtime.

With a browser reload, the state of your application will be reset, meaning you will have to redo any process or changes to get back to the state you were viewing.

With HMR, the reload is avoided. HMR allows you to exchange, add, or remove JavaScript modules and CSS while the application is still running, without having to reload the browser.



#### package.json

This file, along with `package-lock.json` lists the packages your project depends on and which versions of a package your project can use.

This makes your build reproducible and, therefore, easier to share with other developers.

The `scripts` field is of particular interest here. The `start`, `build`, `test`, and `eject` commands point to react-scripts' version of `start`, `build`, `test`, and `eject`. This specifies that when you run `npm` commands like `npm start`, it will actually run `react-scripts start`

react-scripts is a set of scripts from the create-react-app starter pack. `react-scripts start` sets up the development environment and starts a server, as well as convenient development features such as hot module reloading

if you clone a repository, use `npm install` to install all the required dependencies listed in `package.json`

or, if the cloned repo contains a `package-lock.json` file, and you want to respect the exact versions specified, use `npm ci` (clean install) instead of `npm install`



#### Adding CSS

The `index.css` file provides a global CSS scope for your entire application. It is intended for defining global styles that apply to your entire application, such as font families, base styles, or CSS resets.

The `App.js` component is typically the root component of your application, and `App.css` provides styles specifically for this component and its children.

It is up to you to add site-wide `css` to either `index.css` or `App.css` - I will use `App.css`

beyond that it is best practice to make a `.css` file for each component that needs individual styling

But create-react-app by default injects all `css` into the DOM in `<style>` tags..

So, by default, all CSS rules are scoped globally for the entire React application.



#### CSS Modules

To create component-scoped css files, we can use **CSS Modules**, which come preconfigured with create-react-app..

CSS file names will include 'module' like `MyComponent.module.css`

```css
.main {
  background-color: black;
  color: white;
  text-align: center;
}
```

and import it into your component..

```jsx
import styles from "./MyComponent.module.css";

function MyComponent() {
  return <div className={styles.main}>Hello</div>;
};

export default MyComponenet;
```

note global styles will still be applied to these elements unless overwritten in the `.module.css` file with a more specific selector

and because CSS modules use only *class selectors* for selecting elements to style - you cannot style using element selectors like `p` in a `.module.css` file

It's kind of a mess, so use Sass and Bootstrap, detailed below.



#### Sass (.scss)

beyond CSS Modules, you can use a CSS Preprocessor like Sass (SCSS)

Sass (SCSS): Sass (or SCSS) is a widely used CSS preprocessor that provides features like variables, nesting, mixins, and more. It allows you to write modular and reusable styles. Create React App supports Sass out of the box, so you can use `.scss` files and leverage Sass features.

[About scss](https://www.robinwieruch.de/create-react-app-with-sass-support/)



#### Bootstrap

beyond `scss` you can use Bootstrap (learn Bootstrap and `bootstrap/scss`)





## Components

Applications built with React are made with reusable components. A component is a piece of the UI that has its own logic and appearance.

Components are your "building blocks". A component can be as small as a button, or as large as an entire page. To gain confidence using React, you should learn to divide your application or project into these separate components.

For example, a simple website could be divided into the following components:

- `App` - your main application and the parent of all other components
- `Navbar` - navbar component
- `MainArticle` - main content component
- `NewsletterForm` - user input component



In React, each component is defined in an ES6 (ECMAScript 2015) module. ES6 introduced the `import` statement which allows you to import code from one module into another. This allows us to write each component in a separate file and import all components into the parent component like so:

```jsx
// App.js
import ExampleComponent from "./components/ExampleComponent"
```

React components, in general, usually have parent and/or child components. This system of structuring your applications helps to keep your code organized.



### Class Components

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

Note React components, like all classes and object constructors, should be named in PascalCase

By using PascalCase, you can easily distinguish components from regular HTML elements or variables in JSX.

In fact, in JSX, lowercase elements are treated as HTML tags, and a lowercase React component won't render correctly!

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

Note in JSX we can't use some of the normal html attribute names, such as `class`, because they are JavaScript-protected words, and instead..

`class` = `className`

`onchange` = `onChange`

`for` = `htmlFor`

All attributes in JSX are written in camelCase and some have their names changed completely

The `render()` function is the most used React "lifecycle" function

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

// OR CAN USE
render() {
    return (
        <>
            <h1>Hello world</h1>
            <h2>Welcome to my React page!</h2>
        </>
    )
}
// which avoids adding an extra div to the DOM (<> is called a Fragment here)
```



So that we can re-use our component in other files of our project, we export the component..

```jsx
export default App;
```



### Functional Components

Declaring a component using functional, rather than class, syntax is the more modern approach to defining components

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
2. You don't need a constructor
3. You don't need the render function, instead we just put the return statement at the end of the function body



NOTE starting from React v17, you actually don't need to explicitly import the React module in files that contain React components. So the `import React from 'react'` line is no longer needed!

And to avoid including `export default XXX` you can use the syntax..

```jsx
// no import needed

export default function App() {
  return <div className="App">Hello World!</div>;
}

// no export needed
```

This syntax comes in handy when you want to define multiple components in the same file - which you may want to do if components are relatively small or tightly related to each other.

```jsx
export default function Gallery() {
  return (
      <>
          <Profile />
          <Profile />
          <Profile />
      </>
  );
}

function Profile() {
  // code
}
```



## JSX

JSX is a syntax extension for JavaScript that lets you write HTML-like markup inside a JavaScript file.

JSX is different from HTML in quite a few ways, including being 'more strict'

Note in JSX..

1. you must return a single root element
2. all tags must be closed - self-closing tags like `<img>` become `<img/>` in JSX
3. element attribute names follow the same naming conventions as JavaScript variables (should be camelCase, etc)
4. it's recommended to use "double quotes" for HTML attributes and 'single quotes' for JavaScript within the JSX code



JSX turns into JavaScript and attributes written in JSX become keys of JavaScript objects. You'll notice the JSX element attribute names correspond to the JavaScript object properties you are already familiar with (like `className` and `style`)



#### Displaying Data

JSX lets you put markup into JavaScript. 

Curly braces allow you to "escape back" into JavaScript

for example to embed a variable and display it to the user..

```jsx
return (
  <h1>Welcome {user.name}!</h1>
);
```

or for an html attribute..

```jsx
return (
  <img
    className="avatar"
    src={user.imageUrl}   // note no "quotes"!
  />
);
```

with more complex expressions..

```jsx
return (
    <img
      className="avatar"
      src={user.imageUrl}
      alt={'Photo of ' + user.name}   // concatenation
    />
  );
```



#### Conditional Rendering

render a Welcome screen or LoginForm depending on `user.isLoggedIn`

```jsx
const user = {
    name: "Parker",
    age: 27,
    isLoggedIn: true
};

function App() {
    let content;
    if (user.isLoggedIn) {
        content = <Welcome user={user} />;
    } else {
        content = <LoginForm />;
    }
  
    return (
        <div>
            {content}
        </div>
    );
}
```

with javascript ternary operator syntax..

```jsx
function App() {
    return (
        <div>
            {user.isLoggedIn
                ? ( <Welcome user={user} /> )
                : ( <LoginForm /> )
            }
        </div>
    );
}
```

or if you don't need the `else` branch..

```jsx
function App() {
    return (
        <div>
            {user.isLoggedIn && <Welcome user={user} />}
        </div>
    );
}
```



#### Rendering Lists

You will rely on JavaScript `for` loops and `array.map()` to render lists of components

```jsx
// Items.js

const items = [
    { title: 'Cabbage', id: 1 },
    { title: 'Garlic', id: 2 },
    { title: 'Apple', id: 3 },
];

function Items() {
    const listItems = items.map(item =>
        <li key={item.id}>
            {item.title}
        </li>
    );

    return (
        <div>
            <h3>Your items:</h3>
            <ul>{listItems}</ul>
        </div>
    );
}

export default Items;
```

Notice how `<li>` has a `key` attribute. 

For each item in a list, you should pass a string or a number that uniquely identifies that item among its siblings. 

Usually, the key should come from your data, such as a database ID. 

React uses your keys to know what happened if you later insert, delete, or reorder the items.



#### Responding to events

You can respond to events by declaring *event handler* functions inside your components:

```jsx
function MyButton() {
  const  handleClick = () => {
    alert('You clicked me!');
  }

  return (
    <button onClick={handleClick}>
      Click me
    </button>
  );
}
```

Notice how `onClick={handleClick}` has no parentheses at the end! Do not *call* the event handler function: you only need to *pass it down*. React will call your event handler when the user clicks the button.

As opposed to vanilla `html/js` which would be..

```html
<button onclick="handleClick( )">
  Click me
</button>

<script>
  function handleClick() {
    alert('You clicked me!');
  }
</script>
```



## Hooks

Functions starting with `use` are called *Hooks*.

`useState` is a built-in Hook provided by React.

You can find other built-in Hooks in the [React Docs.](https://react.dev/reference/react)

You can also write your own Hooks by combining the existing ones.

Hooks are more restrictive than other functions. You can only call Hooks within React components, and more specifically *at the top* of your components.

If you want to use `useState` in a condition or a loop, extract a new component and put it there.

Some built-in React Hooks..

`useState` - declares a state variable that you can update directly

`useEffect` - is used to add side effects or perform actions in response to certain events or changes

`useContext` - lets a component receive information from distant parents without passing it as props

`useRef` - lets a component hold some information that isn't used for rendering - refs differ from state in that updating a ref does not re-render your component - most often it's used to hold a DOM node

`useMemo` - can be used to tell React to skip calculations and unnecessary re-rendering if the data has not changed since the previous render



### useState

The `useState` hook is used to add state to functional components. It allows you to declare and manage state variables within your components. The `useState` hook returns an array with two elements: the current state value and a function to update that value.

```jsx
import { useState } from 'react';

function MyComponent() {
  const [count, setCount] = useState(0);

  const increment = () => {
    setCount(count + 1);
  };

  const decrement = () => {
    setCount(count - 1);
  };

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={increment}>Increment</button>
      <button onClick={decrement}>Decrement</button>
    </div>
  );
}

export default MyComponent
```

The `setCount` function can be invoked with a new value, and when invoked, React will re-render `MyComponent` with the updated state.



EXAMPELE:

Let's count the number of times a button is clicked. To do this, we add *state* to a component.

```jsx
import { useState } from 'react';

function NewBtn() {
    const [count, setCount] = useState(0);
  
    function handleClick() {
        setCount(count + 1);
    }

    return (
        <button onClick={handleClick}>
            Times clicked: {count}
        </button>
    );
}

export default NewBtn;
```

```jsx
const [count, setCount] = useState(0);
```

`count` = the current state

`setCount` = the function that lets you update the state

`useState(0)` = the initial state



NOTE React Hooks must be called in a React function component or a custom React Hook. So React Hook `useState` cannot be called at the top level (must be *inside* a component definition)



If you render the same component multiple times, each will get its own state..

```jsx
import Button from './Button';

function App() {
  return (
    <div>
      <h1>Counters that update separately</h1>
      <Button />
      <Button />
    </div>
  );
}

export default App;
```

```jsx
import { useState } from 'react';

function Button() {
    const [count, setCount] = useState(0);

    return (
        <button onClick={() => setCount(count + 1)}>
            Clicked {count} times
        </button>
    );
}

export default Button;
```

Each instance of the Button component has its own count state.

However, if we want the components to display the same `count` and update together, you need to move the state from the individual buttons "upwards" to the closest component containing all of them. In this case, `App`.

```jsx
import { useState } from 'react';
import Button from './Button';

function App() {
  const [count, setCount] = useState(0);
  function increaseCount() {
    setCount(count + 1);
  }
  
  return (
    <div>
      <h1>Counters that update separately</h1>
      <Button count={count} increaseCount={increaseCount} />
      <Button count={count} increaseCount={increaseCount} />
    </div>
  );
}

export default App;
```

```jsx
function Button( {count, increaseCount} ) {
    return (
        <button onClick={increaseCount}>
            Clicked {count} times
        </button>
    );
}

export default Button;
```

The information you pass down like this is called *props*. 

Now the `App` component contains the `count` state and the `increaseCount` event handler, and *passes both of them down as props* to the buttons.

This is called "lifting state up". By moving state up, you've shared it between components.



### useEffect

The `useEffect` hook is used to add side effects or perform actions in response to certain events or changes.

It allows you to incorporate logic that should be executed after the rendering of your components.

You should use it when you need to connect and synchronize a component with an external system. This includes dealing with network, browser DOM, animations, and other non-React code. Effects are an "escape hatch" from the React paradigm - don't use Effects to orchestrate the data flow of your application - if you're not interacting with an external system, you might not need an Effect.

The `useEffect` hook takes two arguments: a callback function and an optional array of dependencies. The callback function is the code you want to execute, and it will be executed after the component has rendered. The dependencies array specifies the values that the effect depends on.

```jsx
import { useEffect } from 'react';

function MyComponent() {
  useEffect(() => {
    console.log('effect used');
  }, [ ]);

  return <div>Hi!</div>;
}

export default MyComponent;
```

When you use the `useEffect` hook with an empty dependency array `[ ]`, the code inside `useEffect` should execute only once during the initial rendering of the component. Subsequent updates to the component, such as re-renders caused by changes in props or state, should not cause `useEffect` to execute again.

If you want the effect to run whenever a specific value changes, you can include that value in the dependency array.

The `useEffect` hook is commonly used for tasks such as fetching data from an API, subscribing to events, setting up timers, manipulating the DOM, or performing clean-up actions when a component is unmounted.

NOTE when React.Strict mode is on.. React renders components twice (in dev but not production) in order to detect and excacerbate the implications of multiple renders - and help you to find bugs earlier





## Props

Props are one of the two major pillars of React, the very heart of what the framework was built on.

Prop is short for *property*, as in javascript object property



















ok
