# 1.3: React

Learning Objectives

1. React is a frontend framework and library that allows us to create custom, nest-able UI elements with a combination of HTML and JavaScript syntax (JSX)
2. How to write JSX
3. How to write and render Class based React components
4. How to use props
5. How to use state
6. What are component lifecycles and lifecycle methods
7. How to handle JS events in React
8. How to design component architecture

## Introduction

[React](https://legacy.reactjs.org/) is a frontend framework and library that allows us to create custom, nest-able UI elements with a combination of HTML and JavaScript syntax (JSX). React's HTML-like structure makes it easy to visualise, and its integrated JS makes it easy to render dynamic data. Alternative but less popular frontend libraries include [Vue](https://vuejs.org) and [Angular](https://angularjs.org).

We will use React's official [guide](https://reactjs.org/docs/hello-world.html) and [tutorial](https://legacy.reactjs.org/tutorial/tutorial.html) to learn React, and React's official app-starter kit [Create React App](https://create-react-app.dev) to build React apps. Create React App contains a tool called Webpack that translates React to code that browsers can read. Browsers do not read React natively; they read HTML, CSS and JS, not JSX.

The following sections provide Rocket's annotations to React's official [guide](https://reactjs.org/docs/hello-world.html) and [tutorial](https://legacy.reactjs.org/tutorial/tutorial.html) to explain concepts that the React team assumes readers know.

#### <mark style="color:red;">Additional Setup for Windows machines (If your application doesn't automatically reflect saved changed after npm start)</mark>

<mark style="color:red;">This is only required if the React inbuilt hot-reloading function isn't working as intended.</mark>

After forking and cloning the exercise repository please access it through your code editor.&#x20;

In the package.json please find:

```
"scripts": {
    "start": "react-scripts start",
```

Replace with:

```
"scripts": {
    "start": "WATCHPACK_POLLING=true react-scripts start",
```

This will mean that when you run the `npm start` command the React application will use polling, any changes you make while running the app will be reflected in the browser after a few seconds. This is a work around, React hot-reloading should work straight out of the box.

## Day 5

### 1: [Hello World](https://legacy.reactjs.org/docs/hello-world.html)

1. `document.getElementById('root')` is a DOM (Document Object Model) command that retrieves the HTML element with ID "root". React renders our app inside that element. React removes the need to write DOM code and the above command is the only DOM command we will need.
2. Rocket recommends we play with as many of the provided CodePen examples as we can to understand the relevant concepts
3. Rocket recommends completing the "Main Concepts" guide before attempting the "practical tutorial" so the "practical tutorial" concepts sink in better
4. If there is anything you do not understand in the guide, please let your SL know and we can include it in these notes!

{% embed url="https://youtu.be/PBBynEdqlIo" %}
CRA Introduction
{% endembed %}

{% embed url="https://youtu.be/Q0aFh78sU30" %}
Inside the CRA
{% endembed %}

### 2: [Introducing JSX](https://legacy.reactjs.org/docs/introducing-jsx.html)

1. DOM stands for "Document Object Model", which is a JavaScript representation of HTML rendered on a web page. Frontend frameworks like React use the DOM to programmatically manipulate UI without manually specifying HTML. Rocket recommends [W3School's intro to JavaScript HTML DOM](https://www.w3schools.com/js/js\_htmldom.asp) (just the 1st page) for a primer. For Rocket's Bootcamp we can stop at DOM Intro without reading W3School's subsequent pages on DOM.
2. To apply CSS classes to JSX elements we will need to use the `className` keyword instead of `class`, which we used with vanilla HTML. This is because `class` is a reserved keyword in JS used to declare classes (which we will see in 4: Components and Props below).

{% embed url="https://youtu.be/K_DZ7Q5SsY4" %}
JavaScript and XML
{% endembed %}

{% embed url="https://youtu.be/lW4-WsBflXs" %}
Using JSX
{% endembed %}

### 3: [Rendering Elements](https://legacy.reactjs.org/docs/rendering-elements.html)

1. React follows what we call a "declarative" UI paradigm, where we tell our computers how the UI should look, but not how to achieve that look. In the clock example on this page, we tell React that the latest time should always be in the `h2` element, but we never explicitly tell React to update the value in the `h2` element. The declarative paradigm is a layer on top of the "imperative" paradigm of DOM manipulation more commonly used before React.

## Day 6

### 4: [Components and Props](https://legacy.reactjs.org/docs/components-and-props.html)

1. "ES6 classes" are the same concept we learnt about in [0.4.6: Classes](../../0-foundations/0.4-javascript/0.4.4-classes.md)
2. [User-defined components must be capitalised](https://reactjs.org/docs/jsx-in-depth.html#user-defined-components-must-be-capitalized). Otherwise React will think they are HTML tags.

{% embed url="https://youtu.be/-6hYECl3-z4" %}
React Components
{% endembed %}

{% embed url="https://youtu.be/4O8igNdrSGs" %}
React Props
{% endembed %}

### 5: [State and Lifecycle](https://legacy.reactjs.org/docs/state-and-lifecycle.html)

1. [`setInterval`](https://www.w3schools.com/jsref/met\_win\_setinterval.asp) is a function that runs a given "callback function" at a specified time interval. A callback function is a function that runs at a later time when triggered by an event, such as the timer in `setInterval`.
2. The `super` function in the class `constructor` function runs the `constructor` function of the class' parent class, if any. In the `Clock` example, `super` runs the `constructor` function of the `React.Component` class. This helps classes we create that "inherit" `React.Component` have all functionality of `React.Component` without us having to declare that functionality.

#### Hands-On Explanations: State

{% embed url="https://youtu.be/FJQ052Bk3g8" %}
React State
{% endembed %}

{% embed url="https://youtu.be/jJxJduBmGjg" %}
React Counter Component - Implementing state
{% endembed %}

{% embed url="https://youtu.be/5ZrER1ddAyw" %}
React setState
{% endembed %}

#### Hands-On Explanations: Component Life Cycle Methods

{% embed url="https://youtu.be/Cum8ddeEp-A" %}
Introduction to Life Cycle Methods
{% endembed %}

#### Example: Clock Component

{% embed url="https://youtu.be/B_84fHdVFFk" %}
React Clock Component - Life Cycle Methods
{% endembed %}

{% embed url="https://youtu.be/BvAzQeph52Q" %}
React Clock Component - ComponentWillUnmount
{% endembed %}

## Day 7

### 6: [Handling Events](https://legacy.reactjs.org/docs/handling-events.html)

1. "Events on DOM elements" are the same as [JavaScript events or HTML events](https://www.w3schools.com/js/js\_events.asp). JS events allow us to perform logic on events that happen on our web pages such as mouse clicks. React supports a [wide range of events](https://reactjs.org/docs/events.html#supported-events).
2. `condition ? true : false` syntax is the [JavaScript conditional operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Conditional\_Operator).
3. Rocket recommends using the "public class fields syntax" to define callback methods (functions are called methods when inside classes) inside class components. We will be using Create React App to build React apps which enables this syntax by default.

{% embed url="https://youtu.be/3pG3SKBSnSY" %}
React Events
{% endembed %}

### 7: [Conditional Rendering](https://legacy.reactjs.org/docs/conditional-rendering.html)

1. Conditional rendering is one of the most powerful features of React, enabling us to use conditional logic to specify what a component should render.

### 8: [Lists and Keys](https://legacy.reactjs.org/docs/lists-and-keys.html)

1. Rocket recommends always using keys when rendering JSX elements in a list for performance reasons.

## Day 9

### 9: [Forms](https://legacy.reactjs.org/docs/forms.html)

1. An [HTML form](https://www.w3schools.com/html/html\_forms.asp) is an HTML element that either refreshes the page or navigates to a new page when the user submits the form. We often do not want this behaviour in React, opting to update UI on submit without refresh. To disable "refresh on submit" behaviour, Rocket recommends the technique in the React docs, to provide the `form` a `handleSubmit` callback function that calls `event.preventDefault`.
2. When hanlding the submit method from a form you should target the `event.target.value` to get the current value of an input.&#x20;

{% embed url="https://youtu.be/Jm3C7WuVsIE" %}
Building React Form State
{% endembed %}

{% embed url="https://youtu.be/_6iwcPewd6A" %}
Binding state and handlingChange
{% endembed %}

## Day 10

### 10: [Lifting State Up](https://legacy.reactjs.org/docs/lifting-state-up.html)

1. It is important that we pass both the temperature value and handle-change function from `Calculator` to `TemperatureInput` so the app can maintain only 1 "source of truth" state for temperature value in `Calculator`. If it helps, Rocket recommends drawing the component hierarchy to visualise how data flows in the application and verifying our understanding with our classmates and section leader.

{% embed url="https://youtu.be/CuDqDjytMmM" %}
Why lift up state?
{% endembed %}

#### Example: Building a Blog List

{% embed url="https://youtu.be/j8RqUGBIL3Y" %}
Defining initial state / data and using that data
{% endembed %}

{% embed url="https://youtu.be/2pZMTJYNyPg" %}
Creating a Blog Component within the BlogList, passing down state as props
{% endembed %}

{% embed url="https://youtu.be/yYvtG4SERq0" %}
Powering the Blog functions with methods in the BlogList, passing functions as props
{% endembed %}

{% embed url="https://youtu.be/TFmNJ9HcHo8" %}
Creating a BlogComposer with internal logic
{% endembed %}

{% embed url="https://youtu.be/0fc-_emvEbc" %}
Lifting up state
{% endembed %}

## Day 11

### 11: [Composition vs Inheritance](https://legacy.reactjs.org/docs/composition-vs-inheritance.html)

1. Composition vs inheritance is an architectural paradigm of React where React prefers composing components with other components, instead of defining parent-child inheritance relationships like with traditional OOP classes.&#x20;

## Day 12

### 12: [Thinking In React](https://legacy.reactjs.org/docs/thinking-in-react.html)

1. [JSON](https://www.w3schools.com/js/js\_json\_intro.asp) (JavaScript Object Notation) is a data format similar to JavaScript Objects, except can be used in text or file form. An API (Application Programming Interface) is typically a URL that manipulates and/or returns data. A JSON API is an API that returns data in JSON format, one of the most common formats to send and receive data on the internet.
2. Review 10: Lifting State Up above for a refresher on passing "callbacks" (i.e. callback functions) to descendant components to update shared state in ancestor components.

### [Tutorial: Intro to React](https://legacy.reactjs.org/tutorial/tutorial.html)

If you finish the React Guide pages above early, feel free to start and finish this tutorial early to have more time for [Project 1](../1.p-frontend-app.md).

1. Rocket recommends starting with Setup Option 1 (Write Code in Browser) to focus on understanding React. If you finish the tutorial and have time, do Setup Option 2 (Local Development Environment) and port your code over to understand how to use Create React App. We will use Create React App to develop all frontend projects at Rocket.
2. Rocket recommends using [React DevTools](https://chrome.google.com/webstore/detail/react-developer-tools/fmkadmapgofadopljbjfkapdkoienihi?hl=en) whenever developing React apps. It can help us debug quicker.
3. Note the tutorial's recommendation to use `on[Event]` naming convention for props that represent events and `handle[Event]` for methods that handle events.

## Post-Class Exercises: Codecademy React 101

Complete all exercises in the following Codecademy lessons when they are assigned in the Rocket course schedule.

1. JSX
   1. [Intro to JSX](https://www.codecademy.com/courses/react-101/lessons/react-jsx-intro/exercises/why-react)
   2. [Advanced JSX](https://www.codecademy.com/courses/react-101/lessons/react-jsx-advanced/exercises/jsx-classname-class)
2. React Components
   1. [Your First React Component](https://www.codecademy.com/courses/react-101/lessons/your-first-react-component/exercises/hello-world-component)
   2. [Components and Advanced JSX](https://www.codecademy.com/courses/react-101/lessons/react-components-advanced-jsx/exercises/render-multiline-jsx)
3. Components Interacting
   1. [Components Render Other Components](https://www.codecademy.com/courses/react-101/lessons/components-render-each-other/exercises/components-interacting-intro)
   2. [this.props](https://www.codecademy.com/courses/react-101/lessons/this-props/exercises/this-props-intro)
4. [React Forms](https://www.codecademy.com/courses/react-101/lessons/react-forms/exercises/react-forms-intro)

{% hint style="info" %}
**New to Rocket Academy?**

If you're not enrolled in Rocket's Bootcamp and visiting this page, [check out our website](https://www.rocketacademy.co/courses/bootcamp-course) to learn more about our Bootcamp course!
{% endhint %}
