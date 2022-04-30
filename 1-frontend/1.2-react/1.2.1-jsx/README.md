# 1.3.1: JSX

## Introduction

```jsx
const element = <h1>Hello World!</h1>;
```

JSX is a **"syntax extension"** to JavaScript (JS) that allows us to specify HTML elements directly in JS. We use JSX with React to specify elements we want React to manipulate. \
\
This module will walk through the creation of a sample app using JSX.

## Setup

### Clone Repo

Clone the [base Webpack repo](https://github.com/rocketacademy/webpack-mvc-base-bootcamp).

### Install Packages

Install React libraries and Babel preset for React.

```bash
npm install --save-dev react react-dom @babel/preset-react
```

### Update Webpack Config to Support React

1. In the`webpack.common.js` file, ensure that the `test` [regular expression](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions) includes the new file extension, `.jsx`.
2. Add the React preset to the `presets` key.

```javascript
{
  // Regex to decide which files to run Babel on
  test: /\.(js|mjs|jsx)$/,
  exclude: /node_modules/,
  use: {
    loader: require.resolve('babel-loader'),
    options: {
      presets: ['@babel/preset-env', '@babel/preset-react'],
    },
  },
},
```

### Sample Webpack config

The full Webpack common config should look like the following.

{% code title="webpack_conf/webpack.common.js" %}

```javascript
const HtmlWebpackPlugin = require("html-webpack-plugin");
const MiniCssExtractPlugin = require("mini-css-extract-plugin");
const path = require("path");

module.exports = {
  entry: {
    main: "./src/index.js",
  },
  output: {
    filename: "[name]-[contenthash].bundle.js",
    path: path.resolve(__dirname, "../dist"),
    // Replace previously-compiled files with latest one on each build
    clean: true,
  },
  plugins: [
    new HtmlWebpackPlugin({
      // Name this file main so it does not get automatically requested as a static file
      filename: "main.html",
      template: path.resolve(__dirname, "..", "src", "main.html"),
    }),
    new MiniCssExtractPlugin(),
  ],
  module: {
    rules: [
      {
        // Regex to decide which files to run Babel on
        test: /\.(js|mjs|jsx)$/, // CHANGE HERE: jsx added
        exclude: /node_modules/,
        use: [
          {
            loader: "babel-loader",
            options: {
              // CHANGE HERE: ensure @babel/preset-react
              presets: ["@babel/preset-env", "@babel/preset-react"],
            },
          },
        ],
      },
      {
        test: /\.scss$/,
        use: [MiniCssExtractPlugin.loader, "css-loader", "sass-loader"],
      },
    ],
  },
};
```

{% endcode %}

## JSX Syntax

Below is a comparison between how a div with inner text is created using DOM, React, and JSX syntax respectively. While React can be written without using JSX, as seen in the example below, we will be writing React code using JSX syntax, combining the best of React with JSX. React without JSX is for [nuanced purposes that we are not addressing in this course](https://reactjs.org/docs/react-without-jsx.html).

Try running the JSX code in your Chrome DevTools - there will a syntax error.

{% hint style="info" %}
Babel is used in the Webpack config to help automatically transform JSX to React.&#x20;

Note that `@babel/preset-env` needs to be specified before `@babel/preset-react` so that ES6 gets transformed to ES5 before JSX gets transformed to React.

```javascript
presets: ['@babel/preset-env', '@babel/preset-react'],
```

{% endhint %}

### **DOM JavaScript**

```jsx
const myEl = document.createElement("div");
myEl.innerText = "Hey Wow!";
```

### **React JavaScript**

```jsx
const myEl = React.createElement("div", null, "Hey Wow!");
```

### **JSX**

```jsx
const myEl = <div>Hey Wow!</div>;
```

## Minimal JSX App

We are rendering a div element using React and JSX.&#x20;

We typically set up React in `index.js` using React's imported `createRoot` function to create a root component from a root DOM element. We render the React app inside the root component with `rootComponent.render`.

{% code title="src/index.js" %}

```jsx
import React from "react";
import { createRoot } from "react-dom/client";
import "./styles.scss";

// Create JSX element and log it.
const myEl = <div>Hey Wow!</div>;
console.log("myEl: ", myEl);

// Create root element to render other elements into, add root element to DOM.
const rootElement = document.createElement("div");
document.body.appendChild(rootElement);

// Create React root component with root DOM element
const rootComponent = createRoot(rootElement);

// Render the myEl JSX element in the root component
rootComponent.render(myEl);
```

{% endcode %}

Run the `watch` command to have Webpack auto-compile our code.

```jsx
npm run watch
```

Run our Express server **in a new terminal** to serve our website.

```jsx
npx nodemon index.mjs
```

Visit [http://localhost:3004/home](http://localhost:3004/home) in Chrome to view our element.

## Using CSS Classes with React

In JSX and React, HTML elements can't have a `class` attribute because the HTML `class` keyword conflicts with JavaScript's `class` keyword. JSX has chosen to replace `class` with `className`. React will translate `className` to `class` such that our browsers know what CSS to apply.

To add CSS styles to a React app, import a CSS file like in the following code sample. The following code assumes there is a CSS class `hero-text` defined in `./styles.css`.

```jsx
import "./styles.css";

const myEl = <div className="hero-text">Hey Wow!</div>;
```

## JSX with Multiple HTML Elements

So far we've used JSX to create a single HTML element and rendered that element onto our page. Our equivalent DOM code would be the same length or shorter. The real benefit of JSX is the ability to specify a set of nested elements in the same way we would write HTML. How many lines would the equivalent DOM code be?

There are a couple of rules when writing longer JSX:

1. Surround _multi-line JSX expressions_ with parentheses `()`.
2. Each JS variable contains at most 1 JSX element. Note the `myEl` variable contains a single element (c.f. below: a single `<div></div>` tag as the parent) even though it has other elements inside it.

{% code title="src/index.js" %}

```jsx
import React from "react";
import { createRoot } from "react-dom/client";

// Create JSX element and log it.
const myEl = (
  <div>
    <h1 className="hero-text">
      Hey <span className="warning">Wow!</span>
    </h1>
    <p>Lorem Ipsum!!</p>
  </div>
);
console.log("myEl: ", myEl);

// Create root element to render other elements into, add root element to DOM.
const rootElement = document.createElement("div");
document.body.appendChild(rootElement);

// Create React root component with root DOM element
const rootComponent = createRoot(rootElement);

// Render the myEl JSX element in the root component
rootComponent.render(myEl);
```

{% endcode %}

## JSX Templating with Data

### Basic Templating Example

It is possible to inject JS variables into JSX, similar to how we injected JS variables into EJS. EJS uses `<%= %>` syntax; JSX uses `{}`.&#x20;

In the following example, we initialise a number on line 4 and use it on line 12.

{% code title="src/index.js" %}

```jsx
import React from "react";
import { createRoot } from "react-dom/client";

const myRandomNum = Math.random();

// Create JSX element and log it.
const myEl = (
  <div>
    <h1 className="hero-text">
      Hey <span className="warning">Wow!</span>
    </h1>
    <p>Random Value: {myRandomNum}</p>
  </div>
);
console.log("myEl: ", myEl);

// Create root element to render other elements into, add root element to DOM.
const rootElement = document.createElement("div");
document.body.appendChild(rootElement);

// Create React root component with root DOM element
const rootComponent = createRoot(rootElement);

// Render the myEl JSX element in the root component
rootComponent.render(myEl);
```

{% endcode %}

### Templates Accept Any JS Code

Curly braces in JSX can contain any valid JavaScript code.

```jsx
const myEl = (
  <div>
    <h1 className="hero-text">
      Hey <span className="warning">Wow!</span>
    </h1>
    <p>Random Value: {Math.random() * 100}</p>
  </div>
);
```

### Template Substitution Also Works in Element Attributes

JSX also allows templating of HTML attribute values, not just HTML element contents. We need not specify quotations around HTML attribute values. In the following example we initialise a URL string, `myUrl`, on line 1 and use it in an `href` attribute on line 7.

```jsx
const myUrl = "http://google.com";
const myEl = (
  <div>
    <h1 className="hero-text">
      Hey <span className="warning">Wow!</span>
    </h1>
    <a href={myUrl}>Random Value: {Math.random() * 100}</a>
  </div>
);
```

## Further Reading

Read more about JSX on the official docs: [https://reactjs.org/docs/introducing-jsx.html](https://reactjs.org/docs/introducing-jsx.html)

## Exercise

Replicate the above code.
