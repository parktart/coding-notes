# Test Driven Development TDD



## TDD:

Test Driven Development (TDD) is a phrase you often hear in the dev world

it refers to the practice of writing tests that describe how your code should work before you actually write the code

the test should fail by default, until your code is evoked, in which case passing the test should indicate that your code works

in many ways, TDD is much more productive than writing code without tests



There are many test-running systems available in JavaScript: [Mocha](https://mochajs.org/), [Jasmine](https://jasmine.github.io/), [Tape](https://github.com/substack/tape) and [Jest](https://jestjs.io/) to name a few. Fortunately, the syntax for each one is very similar. They all have their own set of special features, but the basic syntax is almost identical



### Isolation

An important basic concept in testing is isolation. 

You should only test one method at a time, and your tests for one function should not depend upon an external function behaving correctly - especially if that function is being tested elsewhere.

The main reason for this is that when your tests fail, you want to be able to narrow down the cause of this failure.



### Mocking

There are two solutions to the 'tightly coupled code' problem.

The first, and best option, is to simply write 'Pure Functions' and practice isolation in your code.

But that is simply not always possible..

The second option is **mocking** - writing a "fake" version of a function that always behave *exactly* how you want.

For example, if you're testing a function that gets information from a DOM input, you can use a mock version of the input-grabbing function that always returns a specific value and use THAT in your test.

## Jest

Setting up Jest: https://jestjs.io/docs/getting-started

Note **Jest** (as well as **Babel** and **ESLint**) come preconfigured with `create-react-app`



#### Simple implementation

To add jest to a project, in the repo..

`npm install --save-dev jest`

An example `js` file in your project..

```javascript
// sum.js

function sum(a, b) {
  return a + b;
}
module.exports = sum; // so that function 'sum' is available for import in our test file
```

And a test file..

```javascript
// sum.test.js
const sum = require('./sum');

test('adds 1 + 2 to equal 3', () => {
  expect(sum(1, 2)).toBe(3);
});
```

And add to your `package.json`..

```json
{
  "scripts": {
    "test": "jest"
  }
}
```

Now when you run `npm test` in your repo it will run all jest tests it finds

Additionally, if you want to have `npm test` run every time you save a file you can add to your `package.json`..

```json
{
  "scripts": {
    "test": "jest",
    "watch": "jest --watchAll=true --color=true"
  }
}
```

Now run `npm run watch` and watch will be listening for every time you save a file



#### Common implementation

Note `sum.js` in this case is server-side code (Node.js environment, not browser). Jest runs in Node.js environment so in order to allow testing of client-side modules you would need to bundle them with a module bundler like Webpack or Rollup.

So testing client-side JavaScript code with Jest is actually quite common, and Jest is a versatile testing framework that can handle both server-side and client-side JavaScript.

Here are some modern approaches to structuring JavaScript code for both client-side use and testing:

1. **Use a Module Bundler**: Tools like Webpack or Rollup can bundle your ES6 modules into a single file that works in the browser. They can be configured to output different formats (e.g. CommonJS, or ES Modules), so you can have a build step for your tests and a build step for your browser code.
2. **Babel for Transpilation**: Babel can transpile your ES6+ code into code that is compatible with older browsers or environments. You can use Babel with Jest through `babel-jest` to automatically transform your ES6 modules into a format Jest can understand during testing.
3. **Dual Package Hazard**: When a package contains both CommonJS and ES Module sources and both are used within the same project, this can lead to issues known as the "dual package hazard". It's best avoided by choosing a single module format for a package and sticking to it.

Most modern web development workflows involve a build step, so using tools like Babel and Webpack is considered standard practice.



#### Create-react-app implementation

`create-react-app` abstracts away the complexities of the build configuration, providing a simplified developer experience.

1. **Bundling and Transpilation**: Under the hood, `create-react-app` uses Webpack to bundle and Babel to transpile the code. It sets up a development environment that can immediately handle JSX, ES6, and other modern JavaScript features without any manual configuration.
2. **Environment Handling**: `create-react-app` comes with two primary npm scripts: `start` for development and `build` for production. Each is configured with a different Webpack setup tailored for the respective environment. For development, it includes features like hot module reloading and source maps, while for production, it includes optimizations like minification and chunking.
3. **Testing**: `create-react-app` includes Jest as the testing framework by default. It is pre-configured to work with the Babel setup, so Jest can understand the ES6 and JSX syntax. You don't need to configure Babel separately for Jest when using `create-react-app`.
4. **ES Modules**: The Babel configuration within `create-react-app` transpiles ES Modules into a format compatible with Jest. Therefore, you can write your tests using the same import/export syntax you use in your components.
5. **Zero Configuration**: `create-react-app` aims to be a zero-config tool, where you don't have to manually set up Webpack, Babel, or Jest. All the configurations are pre-set and hidden initially, giving you the ability to just start coding without worrying about the build and test setup.
6. **Ejecting**: If you need more control over the build and test configuration, `create-react-app` allows you to "eject" and customize its configuration files. However, this is a one-way operation and is generally not encouraged unless absolutely necessary, as it exposes you to the complexity that `create-react-app` was designed to hide.



#### Matchers

The most common **matcher** is the **exact** equality

```javascript
test('two plus two is four', () => {
  expect(2 + 2).toBe(4);
});
```

In this code, `expect(2 + 2)` returns an "expectation" object. 

You typically won't do much with these expectation objects except call matchers on them.

In this code, `.toBe(4)` is the matcher.

`toBe` uses `Object.is` to test exact equality

 If you want to check the value of an object, use `toEqual`

```javascript
test('object assignment', () => {
  const data = {one: 1};
  data['two'] = 2;
  expect(data).toEqual({one: 1, two: 2});
});
```

`toEqual` recursively checks every field of an object or array.

`toEqual` ignores object keys with `undefined` properties, `undefined` array items, array sparseness, or object type mismatch. To take these into account use `toStrictEqual` instead.

```javascript
// toBe and toEqual are equivalent for numbers
  expect(value).toBe(4);
  expect(value).toEqual(4);
```

For floating point equality, use `toBeCloseTo` instead of `toEqual` to account for `js` rounding errors



see [Jest Docs](https://jestjs.io/docs/getting-started) for more



## Testing Setup

When testing a React/Preact app using Jest as the test runner..

- **Jest**: Acts as the test runner and framework. It's responsible for executing tests and providing functionalities like test organization, assertions, mocks, and spies.
- **jsdom**: Serves as the testing environment within Jest for simulating a web browser's environment. This is crucial for testing JavaScript code that interacts with the DOM, as it allows such code to run in a Node.js environment as if it were running in a real browser.
- **DOM Testing Library**: Provides utility functions and additional matchers to facilitate the testing of DOM nodes. It allows for more natural querying of the DOM, enabling tests to interact with the DOM in ways similar to how users would. It's framework-agnostic, meaning it can be used with plain JavaScript or any JavaScript framework that interacts with the DOM (like React).
- **React Testing Library**: An extension of the DOM Testing Library, it is specifically tailored for testing React components. It abstracts the complexities of the React component tree, providing utilities to interact with and test React components in a user-centric way.
- **Preact Testing Library**: Similar in functionality to React Testing Library but specifically designed for Preact. It provides a set of tools to render Preact components into a virtual DOM for testing and to interact with these components as users would. This library helps ensure that Preact components work as expected in a simulated browser environment provided by jsdom.
- **jest-dom** is a companion library for DOM/React/Preact Testing Library that provides custom DOM element matchers for Jest. For example, instead of using a combination of generic Jest matchers to test a component's state, **jest-dom** provides matchers like `.toBeVisible()`, `.toHaveTextContent()`, and `.toHaveClass()`.

In a React/Preact application using Jest for unit testing, this combination of tools enables a comprehensive testing strategy. Jest orchestrates the testing process, jsdom simulates the browser environment, and React/Preact Testing Library allows for effective, user-centric testing of React/Preact components.





## DOM Testing Library

[DOM Testing Library](https://testing-library.com/docs/dom-testing-library/intro)

When testing your UI you want your tests to test functionality, rather than the code/implementation details. Changes and refactors to your implementation should not break these tests. The DOM Testing Library provides a way to do this.

The `DOM Testing Library` is a very light-weight solution for testing DOM nodes. The main utilities it provides involve querying the DOM for nodes in a way that's similar to how the user finds elements on the page.

As part of this goal, the utilities this library provides facilitate querying the DOM in the same way the user would. 

- Finding form elements by their label text (just like a user would)
- Finding links and buttons from their text (like a user would)
- It also exposes a recommended way to find elements by a `data-testid` as an "escape hatch" for elements where the text content and label do not make sense or is not practical



Note DOM Testing Library is the "core API" of the Testing Library family - the other libraries (with a few exceptions) re-export the full DOM Testing Library API, with additional methods built on top.



## React Testing Library

[React Testing Library](https://testing-library.com/docs/react-testing-library/intro)

React Testing Library builds on top of DOM Testing Library by adding APIs for working with React components.

Projects created with create-react-app have React Testing Library set up out of the box (`@testing-library/react`)

### Example

```jsx
import { render } from '@testing-library/react';
import App from './App';

test('renders App component', () => {
  render(<App />); // will fail if App fails to render
});

test('renders App component', () => {
  render(<App />);
  screen.debug(); // will output the DOM HTML to the console - you can check this to see what is available for testing!
});

test('Checks for Hello', () => {
  render(<App />);
  screen.getByText('Hello'); // this will fail if no element on the screen has 'Hello' but this isn't very explicit
});

test('Checks for Hello Explicitly', () => {
  render(<App />);
  expect(screen.getByText('Hello')).toBeInTheDocument(); // more explicit
});

// you can also check for sub-strings with regex or exact: false
screen.getByText(/ello/);
screen.getByText(/ello/i); // case-insensitive
screen.getByText('ello', { exact: false }); // case-insensitive
 

// you can also select elements by their accessibility role with React Testing Library

test('Show Available Roles', () => {
  render(<App />);
  screen.getByRole(' '); // this will sow all the selectable roles in the component
});
```



### Search Variants

You'll notice React Testing Library has three search variants..

1. `getBy` returns an element or an error
2. `queryBy` returns an element or `null` - making it possible to check for elements that *shouldn't* be there
3. `findBy` is used for asynchronous elements that will be there eventually



So if you are asserting that an element isn't there, use `queryBy`, otherwise default to `getBy`

```jsx
test('Check that something isnt there, () => {
  render(<App />);
  expect(screen.queryByText('Something')).toBeNull();
});
```



`findBy`

For example, if..

- after its initial render, the App component fetches a user from a simulated API
- the API returns a JavaScript promise which immediately resolves with a user object
- and the component stores the user from the promise in the component's state
- the component updates and re-renders at which point the component should render "Signed in as: user" 

```jsx
const getUser = () => {
  return Promise.resolve({ id: '1', name: 'Robin' });
};

const App = () => {
  const [user, setUser] = useState(null);

  useEffect(() => {
    const loadUser = async () => {
      const user = await getUser();
      setUser(user);
    };
    loadUser();
  }, []);

  return (
    <div>
      {user ? <p>Signed in as {user.name}</p> : null}
    </div>
  );
}
```

If we want to test the component over the stretch of its first render to its second render due to the resolved promise, we have to write an async test, because we have to wait for the promise to resolve asynchronously. 

In other words, we have to wait for the user to be rendered after the component updates for one time after fetching it:

```jsx
test('Displays Signed in as', async () => {
    render(<App />);
    expect(screen.queryByText(/Signed in as/)).toBeNull();
    expect(await screen.findByText(/Signed in as/)).toBeInTheDocument();
});
```

So for any element that isn't there yet but will be there eventually, use `findBy`

React Testing Library is designed to work seamlessly with React so

when you use `findBy` queries, they automatically wait for the next DOM update

this means if a state update causes a re-render, `findBy` will wait for this re-render to check for the element again

or `findBy` just continually checks for 1000ms - either way it's magic



### Events

We can use RTL's `fireEvent` and `waitFor` functions to simulate interactions of an end user

```jsx
import { render, screen, fireEvent } from '@testing-library/react';
import App from './App';

test('Fire an event', () => {
  render(<App />);
  screen.debug();
  fireEvent.change(screen.getByRole('textbox'), {
    target: { value: 'JavaScript' },
  });
  screen.debug();
});
```



## Learning Path for React Testing Library:

1. **Introduction to React Testing Library**:

   - Understand the philosophy: "The more your tests resemble the way your software is used, the more confidence they can give you."
   - Familiarize yourself with the basic syntax and utilities.

   **Resources**:

   - [Official RTL Introduction](https://testing-library.com/docs/react-testing-library/intro/)
   - [Kent C. Dodds - Introducing the React Testing Library](https://kentcdodds.com/blog/introducing-the-react-testing-library)

2. **Querying Elements**:

   - Learn about the different ways to select elements in the DOM: `getBy`, `findBy`, `queryBy`, and their multiple variants (`*ByText`, `*ByRole`, etc.).
   - Understand the difference between these queries and when to use each.

   **Resources**:

   - [Official RTL Queries](https://testing-library.com/docs/queries/about/)

3. **Firing Events**:

   - Learn how to simulate user interactions like clicks, input changes, and form submissions.

   **Resources**:

   - [RTL fireEvent](https://testing-library.com/docs/dom-testing-library/api-events/)

4. **Asynchronous Utilities**:

   - Understand how to deal with asynchronous behavior, such as fetching data or delayed responses.
   - Learn about `waitFor`, `findBy`, and other async utilities.

   **Resources**:

   - [RTL Asynchronous Queries](https://testing-library.com/docs/dom-testing-library/api-async/)

5. **Custom Hooks Testing**:

   - Delve into how to test custom hooks with `@testing-library/react-hooks`.

   **Resources**:

   - [Testing Custom Hooks](https://react-hooks-testing-library.com/)

6. **Mocking & Spying**:

   - Learn how to mock modules or spy on function calls. This is especially useful when you want to isolate a component behavior or avoid making real API calls during tests.

   **Resources**:

   - [Jest Mock Functions](https://jestjs.io/docs/mock-functions)
   - [MSW for mocking network requests](https://mswjs.io/)

7. **Advanced Patterns**:

   - Dive into advanced testing patterns, edge cases, or integration with other tools and libraries.
   - Consider exploring topics like context providers, testing components with routers, or integrating with animations.

   **Resources**:

   - [Common mistakes with React Testing Library - Kent C. Dodds](https://kentcdodds.com/blog/common-mistakes-with-react-testing-library)
   - [Testing Library's Community Recipes & Guides](https://testing-library.com/docs/guide-which-query/)

8. **Practice!**:

   - As with any skill, practice is vital. Start with simpler components and move to more complex scenarios.
   - Regularly refer back to the official documentation and other trusted sources to clarify doubts.