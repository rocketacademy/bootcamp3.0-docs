---
description: ReactJs Styling
---

# Styling in ReactJs

Learning Objectives

1. Understand how to implement Style within a ReactJs context
2. Style Components using in-line style
3. Style Components using Stylesheet and classes

## Introduction

In a previous section we introduced CSS, which is used to apply styles to HTML pages beautifying content. Within ReactJs we can use CSS in order style our rendered output, you can apply any CSS style within React. We can use the boilerplate code that is generated from the npx Create React Application, we actually have some built in styling. Below is an example of the boilerplate output.

<figure><img src="../../.gitbook/assets/Screenshot 2022-12-15 at 1.08.08 PM.png" alt=""><figcaption><p>Create React Application</p></figcaption></figure>



### In-line Styling

To apply style in ReactJs we can apply in-line style. This has the highest level of CSS precedence as it is evaluated last by the browser, at this stage the component is being styled by a stylesheet, but we can override this. To demonstrate this we will alter the text 'Edit src ....' such that it is bold and red.

Go to the App.js file, alter the parent div of your local code to reflect the block below:

{% code lineNumbers="true" %}
```jsx
 <div className="App">
      <header className="App-header">
        <img src={logo} className="App-logo" alt="logo" />
        <p style={{ color: "Red", fontWeight: "bold" }}>
          Edit <code>src/App.js</code> and save to reload.
        </p>
        <a
          className="App-link"
          href="https://reactjs.org"
          target="_blank"
          rel="noopener noreferrer"
        >
          Learn React
        </a>
      </header>
    </div>
```
{% endcode %}



Notice how the opening p tag on line 4 contains a style property which equals to a double set of curly braces. This code specifies a style object, the properties within must be camelCased and the values must be written in strings. Moreover each property and value should be seperated by a common.

This is the resulting render in the browser.

<figure><img src="../../.gitbook/assets/Screenshot 2022-12-15 at 1.25.46 PM.png" alt=""><figcaption><p>Create React Application In-line style</p></figcaption></figure>

### Stylesheets React

Another way one can apply style within Reactjs is through the stylesheet, as stated previously the App.js component is already affect by some boilerplate style. We can alter the content further by adding new classes into the App.css stylesheet and by adding new classes to our App.js code.&#x20;

Lets change the link below to remove all text decoration such that we can apply our own style.

Alter your App.css, target the App-link class to reflect the code below:

```css
.App-link {
  color: #3324bd;
  font-weight: bold;
  text-decoration: none;
  border: 2px solid #ff0000;
  background-color: #ffffff;
}
```

The output should look like this within the browser.

<figure><img src="../../.gitbook/assets/Screenshot 2022-12-15 at 1.34.42 PM.png" alt=""><figcaption><p>Create React Application Stylesheet</p></figcaption></figure>

Stylesheets are used within the Application by importing them at the top of the component. The full component should be similar to the code below.

{% code lineNumbers="true" %}
```jsx
import logo from "./logo.svg";
import "./App.css";

function App() {
  return (
    <div className="App">
      <header className="App-header">
        <img src={logo} className="App-logo" alt="logo" />
        <p style={{ color: "Red", fontWeight: "bold" }}>
          Edit <code>src/App.js</code> and save to reload.
        </p>
        <a
          className="App-link"
          href="https://reactjs.org"
          target="_blank"
          rel="noopener noreferrer"
        >
          Learn React
        </a>
      </header>
    </div>
  );
}

export default App;
```
{% endcode %}

In the component above we can see that we apply classes to JSX tags using the property className. It is possible to apply more than one class to a JSX tag just like in HTML.
