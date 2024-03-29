# React Basics

## Learning Objectives

- [ ] Understanding what React is and why it is used
- [ ] Understanding JSX and differences to HTML
- [ ] Understanding the declarative approach of React
- [ ] Creating React components
- [ ] Understanding rendering with React
- [ ] Project Scaffolding with the `Create React App` tool

---

## What is React and why do we use it?

React is a JavaScript **library** used for building user interfaces. It allows us to create reusable UI components without needing to work directly with the DOM API (e.g. `createElement`) in most cases. In React we write shorter, declarative code.

Compared to working with Vanilla JS, in React we now **describe what the user interface should look like** and React handles the DOM for us under the hood.

To write declarative code for React, we use **JSX**.

## JSX

Even thought JSX looks similar to HTML, it is not HTML as we know it. JSX is actually a syntax extension to JavaScript.
JSX expressions can be used anywhere a JavaScript expression can be used.
This can look as simple as this:

```jsx
const element = <p>Hello World!</p>;
```

We use JSX to create **React elements**. React elements are an intermediary format that React converts
to DOM elements during the rendering process.

This allows us to **declaratively** describe our user interface using JSX.
Up until now we have been using the DOM API in Vanilla JS to create elements **imperatively**.

### Imperative vs. Declarative Programming

To understand the difference between imperative and declarative code, let's look at an example of a simple button.

> ❗️ The main difference between imperative and declarative code is that imperative code describes _how_ something should be built, and declarative code describes _what_ needs to be built.

#### Imperative Code in Vanilla JavaScript

In imperative programming, your code performs a series of actions.

```js
const button = document.createElement("button");
button.type = "button";
button.textContent = "click me";
button.addEventListener("click", () => console.log("Hello World"));
document.body.append(button);
```

- We create the element with `document.createElement()`
- We set the button type,
- We set the text content
- We add the event listener
- We append the button to the body

#### Declarative Code in React

In declarative programming, your code describes a desired outcome.

```jsx
const element = (
  <button type="button" onClick={() => console.log("Hello World")}>
    click me
  </button>
);
```

- We describe in JSX what element we want (in this case a button element)
- React figures out how to update the DOM according to our description

> 💡 A metaphor: Image you are really hungry. You have two options:
>
> The Vanilla JavaScript way would be to cook a meal yourself. You would have to go to the grocery store, buy the ingredients, prepare them, cook them, and finally eat them.
>
> There is also the React way: You could just order food from a restaurant. You would just have to tell them what you want to eat, and they (React) would take care of the rest.

## React Components

React components are **customizable, reusable building blocks** for a React application, They serve as **independent elements of the user interface** that can be used multiple times across different parts of the app. It contains its own structure, logic, and potentially styling.

> 💡 There are hardly any limitations to how 'small' a component can be (e.g. a button), or how 'big' (e.g. an entire page).

To create a component in React, we define a **named function** (using PascalCase) and have it **return the desired elements using JSX**. We can then use the component in our code by using the function name as a tag name.

```jsx
function Button() {
  return (
    <button type="button" onClick={() => console.log("Hello World")}>
      click me
    </button>
  );
}

// Use the component by using the function name as a tag name
const element = <Button />;
```

This is a very powerful concept, because it allows us to reuse the same component in multiple places in our application.

> 💡 Components need to be named with PascalCase, otherwise React will not recognize them as components.

> 📙 Read about [**Your First Component**
> in the React Docs](https://react.dev/learn/your-first-component).

---

## Nesting Elements

JSX elements in a React component can be nested the same way we have been nesting our HTML elements.

```jsx
function Card() {
  return (
    <div>
      <p>Some Text</p>
      <p>Some more Text</p>
    </div>
  );
}
```

## Attributes

In most cases the names for attributes are the same as in HTML, but there are some exceptions. For example, the `class` attribute from HTML is called `className` in JSX.

```jsx
const element = <p className="text">Some Text</p>;
```

> 📙 Find out more about the [differences in attributes](https://legacy.reactjs.org/docs/dom-elements.html#differences-in-attributes)

---

Passing string values to attributes is done by using double quotes. To pass any JavaScript expression use curly braces.

```jsx
const myValue = "This is a string";
const input = <input type="text" value={myValue} minLength={5} />;
```

### Interpolating Expressions

We can use any JavaScript expression inside JSX by wrapping it in curly braces. This is called interpolation. It is similar to string interpolation in JavaScript template strings.

```jsx
const name = "Pawtricia";
const element = <p>My cat's name is {name}</p>;
```

```jsx
const a = 5;
const b = 10;

const element = (
  <p>
    {a} + {b} = {a + b}
  </p>
);
```

> 💡 You can only use **expressions** inside JSX. Statements like `if/else` or `for`-loops are not allowed.

> 📙 Read more about [**JavaScript in JSX with Curly Braces**
> in the React Docs](https://react.dev/learn/javascript-in-jsx-with-curly-braces).

---

## How React Renders

React needs to know where to render the elements it creates. We select the DOM element we want to
render into by using `document.querySelector()`. We then create a React root object. The root object
has a `render()` method that we can use to render React elements into the DOM.

**HTML**

```html
<div id="root"></div>
```

**JavaScript**

```js
const rootElement = document.querySelector("#root");
const root = ReactDOM.createRoot(rootElement);
root.render(<h1>Hello, world</h1>);
```

You'll probably never have to write this code yourself, because it is already included in all
templates and starters. In the real world it usally looks like this:

```js
const rootElement = document.getElementById("root");
const root = ReactDOM.createRoot();

root.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>
);
```

Here we have an imported `<App />` element that is wrapped in `<React.StrictMode>`.

> 💡 `StrictMode` sets up React to run in strict mode. In strict mode React points out potential
> problems in an application.

### React works smart, not hard

React only updates the DOM elements that have changed compared to the last render. This is very
efficient and provides a great user experience (focus stays consistent, inputs keep their values,
etc.) as well as a great developer experience (declaritive code is much easier to read).

## Nice to know: React, JSX, Transpilers and Bundlers

Since JSX is not a standard JavaScript syntax, we need to use a [transpiler](https://babeljs.io/) (a tool that translates one variant of a language into another) to transform it into standard JavaScript, that can be understood by the browser.

A [bundler](https://webpack.js.org/) is a tool that combines all the files of our codebase into one file, that we can include in our HTML. The bundler also takes care of running the transpiler when needed.

The bundler creates a development server when we run `npm run start` locally.

> 💡 You might notice that in the challenges we are using an `import` statement to import `.css` files into our JavaScript files. This is not a standard JavaScript feature, but it is supported by the bundler. A css import statement is transformed into a `<link>` element in the HTML automatically.
>
> ```js
> import "./styles.css";
> ```

---

## npm

[npm](https://www.npmjs.com/) a package registry that works like an app store for your project.

It is used to install and manage packages (libraries) for a project.

It is also used to run scripts that are defined in the `package.json` file (like `npm start`)

---

## `package.json`

Packages that are installed into your project are called dependencies. They are kept inside a
`package.json` file in your project root. The `package.json` file also contains information about
your project.

A `package.json` may look something like this:

```json
{
  "name": "my-app",
  "version": "1.0.0",
  "description": "A description of my app",
  "scripts": {
    "test": "npm run …"
  },
  "author": "Alex Newfish",
  "license": "UNLICENSED",
  "dependencies": {
    "my-dependency": "^10.4.1",
    "my-other-dependency": "^2.0.0"
  },
  "devDependencies": {
    "my-dev-dependency": "^8.0.105",
    "my-other-dev-dependency": "^0.1.6"
  }
}
```

- `dependencies` are packages that your application source code directly depends on, like libraries
  or frameworks.
- `devDependencies` are packages that help you while developing your application, like linters or
  build tools.

### Installing dependencies

`dependencies` and `devDependencies` inside the `package.json` can be installed by running
`npm install` (or just `npm i` for short).

> 💡 Do not forget to run `npm install` after cloning a new repository that has a `package.json`
> file.

When installing, npm creates a `node_modules` folder and a `package-lock.json` file.

- `node_modules` must always be in your `.gitignore` and must not be committed to your repository!
- `package-lock.json` should be commited to your repository.

---

## Project Scaffolding with `Create React App`

Project scaffolding is the process of creating a new project. You will use the
[Create React App](https://create-react-app.dev/docs/getting-started) tool to create a new React project automatically.

> 💡 In principle, you could create a new React project from scratch. However, this would be a lot of work and we would have to set up a lot of things ourselves.

> 💡 Create React App, by the way, works quite similar to the `ghcd` tool you have probably already
> used.

A new project is created by running the following command in the terminal:

```sh
npx create-react-app my-react-app
```

- Run `cd my-first-react-app` to go into the project and open in VSCode with `code .`
- Run `npm i`
- Run `npm start`to start the dev server

A new create-react-app project will have a lot of files and folders. Here is a brief overview:

| File / Folder           | Description                                                                                                              | contains                                                                           |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------- |
| README.md               | general info about project                                                                                               | reminder how to start the dev-server                                               |
| package.json            | project configuration                                                                                                    | information about dependencies, scripts, metadata                                  |
| node_modules folder     | dependencies                                                                                                             | all dependencies of the project                                                    |
| **public folder**       | static assets that are not processed by the bundler                                                                      | e.g. index.html, favicon.ico, manifest.json, robot.txt                             |
| index.html              | root html file, don't mess with the `div id="root"></div>`                                                               | root element for React                                                             |
| favicon.ico             | icon that is shown in the browser tab                                                                                    | image                                                                              |
| robots.txt              | instructions for web robots how to crawl the site                                                                        | text                                                                               |
| manifest.json           | configuration for Progressive Web Apps, it defines how your app appears and behaves when 'installed' on a mobile device. | metadata                                                                           |
| images and other assets | static assets that you want to be served directly without processing.                                                    | images, fonts, etc.                                                                |
| **src folder**          | all source code that will go through webpack processing                                                                  | all JavaScript, JSX, CSS, and other files that make up your React application.     |
| index.js                | The JavaScript entry point where ReactDOM renders the App component into the DOM.                                        | imports react-dom and the App component                                            |
| App.js                  | The root component of the React app                                                                                      | typically where you start writing your app's code and organizing other components. |
| App.css                 | CSS file for the App component                                                                                           | styles for the App component                                                       |
| App.test.js             | Test file for the App component                                                                                          |                                                                                    |
| reportWebVitals.js      | Report performance metrics to Google Analytics                                                                           |                                                                                    |
| setupTests.js           | Setup file for Jest                                                                                                      |

---

## Resources

- [What is React: A Visual Introduction For Beginners on learnreact.design](https://learnreact.design/posts/what-is-react)
- [Writing Markup with JSX in the React Docs](https://react.dev/learn/writing-markup-with-jsx)
- [JavaScript in JSX with Curly Braces in the React Docs](https://react.dev/learn/javascript-in-jsx-with-curly-braces)
- [Your First Component in the React Docs](https://react.dev/learn/your-first-component)
- [Difference between a Framework and a Library on freecodecamp](https://www.freecodecamp.org/news/the-difference-between-a-framework-and-a-library-bd133054023f/)

### `Create React App` Docs

- [Getting Started on the Create React App Docs](https://create-react-app.dev/docs/getting-started)
- [Folder Structure on the Create React App Docs](https://create-react-app.dev/docs/folder-structure)
- [Available Scripts on the Create React App Docs](https://create-react-app.dev/docs/available-scripts)
- [Adding a Stylesheet on the Create React App Docs](https://create-react-app.dev/docs/adding-a-stylesheet)
- [Adding Images, Fonts and Files on the Create React App Docs](https://create-react-app.dev/docs/adding-images-fonts-and-files)

# React Props

## Learning Objectives

- [ ] Understanding what props are
- [ ] Understanding how to pass props to a component
- [ ] Understanding how to use props in a component
- [ ] Understanding how to render conditionally

---

## Using Props

Props is short for properties. They are a way to pass data to a child component. A component receives a props object as the first function parameter.

Props are [passed to a component as attributes](#passing-props-to-a-component).

```js
function UserCard(props) {
  return <div>{props.name}</div>;
}
```

For convenience the props object is often destructured in the function parameter.

```js
function UserCard({ name }) {
  return <div>{name}</div>;
}
```

You can choose any names for your props.

> 💡 There are some naming conventions though. Boolean props are often prefixed with `is`, `has` or `should`. For example `isDisabled`, `hasError` or `shouldShow`. Props that take functions are often prefixed with `on`. For example `onClick`, `onSubmit` or `onHover`. Following these conventions makes it easier to understand the purpose of the prop.

Props can be of any type (string, number, array, object, function, ...).

You should treat the props object as immutable and read-only.

---

## Passing Props to a Component

Props are passed to a component as attributes.

```js
<UserCard name="Alex" />
```

You can pass any type of data as a prop.

```js
<UserCard
  name="Alex"
  age={25}
  onContact={() => console.log("let's chat!")}
  isFavorite={true}
  favoriteFoods={["Pasta", "Salad"]}
  contactDetails={{ email: "alex@neuefische.de", phone: "123456789" }}
/>
```

String props can be passed using double quotes. All other props must be passed using curly braces.

> 💡 Notice the double curly braces for the object. This is because the outer curly braces are used to signify a JavaScript expression. The inner curly braces are used to define an object.

> 💡 There is a shorthand syntax for boolean props. If the value should be `true` you can omit the value.
>
> ```js
> <UserCard isFavorite />
> ```

Omitting any attribute will result in the value `undefined` for that prop.

> 📙 Read more about [**Passing props to a Component**
> in the React Docs](https://react.dev/learn/passing-props-to-a-component).

### Conditional Rendering

You can use props to conditionally render parts of a component.

```js
function UserCard({ name, isFavorite }) {
  return (
    <div>
      {name}
      {isFavorite ? <span>🌟</span> : null}
    </div>
  );
}
```

> 💡 In JSX `null` is a way to render nothing.

You can not use an `if` statement within JSX because only expressions are allowed. You can use an `if` statement outside of the JSX though.

```js
function UserCard({ name, isFavorite }) {
  let favoriteStar = null;
  if (isFavorite) {
    favoriteStar = <span>🌟</span>;
  }

  return (
    <div>
      {name}
      {favoriteStar}
    </div>
  );
}
```

> 📙 Read more about [**Conditional Rendering**
> in the React Docs](https://react.dev/learn/conditional-rendering).

---

## Resources

- [Passing props to a Component in the React Docs](https://react.dev/learn/passing-props-to-a-component)
- [Conditional Rendering in the React Docs](https://react.dev/learn/conditional-rendering)

# React Nesting

## Learning Objectives

- Understanding the concept of nesting
- Creating multiple custom components to create a hierarchy
- Using the `children` prop to render JSX from the parent component
- Understanding composition as a way to build complex components

---

## Passing JSX as Props

Elements created by JSX are just objects. They can be passed around like any other object: for example, as props.

```js
function UserCard({ avatar }) {
  return <div className="card">{avatar}</div>;
}
```

```js
function App() {
  return <UserCard avatar={<Avatar />} />;
}
```

## The `children` Prop

You are already familiar with nesting built-in browser tags:

```js
<div>
  <img />
</div>
```

Oftentimes you'd want your own components to be nestable as well.

```js
<UserCard>
  <Avatar />
</UserCard>
```

If you nest a component inside of another component, the nested component is passed as a prop to the parent component. This special prop is called `children`.

```jsx
function UserCard({ children }) {
  return <div className="card">{children}</div>;
}
```

This component will render the nested element(s) as a child of the `div` element.

> 💡 The nested element(s) can be a single element, multiple elements, or even a string or number.

> 📙 Read more about [**Passing JSX as children**
> in the React Docs](https://react.dev/learn/passing-props-to-a-component#passing-jsx-as-children).

## Fragments

Sometimes you want to return multiple elements from a component function without wrapping them in a `div` or other element. You can use a `Fragment` (`<></>` or `<Fragment></Fragment>`) for this.

This is necessary because React components can only return a single element from a component function.

```jsx
function UserList() {
  return (
    <>
      <UserCard>
        <Avatar />
      </UserCard>
      <UserCard>
        <Avatar />
      </UserCard>
    </>
  );
}
```

This is equivalent to the following, but the shorthand version above is generally preferred.

```jsx
import { Fragment } from "react";

function UserList() {
  return (
    <Fragment>
      <UserCard>
        <Avatar />
      </UserCard>
      <UserCard>
        <Avatar />
      </UserCard>
    </Fragment>
  );
}
```

> 💡 The `<Fragment></Fragment>` syntax is only necessary if you want to pass the special `key` prop to the fragment, which will become important when you start working with lists.

> 💡 When researching you sometimes might see `<React.Fragment></React.Fragment>`, which is the same thing.

> 📙 Read more about [**Fragment (<>...</>)**
> in the React Docs](https://react.dev/reference/react/Fragment).

---

## Composition

When we build React applications, we often want to build complex components from simpler components. This is called composition.

To do so you need to break down you application into components. You can then compose these components to build more complex components.

It is important to figure out which components you need and how they should be composed. This is called application design.

> 📙 Read [**Thinking in React**
> in the React Docs](https://react.dev/learn/thinking-in-react) up to and including Step 2. Later steps require state, which we will cover in a future session.

---

## Resources

- [Passing JSX as children in the React Docs](https://react.dev/learn/passing-props-to-a-component#passing-jsx-as-children)
- [Fragment (<>...</>) in the React Docs](https://react.dev/reference/react/Fragment)
- [Thinking in React in the React Docs](https://react.dev/learn/thinking-in-react)

# React State 1

## Learning Objectives

- [ ] Knowing how to attach events in React
- [ ] Understanding the concept of "state"
- [ ] Using `useState()` to handle state in React
- [ ] Understanding the React Lifecycle

---

## What is state?

State is data that changes over time. Think of the lamp on your desk. It can be switched on or
switched off. The lamp is in a particular state at a given time and that state can change over time.

Another example could be the amount of money in your purse. At any given time you have a certain amount
of money in your purse, but the amount of money can change. The state of your purse can change.
Going to the grocery store will decrease the amount of money, while going to the ATM will increase
it.

This concept also applies to software. Your app can have data that changes over time.

Think of a post on a social media app. You might have liked a specific post, or not. The "liked"
state of a post can be on or off, like the lamp on your desk.

The website of your bank refers to your purse in the analog world. At any given time, the banking software
displays the current balance of your account, the current state. You can use the banking software to
change that state. For example you could transfer money to another account to decrease the number
stored in the "balance" state.

Oftentimes such stateful data changes after a user interaction, like a click on a button.

---

## State in React

In React we work with state by using the `useState` hook function.

We call the `useState` function and pass the **initial state** value as argument. This is the value
that is used in our app until something changes.

Calling the `useState` function gives us two things in return:

- a variable with the **current state** as value
- the `set` function to set a **new state**

```js
import { useState } from "react";

function SocialMediaPost() {
  const [liked, setLiked] = useState(false);

  function toggleLiked() {
    setLiked(!liked);
  }

  return (
    <article>
      <p>Liked: {liked ? "Yes" : "No"}</p>
      <button type="button" onClick={toggleLiked}>
        {liked ? "Remove like" : "Add like"}
      </button>
    </article>
  );
}
```

> 💡 There is a naming convention for React apps that the state variable and the function always
> follow the pattern of `x` and `setX`

> 📙 Read more about the
> [**concept of state** in the React Docs](https://react.dev/learn/adding-interactivity).

In React state is encapsulated per instance of a component. Think of a feed in a social media app.
The feed is a list of posts. Each post is an individual instance of the `SocialMediaPost` component,
each with individual state. When you change the "liked" state of one specific post, all other posts
stay as they are.

A React component can have multiple states. You can use the `useState` function as much as you need.

You can store all kinds of data in state (like booleans, numbers, strings, objects or arrays).

```js
import { useState } from "react";

function SocialMediaPost() {
  const [liked, setLiked] = useState(false);
  const [comments, setComments] = useState([]);
  const [views, setViews] = useState(0);

  /* ... */

  return <article>{/* ... */}</article>;
}
```

---

## What happens when state changes?

To handle state in React we can not simply use a "normal" variable and assign a new value. React
needs to be informed that the data was changed.

This is related to the render cycle of React components.

When React renders a component it executes the component function, which returns JSX. If the JSX
includes a state variable, it uses the variable's value at that time to place into the JSX. Calling
the `set` function with a new value informs React, that the state has changed.

> 💡 Changing a state triggers a re-render of the component.

When re-rendering the component, React executes the component function again from top to bottom,
which will again return JSX. However, this time the variable has a new value - the value that was
passed with the call of the `set` function. This means the return JSX includes the new value.

> 📙 Read more about
> [**state updates and re-rendering** in the React Docs](https://react.dev/learn/render-and-commit).

---

## Resources

- [React Docs: Adding Interactivity](https://react.dev/learn/adding-interactivity)
- [React Docs: Responding to Events](https://react.dev/learn/responding-to-events)
- [React Docs: A simple variable is not enough](https://react.dev/learn/state-a-components-memory#when-a-regular-variable-isnt-enough)
- [React Docs: Render and commit](https://react.dev/learn/render-and-commit)
- [MDN: react events and state](https://developer.mozilla.org/en-US/docs/Learn/Tools_and_testing/Client-side_JavaScript_frameworks/React_interactivity_events_state)

# React with Arrays

## Learning Objectives

- [ ] Knowing how to use `.map()` to render lists in JSX
- [ ] Understanding how to render items from an array of objects
- [ ] Knowing to add a unique key for list items

---

## Arrays in JSX

To render elements from an array in React we use the array method `.map()`.

The array method `.map()` is used to apply a transformation to all items of an array. When rendering
an array to JSX we like to do exactly this. We like to transform each item of an array into a JSX
tag. This is why we are using `.map()`.

```js
function Drinks() {
  const drinks = ["water", "lemonade", "coffee", "tee"];

  return (
    <ul>
      {drinks.map((drink) => (
        <li>{drink}</li>
      ))}
    </ul>
  );
}
```

---

## Key Property

The example above misses a tiny, but very important part: the `key` prop!

Without the `key` prop you will see an error in the console:

> `Warning: Each child in a list should have a unique "key" prop.`

When rendering an array in JSX you need to pass a **unique identifier** as value for the `key` prop
of the first JSX tag returned in `.map()`. This is important for React to keep track of changes that
happens to the data when re-rendering.

Therefore you must always make sure your array contains a unique id per item. You can ensure this by
using objects to define the data in your arrays.

```js
function Drinks() {
  const drinks = [
    { id: 0, name: "water" },
    { id: 1, name: "lemonade" },
    { id: 2, name: "coffee" },
    { id: 3, name: "tea" },
  ];

  return (
    <ul>
      {drinks.map(({ id, name }) => (
        <li key={id}>{name}</li>
      ))}
    </ul>
  );
}
```

> 📙 If you are interested in understanding the details behind this, you can read about
> [**the `key` prop** in the React Docs](https://react.dev/learn/rendering-lists#keeping-list-items-in-order-with-key).

> 💡 If you pass the `key` prop to a component, you cannot access it in the component. It is a special prop that React only uses internally.
>
> ```js
> function Drink({ name, key }) {
>   console.log(key); // → undefined
>   return <li>{name}</li>;
> }
>
> function Drinks() {
>   const drinks = [
>     { id: 0, name: "water" },
>     { id: 1, name: "lemonade" },
>     { id: 2, name: "coffee" },
>     { id: 3, name: "tea" },
>   ];
>
>   return (
>     <ul>
>       {drinks.map(({ id, name }) => (
>         <Drink key={id} name={name} />
>       ))}
>     </ul>
>   );
> }
> ```
>
> If you want to access the `id` in this example you can pass it again as a prop:  
> `<Drink key={id} id={id} name={name} />`.

## Keyed Fragments

If you are rendering a list of items that are not wrapped in a single JSX tag, you can use a
`<Fragment>` to wrap the items.

```js
import { Fragment } from "react";

function Drinks() {
  const drinks = [
    { id: 0, name: "water", description: "very wet" },
    { id: 1, name: "lemonade", description: "quite sweet" },
    { id: 2, name: "coffee", description: "cold brew" },
    { id: 3, name: "tea", description: "earl grey, hot" },
  ];

  return (
    <dl>
      {drinks.map(({ id, name, description }) => (
        <Fragment key={id}>
          <dt>{name}</dt>
          <dd>{description}</dd>
        </Fragment>
      ))}
    </dl>
  );
}
```

> 💡 Here you cannot use the short syntax (`<>…</>`) for the `<Fragment>` because you need to
> pass the `key` prop to the `<Fragment>`. The short syntax does not allow to pass props.

---

## Resources

- [React Docs: Rendering Lists](https://react.dev/learn/rendering-lists)

# React State 2

## Learning Objectives

- [ ] Knowing how to handle form fields: controlled components, uncontrolled components
- [ ] Knowing how to handle form submit events
- [ ] Understanding the concept of lifting state up
- [ ] Knowing how to pass state and functions via props
- [ ] Understanding that state updates are not synchronous
- [ ] Knowing what a `hook` in React is and which rules apply to hooks

---

## Sharing State Between Components

### Passing State Down

The value of a state variable and the setter function can be passed down to child components as
props. They are functions and values, so they can be passed down like any other data.

```js
function Parent() {
  const [count, setCount] = useState(0);

  function handleIncrement() {
    setCount(count + 1);
  }

  return <Child count={count} onIncrement={handleIncrement} />;
}
```

```js
function Child({ count, onIncrement }) {
  return (
    <>
      <p>Count: {count}</p>
      <button onClick={onIncrement}>increment</button>
    </>
  );
}
```

### Lifting State Up

When we have multiple components that need to share state, we can lift the state up to the parent
component and pass it down as props. This is called "lifting state up" because you usually start with
the state directly in the child component and then move it up to the parent components as you need
it in more and more components.

A state variable can be passed down to multiple child components. The child components can then
update the state variable by calling the setter function.

Any state variable should live as low in the component tree as possible but has high as needed. If
the whole `App` needs to know about the state variable, it should live in the `App` component. If
only child components of the `Article` need to know about the state variable, it should live in the
`Article` component.

Consider the following example:

<img src="./assets/lifting-state-up.png" width="616" height="694" />

Here we find that a `Link` in the `Navigation` component needs to know about a state that previously
existed in the `Article` component. We can lift the state up to the `App` component and pass it down
to the `Article` component as a prop.

> 📙 Read more about
> [**Sharing State Between Components** in the React docs](https://react.dev/learn/sharing-state-between-components).

## Handling Form Data

### Using Form Data `onSubmit`

We can use the `onSubmit` event handler to handle form data. The `onSubmit` event handler is called
when the user submits the form. We can get the form data (just like with regular JavaScript) from
the `event` object.

```js
function SearchForm() {
  function handleSubmit(event) {
    event.preventDefault();
    const form = event.target;
    const searchTerm = form.elements.searchTerm.value;
    console.log("A new search term was submitted:", searchTerm);
  }
  return (
    <form onSubmit={handleSubmit}>
      <label htmlFor="searchTerm">Search</label>
      <input name="searchTerm" id="searchTerm" />
      <button>Search</button>
    </form>
  );
}
```

In this example the input elements value is not manually controlled by React: The input is an
"uncontrolled input". It's value is managed by the browser. In the submit event handler we just
"peek" at the input field and read the value from the DOM.

### Using Controlled Inputs

We can use React to control the value of an input element. This is called a "controlled input". This
means that we manually set the value attribute of the input element. We can wire up a state variable
to the value attribute of the input element. This way the input element will always have the same
value as the state variable. Combined with the `onChange` event handler we can update the state
variable when the user types in the input field.

```js
function SearchForm() {
  const [searchTerm, setSearchTerm] = useState("");

  function handleSubmit() {
    event.preventDefault();
    console.log("A new search term was submitted:", searchTerm);
  }

  return (
    <form onSubmit={handleSubmit}>
      <label htmlFor="searchTerm">Search</label>
      <input
        name="searchTerm"
        id="searchTerm"
        value={searchTerm}
        onChange={(event) => setSearchTerm(event.target.value)}
      />
      <button>Search for {searchTerm}</button>
    </form>
  );
}
```

In this example you always know the value of the search term input. Since it is a state variable,
you can use it in other places in your application. You should prefer using uncontrolled inputs
when possible, but sometimes you need to use a controlled input.

You might need a controlled input when

- showing search results while the user is typing,
- autocompleting the user's input or
- validating the user's input.

## State Updates are not Immediate

When we call the setter function of a state variable, React will not immediately update the state
variable. Instead, it will update it's internal value and schedule a re-render of the component.

```js
// ⚠️ This code is broken!
function Counter() {
  const [count, setCount] = useState(0); // count is 0 initially

  function handleIncrement() {
    // when this is first called, count is still 0
    console.log(count); // → 0

    // this will set reacts internal state to 1,
    // but does not update the count variable
    setCount(count + 1);
    console.log(count); // → 0

    // the count variable is still 0, thus count + 1 is still 1,
    // so react's internal state will still be 1
    setCount(count + 1);
    console.log(count); // → 0

    // since setter functions were called
    // react will schedule a re-render of
    // the component with the new count value of 1
  }

  return (
    <>
      <p>Count: {count}</p>
      <button onClick={handleIncrement}>increment by 2</button>
    </>
  );
}
```

This behavior can be unexpected, but it is important to understand that state variables are not
immediately updated.

There are a few ways to fix the code above. In this example we could call `setCount(count + 2)` and
be done. If for some reason we need to call `setCount` twice, we can use the functional form of the
setter function, which provides the current internal value of the state variable as an argument.

```js
// ⚠️ This code is unnecessary complicated, but it works!
function Counter() {
  const [count, setCount] = useState(0); // count is 0 initially

  function handleIncrement() {
    // when this is first called, count is still 0
    console.log(count); // → 0

    // this will set reacts internal state to 1,
    // but does not update the count variable
    setCount((prevCount) => prevCount + 1);
    console.log(count); // → 0

    // the internal value of count is 1,
    // we get it as the the first parameter of the function we pass to the setter.
    // 1 + 1 is 2, so react's internal state will now be _2_
    setCount((prevCount) => prevCount + 1);
    console.log(count); // → 0

    // since setter functions were called
    // react will schedule a re-render of
    // the component with the new count value of _2_
  }

  return (
    <>
      <p>Count: {count}</p>
      <button onClick={handleIncrement}>increment by 2</button>
    </>
  );
}
```

> 💡 Here the prefix `prev` is used to indicate that the value is the previous value of the state
> variable. Another common convention is to use the just the first letter of the state variable as
> the parameter name: `setCount(c => c + 1)`.

> 📙 Read more about
> [**Updating state based on the previous state**](https://react.dev/reference/react/useState#updating-state-based-on-the-previous-state)
> and
> [**I’ve updated the state, but logging gives me the old value**](https://react.dev/reference/react/useState#ive-updated-the-state-but-logging-gives-me-the-old-value)
> in the React docs.

## React Hooks

The `useState` function is part of a broader set of features of react that give components extra
powers.

Hooks are functions that allow component functions to hook into React features (like state) and
allow components to do more than a traditional JavaScript function can. They follow the naming
convention `useXzy`.

Common hooks that you'll come across are `useState` and `useEffect`.

When using hooks you need to follow a few rules:

- Only call hooks at the top level. Don’t call Hooks inside loops, conditions, or nested functions.
- Only call hooks from React function components or custom hooks. Don’t call Hooks from regular
  JavaScript functions.

> 📙 Read more about [**Hooks** in the React Docs](https://reactjs.org/docs/hooks-overview.html)
> from when they were introduced to React.

---

## Resources

- [Sharing State Between Components in the React Docs](https://react.dev/learn/sharing-state-between-components)
- [Updating state based on the previous state in the React Docs](https://react.dev/reference/react/useState#updating-state-based-on-the-previous-state)
- [I’ve updated the state, but logging gives me the old value in the React Docs](https://react.dev/reference/react/useState#ive-updated-the-state-but-logging-gives-me-the-old-value)
- [Hooks at a Glance in the React Docs](https://reactjs.org/docs/hooks-overview.html)

# React State 3

## Learning Objectives

- [ ] Knowing how to handle arrays and objects in state
- [ ] Knowing what state mutation is and how to avoid it

---

## Avoiding State Mutation

Regardless of how complex the state you have in your application (object, array, array of objects) is, you must always treat state as immutable.
This means that you should not directly mutate the state, e.g. with reassigning a new value to it.

To avoid mutation when updating state, you need to

1. create a new object / array (or make a copy of the existing one), and
2. use the setter function with the recently created / updated copy in order to cause a re-render.

---

## Updating Objects in State

To make a copy of an object and change only some properties, you can use the spread syntax:

```js
const [person, setPerson] = useState({
  firstName: "John",
  lastName: "Doe",
});

function handleChangeFirstName(firstName) {
  setPerson({ ...person, firstName });
}

// Somewhere else:
handleChangeFirstName("Jane");
```

> ❗️ If you were to assign a new value directly, you would mutate the state. This is bad because we must treat state as immutable. Doing so can lead to hard to find bugs.
>
> ```js
> // ⚠️ NEVER DO THIS
> function handleChangeFirstName(firstName) {
>   person.firstName = firstName;
>   setPerson(person);
> }
> ```

> 📙 Learn more about [**Updating Objects in State** in the React Docs](https://react.dev/learn/updating-objects-in-state).

---

## Updating Arrays in State

As you know, there are several ways to update arrays. Some of them, however, mutate the array, and some
of them don't.

|           | avoid (mutates the array)           | prefer (returns a new array) |
| --------- | ----------------------------------- | ---------------------------- |
| adding    | `push`, `unshift`                   | `[...arr]` spread syntax     |
| removing  | `pop`, `shift`, `splice`            | `filter`                     |
| replacing | `splice`, `arr[i] = ...` assignment | `map`                        |
| sorting   | `reverse`, `sort`                   | copy the array first         |

> 💡 It does not matter whether your array state contains only primitives or other objects / arrays;
> in all cases, you should only use the preferred array methods.

### Adding to an Array

To add an element to an array, you can use the spread syntax:

```js
const [numbers, setNumbers] = useState([0, 1, 2]);

function handleAppendNumber(number) {
  setNumbers([...numbers, number]);
}

// Somewhere else:
handleAppendNumber(3);

function handlePrependNumber(number) {
  setNumbers([number, ...numbers]);
}

// Somewhere else:
handlePrependNumber(-1);
```

### Removing from an Array

To remove an element from an array, you can use the `filter` method:

```js
const [numbers, setNumbers] = useState([0, 1, 2]);

function handleRemoveNumber(numberToRemove) {
  setNumbers(numbers.filter((number) => number !== numberToRemove));
}

// Somewhere else:
handleRemoveNumber(1);
```

### Replacing an Array Element

To replace an element in an array, you can use the `map` method:

```js
const [numbers, setNumbers] = useState([0, 1, 2]);

function handleReplaceNumber(oldNumber, newNumber) {
  setNumbers(
    numbers.map((number) => {
      if (number === oldNumber) return newNumber;
      return number;
    })
  );
}

// Somewhere else:
handleReplaceNumber(1, 1337);
```

> 📙 Learn more about [**Updating arrays without mutation** in the React Docs](https://react.dev/learn/updating-arrays-in-state#updating-arrays-without-mutation).

---

## Updating Arrays of Objects in State

Most of the time, you will encounter arrays of objects in your state.

### Adding a new Object

You can add a new object to the state array by using the spread syntax:

```js
const [trees, setTrees] = useState([
  { id: 0, name: "Oak", height 7.5},
  { id: 1, name: "Beech", height 6},
  { id: 2, name: "Pine", height 10}
]);

function handleAddTree(tree) {
  setTrees([...trees, tree]);
}

// Somewhere else:
handleAddTree({id: 3, name: "Spruce", height: 13})
```

### Removing an Object

To remove an object, you can `filter` the array for a unique identifier. In most cases, this
identifier is in scope because the relevant object is rendered via `map`.

```js
const [trees, setTrees] = useState([
  { id: 0, name: "Oak", height 7.5},
  { id: 1, name: "Beech", height 6},
  { id: 2, name: "Pine", height 10}
]);

function handleRemoveTree(idToRemove) {
  setTrees(trees.filter((tree) => tree.id !== idToRemove));
}

// Somewhere else:
handleRemoveTree(0);
```

### Replacing an Object

To replace an object, you can use `map` to create a new array with the updated object. Remember to create a copy of the object first, otherwise you will mutate the state.

```js
const [trees, setTrees] = useState([
  { id: 0, name: "Oak", height 7.5},
  { id: 1, name: "Beech", height 6},
  { id: 2, name: "Pine", height 10}
]);

function handleSetNewHeightForTree(id, height) {
  setTrees(
    trees.map((tree) => {
      if (tree.id === id) return { ...tree, height };
      return tree;
    })
  );
}

// Somewhere else:
handleSetNewHeightForTree(0, 8);
```

### Sorting an Array of Objects

To sort an array of objects, you can use `sort` on a _copy of the array_ with a custom compare function. The compare function
returns a number, which is used to determine the order of the elements.

```js
const [trees, setTrees] = useState([
  { id: 0, name: "Oak", height 7.5},
  { id: 1, name: "Beech", height 6},
  { id: 2, name: "Pine", height 10}
]);

function handleSortTreesByHeight() {
  setTrees([...trees].sort((a, b) => a.height - b.height));
}
```

> 📙 Learn more about [**Updating objects inside Arrays** in the React Docs](https://react.dev/learn/updating-arrays-in-state#updating-objects-inside-arrays).

## Choosing the State Structure

There are some common pitfalls when choosing your state structure.

### Group Related State

If you have state that belongs (and updates) together, group it into a single object. This makes it easier to update the state.

```js
// ❌ MEH
const [userName, setUserName] = useState("Alex");
const [userAge, setUserAge] = useState(28);

// ✅ BETTER
const [user, setUser] = useState({ name: "Alex", age: 28 });
```

### Avoid Redundant State

If you have a value that is derived from a state, you should avoid storing it in state. Instead just use a normal variable.

The problem with redundant state is that it can get out of sync with the source of truth if you forget to update it correctly.

```js
// ❌ BAD
const [user, setUser] = useState({ name: "Alex", age: 28 });
const [isAdult, setIsAdult] = useState(user.age >= 18);

// ✅ GOOD
const [user, setUser] = useState({ name: "Alex", age: 28 });
const isAdult = user.age >= 18;
```

### Avoid Duplication in State

Avoid storing the same value in multiple places in state. This can lead to bugs and makes it harder to update the state.

```js
// ❌ BAD
const [trees, setTrees] = useState([
  { id: 0, name: "Oak", height 7.5},
  { id: 1, name: "Beech", height 6},
  { id: 2, name: "Pine", height 10}
]);

const [selectedTree, setSelectedTree] = useState(trees.find((tree) => tree.id === 0));

// Somewhere else:
setSelectedTree(trees.find((tree) => tree.id === 2));


// ✅ GOOD
const [trees, setTrees] = useState([
  { id: 0, name: "Oak", height 7.5},
  { id: 1, name: "Beech", height 6},
  { id: 2, name: "Pine", height 10}
]);

const [selectedTreeId, setSelectedTreeId] = useState(0);

const selectedTree = trees.find((tree) => tree.id === selectedTreeId);

// Somewhere else:
setSelectedTreeId(2);
```

### Avoid Having Duplicate Lists in State

If you have a list of items in state, you should avoid storing a derived version of it in a different state variable. This is a common mistake when you want to display a filtered version of the list.

```js
// ❌ BAD
const [trees, setTrees] = useState([
  { id: 0, name: "Oak", height 7.5},
  { id: 1, name: "Beech", height 6},
  { id: 2, name: "Pine", height 10}
]);

const [filteredTrees, setFilteredTrees] = useState(trees.filter((tree) => tree.height > 7));

// Somewhere else:
setFilteredTrees(trees.filter((tree) => tree.height > 9));

// ✅ GOOD
const [trees, setTrees] = useState([
  { id: 0, name: "Oak", height 7.5},
  { id: 1, name: "Beech", height 6},
  { id: 2, name: "Pine", height 10}
]);

const [minHeight, setMinHeight] = useState(7);

const filteredTrees = trees.filter((tree) => tree.height > minHeight);

// Somewhere else:
setMinHeight(9);
```

> 📙 Read more about [**Choosing the State Structure** in the React Docs](https://react.dev/learn/choosing-the-state-structure). The Docs have many more examples and explanations.

---

## Resources

- [Updating Objects in State (React Docs)](https://react.dev/learn/updating-objects-in-state)
- [Updating Arrays in State (React Docs)](https://react.dev/learn/updating-arrays-in-state)
