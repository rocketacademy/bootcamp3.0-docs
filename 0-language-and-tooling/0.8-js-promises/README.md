# 0.8: JS Promises

## Introduction

Promises are a JavaScript tool to avoid many levels of nested callbacks for asynchronous logic. To achieve this, Promises allow us to run certain logic only after a Promise "resolves", meaning the asynchronous functionality is complete, and we can "chain" this logic so that the logic reads sequentially instead of nested.

We will first look at the usage of Promises with `.then`, the most common way to use Promises, and then we'll review how to create Promises ourselves.

## Example: Axios

[Axios](https://www.npmjs.com/package/axios) is a Promise-based HTTP library that allows us to make arbitrary HTTP requests in code. Axios is Promise-based in the sense that Axios functions return Promises, allowing us to run certain logic only when the Promises resolves, i.e. when the request is completed.

To set up the example, we install Axios via NPM.

```text
npm install axios
```

### `.then` Method

The function `axios.get` returns a Promise, on which we then use the `.then` method to perform certain logic only when the request is complete, i.e. when we receive a response. 3rd-party asynchronous functions such as `axios.get` often have Promise support, where we can depend on the functions to return Promises such that we can use `.then` logic. 3rd-party libraries will document whether they support Promises.

The following code sends a request, then `console.log`s the response when the response is received.

```javascript
import axios from 'axios';

// Make a request
axios.get('http://dog.ceo/api/breeds/image/random').then((response) => {
  // Handle request success
  console.log(response);
});
```

The previous code can be rewritten as follows for a clearer breakdown of how `.then` works.

```javascript
import axios from 'axios';

// Make a request
const getRequestPromise = axios.get('http://dog.ceo/api/breeds/image/random');

// Define the callback
const whenRequestHasResponse = (response) => {
  // Handle request success
  console.log(response);
};

// Tell the program to call the callback on request success.
getRequestPromise.then(whenRequestHasResponse);
```

### Sequential, not Nested Callbacks

One of the worst parts of JavaScript callbacks is the fact that if you want four things to happen in order, you have to nest them. They become unreadable when you have many code blocks inside of other blocks. With Promises you can keep everything to mostly 1 level of nesting.

Here is an example of 3 sequential requests that would have required 3 levels of nested callbacks without Promises. `myAddr` variables are fictitious. `.then` functions always return a promise, no matter what is returned from their inner callback. More on this behaviour [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise/then).

```javascript
axios
  .get(
    `https://maps.googleapis.com/maps/api/geocode/json?&address=${myAddr1}`
  )
  .then((response) =>
    axios.get(
      `https://maps.googleapis.com/maps/api/geocode/json?&address=${myAddr2}`
    )
  )
  .then((response) =>
    axios.get(
      `https://maps.googleapis.com/maps/api/geocode/json?&address=${myAddr3}`
    )
  )
  .then((response) => console.log(response));
```

## Creating Promises

It's rare to create Promises unless we are building a library, but knowing some of the mechanics can be helpful.

`Promise` is a built-in [JavaScript "class"](https://www.w3schools.com/js/js_classes.asp). To create a Promise, we use `new Promise(<CALLBACK>)` syntax, where the parameter to the `Promise` "class constructor" is a callback function that takes 2 parameters: `resolve` and `reject`. The callback function typically invokes asynchronous functionality, and `resolve` and `reject` are functions that should get called when the asynchronous functionality completes successfully or fails to complete respectively. A call to `resolve` is what triggers the `.then` callback where the Promise is used. A call to `reject` will trigger a `.catch` callback where the Promise is used, if `.catch` is specified.

In the following example, we call `resolve` when the timeout is finished and it kicks off the `.then` callback where `myFirstPromise` is used. Note that we do not have an error case that calls `reject`. For proper error handling, we would call `reject` on error and catch it where the Promise is used with a `.catch` block. More information on Promise error handling [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise/catch).

```javascript
console.log('creating promise');
const myFirstPromise = new Promise((resolve, reject) => {
  // We call resolve(...) when what we were doing asynchronously was successful.
  // We call reject(...) when what we were doing asynchronously failed.
  // In this example, we use setTimeout(...) to simulate async code.
  // In reality, you will probably be using something like AJAX.
  console.log('setting timeout');
  setTimeout(() => {
    console.log('timeout done, calling resolve');
    resolve('Success!'); // Yay! Everything went well!
    console.log('done calling resolve');
  }, 250);
  console.log('done setting timeout');
});

console.log('about to set .then callback');
myFirstPromise.then((successMessage) => {
  // successMessage is whatever we passed into the resolve(...) function above.
  // It doesn't have to be a string, but if it is only a succeed message, it probably will be.
  console.log(`Yay! ${successMessage}`);
  console.log('done calling .then');
});
console.log('done setting then callback');
```

