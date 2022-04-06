# 1.2: DOM Review

## Introduction

The DOM \(Document Object Model\) is a set of nodes that represent the elements in an HTML document. Browsers generate the DOM automatically when they load HTML. The DOM is the interface through which our JS logic can update what's on screen and determine how user actions manipulate our UI.

![](../../.gitbook/assets/img_0018.png)

{% embed url="https://youtu.be/AP8YcJ9MR64" caption="" %}

## DOM Inputs and Outputs

HTML differs from JS in that HTML has no logic, no control flow, and no dynamic data. The DOM allows us to use JS to manipulate HTML dynamically, where users provide input and JS modifies our HTML \(through the DOM\) to display relevant output. The following are potential DOM inputs and outputs.

#### Potential Inputs

- Any user mouse movement within the browser screen.
- Any element on the page they've clicked on.
- Any radio button, drop down or checkbox they've interacted with.

#### Potential Outputs

- Any HTML element, with any CSS style applied to it.

JS and the DOM allow us to receive any user interaction on a page and update that page's HTML accordingly.

## How to Use the DOM

In practice, the DOM is the set of JS variables that represent all browser functionality. `console.log` is an example of 1 such variable `console`, which allows us to output values in the browser console. Similarly, we will use other DOM variables to accept user inputs and provide outputs in the form of HTML elements.

Other than `console`, the major variables that represent the DOM are `window` and `document`. We can think of these variables as an API \(Application Programming Interface\) for the browser, where we can only perform logic that the browser allows us to via the `window` and `document` interfaces.

## Exercises

### Window and Document Variables

1. Open the browser console and type `window` and `document`, 1 on each line, to see their values.
2. Click the triangles next to the output to see inside the variables. What is there?

### Handle User Interactions as Input "Events"

1. Look up how to "listen" for any HTML event: [https://www.w3schools.com/jsref/met_document_addeventlistener.asp](https://www.w3schools.com/jsref/met_document_addeventlistener.asp)
2. You may also see this syntax which sets a callback function without storing that function in a separate variable. Such callback functions are called "**anonymous functions**"

```javascript
button.addEventListener("click", function () {
  console.log("clicked");
});
```

### Create Any HTML Output Using JS

1. Create an HTML element with JS: [https://www.w3schools.com/jsref/met_document_createelement.asp](https://www.w3schools.com/jsref/met_document_createelement.asp)
2. Add the element to the page with `appendChild`: [https://www.w3schools.com/jsref/met_node_appendchild.asp](https://www.w3schools.com/jsref/met_node_appendchild.asp)

### Implement Basic DOM Manipulation with Starter Code

Implement basic DOM manipulation with the code provided below.

1. Read comments in below code to understand what's happening
2. Clone this repo: [https://github.com/rocketacademy/dom-starter-bootcamp](https://github.com/rocketacademy/dom-starter-bootcamp)
3. Don't forget to [run npm install in the starter code directory.](../../course-logistics/required-hardware-and-software.md#eslint-npm-configuration-libraries)
4. Implement the below code in your copy of the repo

The following elements are manipulated by our JS using the DOM interface

{% code title="index.html" %}

```html
<p>
  <input id="starter-ex" />
</p>
<button id="starter-button">submit me</button>
```

{% endcode %}

{% code title="script.js" %}

```js
// make a variable out of the input and button
var input = document.querySelector("#starter-ex");
var button = document.querySelector("#starter-button");

// call this function
var myButtonClicked = function () {
  // get the current value that's been typed into the input
  var typedValue = input.value;

  // create a new h2
  var newHtwo = document.createElement("h2");

  // set the text inside this new element
  newHtwo.innerText = typedValue;

  // make the h2 appear on screen
  document.body.appendChild(newHtwo);

  // empty out the HTML input
  input.value = "";
};

// say which function to call *when* the user clicks the button
button.addEventListener("click", myButtonClicked);
```

{% endcode %}
