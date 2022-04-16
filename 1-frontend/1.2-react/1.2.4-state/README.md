# 1.2.4: React State

## Introduction

State is the concept in React that represents temporary data stored in the app, and data that potentially triggers DOM manipulation when changed. When we run the ReactDOM render function React manipulates the DOM once when the page loads. Over the life of the React app in the browser, React may manipulate the DOM multiple times as the user makes actions that modify the app state.

## Events

Before we learn how to use state, let's learn how to specify event listener callbacks in React. The following example calls `incrementCount` when the button is clicked. See the full list of React listener attributes here: [https://reactjs.org/docs/events.html#supported-events](https://reactjs.org/docs/events.html#supported-events).

```jsx
<button onClick={incrementCount}>Click me</button>
```

Note in the following example we define the callback function `incrementCount` _inside_ the component function `Counter`. We would not typically define a function inside a function in JS, but this is standard convention in React functional components.

```jsx
import React from "react";

export default function Counter() {
  // Define count variable shared across the component
  let count = 0;

  // Define incrementCount function to increment count on an event
  const incrementCount = (event) => {
    count += 1;
    console.log(`current value of count is: ${count}`);
  };

  // Return the JSX to be rendered in the browser
  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={incrementCount}>Click me</button>
    </div>
  );
}
```

This code may not work as you expect. We display the `count` variable value on line 16. Clicking the button triggers `incrementCount`, and the value of `count` changes, but its value on screen never does.

In order to get React to manipulate the DOM on state variable changes, we have to use specific built-in features of React.

## Hooks and `useState`

In React class components (see [1.2.3.3: Class Components](1.2.3-react-components/1.2.3.3-class-components.md)), there is a special class property `this.state` that is an object that stores the local state for that component. When properties in `this.state` change, the JSX that depends on those properties gets re-rendered.

In React functional components, `this.state` is replaced by what is known as "**hooks**". Hooks are the more modern React system for DOM manipulation, replacing both `this.state` and what were known as "component lifecycle methods" that we will learn about in Module 8: Advanced React. The React team launched hooks in Feb 2019, thus many companies that used React before 2019 still rely on class components.

The hooks function `useState` is a React function that returns an array with 2 elements.

1. A variable representing the state value, e.g. `X`
2. A function that updates this value, whose name is typically `setX`, where `X` is the variable name from #1.

`useState` takes 1 input, the initial state value. In the example below `count` begins as `0`.

```jsx
import React, { useState } from "react";

export default function Counter() {
  // Initialise count to 0
  const [count, setCount] = useState(0);

  // Callback function to update state
  const incrementCount = (event) => {
    console.log(`current value of count is: ${count}`);
    // Call the setCount hook function to manipulate the DOM
    setCount(count + 1);
  };

  console.log("Executing Counter component function");

  // Return JSX to render
  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={incrementCount}>Click me</button>
    </div>
  );
}
```

Note the following when we run this code.

1. `count` gets updated when we press the button!
2. The `console.log` on line 14 runs every time the counter gets updated

When we call the state "hook function" `setCount`, React takes the value and calls the component function again, where `count` in the re-rendered component is the new value, but `count` in the original component is still the old value. The variable `count` and hook function `setCount` are related from when we first created them with `useState`. The subsequently called component function renders JSX with the _**new**_ value and React puts it on screen.

## Differences Between Manual DOM Manipulation and React State

In the past we might have manipulated the DOM manually when increment count button were clicked by running code like `document.getElementById('count')` to get the element that displays the count, and setting that element's text value to the new count.

With React, this process of updating the display element's value happens automatically when the `count` state changes. This makes our lives easier as developers because we no longer need to manually manage state; React manages it automatically for us.

In summary, we can describe this difference as that between an **"imperative"** paradigm (manual DOM manipulation) where we need to command the DOM to change every time, and a **"declarative"** paradigm (React), where we declare how the UI should look like and what state it depends on in components, and React automatically updates the UI when the state changes.

## Full Example

Clicking "Click me" updates the `count` state and re-renders `Counter` component with new value of `count`.

#### App.jsx

```jsx
import React, { useState } from "react";

function Counter() {
  // Initialise count to 0
  const [count, setCount] = useState(0);

  // Callback function to update state
  const incrementCount = (event) => {
    console.log(`current value of count is: ${count}`);
    // Call the setCount hook function to manipulate the DOM
    setCount(count + 1);
  };

  console.log("Executing Counter component function");

  // Return JSX to render
  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={incrementCount}>Click me</button>
    </div>
  );
}

export default function App() {
  console.log("Executing App component function");
  return (
    <div>
      This is App.jsx
      <Counter />
    </div>
  );
}
```

## Optimising Nested Components

When a component is rendered, React also renders all its child components. Note how the `Fahrenheit` `console.log` happens when `count` changes. To avoid this for performance reasons, we might move `BigWord` and `Fahrenheit` components up inside the `App` component so that they are not re-rendered every time `count` changes in `Counter`.

#### App.jsx

```jsx
import React, { useState } from "react";

function BigWord() {
  console.log("Executing BigWord component function");
  return <h1>HELLO</h1>;
}

function Fahrenheit({ celsiusTemp }) {
  console.log("Executing Fahrenheit component function");
  const fahrenheitTemp = (celsiusTemp * 9) / 5 + 32;
  return (
    <p>
      {celsiusTemp} in Fahrenheit is: {fahrenheitTemp}
    </p>
  );
}

function Counter() {
  const [count, setCount] = useState(0);

  const incrementCount = (event) => {
    console.log(`Current value of count is: ${count}`);
    setCount(count + 1);
  };

  console.log("Executing Counter component function");

  // In this implementation, BigWord and Fahrenheit components get
  // re-rendered every time the "count" state changes. This is
  // inefficient and undesirable.
  return (
    <div>
      <BigWord />
      <Fahrenheit celsiusTemp={count} />
      <p>You clicked {count} times</p>
      <button onClick={incrementCount}>Click me</button>
    </div>
  );
}

export default function App() {
  console.log("Executing App component function");
  return (
    <div>
      This is App.jsx
      <Counter />
    </div>
  );
}
```

## Set State Functions Do Not Instantly Update Variables

A major feature of using the React library to do DOM manipulation is that calling a set state hook function triggers the library to update the DOM. Basically this happens whenever the current context of the function ends, i.e., a click event function runs (on line 9) and a set state function is called within. React waits until the function ends to update the DOM.

Notice the `debugger` statement on line 12. This will pause execution of the JavaScript at that line- this makes it clear that after the `setCount` function call, the browser screen has not been updated yet.

#### React Updating State Values

Another thing to pay attention to is the value of `count`. It has also not changed. Calling the set state function does not set the count state variable. This value changes after the function ends.

This means that you cannot call a set state hook function and rely on an updated state value further on in the function.

```
import React, { useState } from 'react';

export default function Counter() {
  // Initialise count to 0
  const [count, setCount] = useState(0);

  // Callback function to update state
  const incrementCount = (event) => {
    console.log(`current value of count is: ${count}`);
    // Call the setCount hook function to manipulate the DOM
    setCount(count + 1);
    debugger;
    console.log('THIS WILL NOT BE THE UPDATED COUNT VALUE')
    console.log(count);
  };

  console.log('Executing Counter component function');

  // Return JSX to render
  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={incrementCount}>Click me</button>
    </div>
  );
}
```

## Further Reading

Past students have found [this video](https://www.youtube.com/watch?v=TNhaISOUy6Q) helpful in explaining React Hooks.

Web Dev Simplified has a series that does deep dives into React hooks. [This video](https://www.youtube.com/watch?v=O6P86uwfdR0) is specifically for useState.
