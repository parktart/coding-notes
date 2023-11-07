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

Note Jest (as well as Babel and ESLint) come preconfigured with `create-react-app`



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

Additionally, if you want to have `npm test` run every time you save a `.js` file you can add to your `package.json`..

```json
{
  "scripts": {
    "test": "jest",
    "watch": "jest --watch *.js"
  }
}
```

Now run `npm run watch` and watch will be listening for every time you save a `.js` file



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