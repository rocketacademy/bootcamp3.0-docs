# 0.4.6: Promises

## Learning Objectives

1. JavaScript Promises allow us to program logic to run after asynchronous function calls return, e.g. network requests that take an indefinite amount of time.
2. Promises are an alternative to callback functions and often a "cleaner" syntax due to fewer levels of nesting.

## Introduction

JavaScript Promises allow us to program logic to run after asynchronous function calls return, for example if we wanted to highlight a like button after we have saved the "like" in our database. The same logic would be possible with callback functions, but promises allow us to achieve the same functionality with at most 1 level of nesting.

## Example with Axios

[Axios](https://axios-http.com) is a promise-based HTTP library that allows us to make arbitrary HTTP requests in code. "Promise-based" means Axios functions return promises, allowing us to run certain logic only when the promises "resolve", i.e. when the requests are completed.

### `.then` Method

The function `axios.get` sends a GET request and returns a promise, on which we then call the promise's `.then` method to perform certain logic only when the GET request is complete, i.e. when we receive a response. 3rd-party asynchronous functions such as `axios.get` often return promises for this purpose, and when unsure we can check their [online documentation](https://axios-http.com/docs/api\_intro).

The following code sends a request, then `console.log`s the response when the response is received.

```javascript
import axios from "axios";

// Make a request
axios.get("http://dog.ceo/api/breeds/image/random").then((response) => {
  // Handle request success
  console.log(response);
});
```

The previous code can be rewritten as follows for a clearer breakdown of how `.then` works.

```javascript
import axios from "axios";

// Perform logic after the request is complete.
const handleResponse = (response) => {
  // Handle request success
  console.log(response);
};

// Make a request and store return value (promise) in getRequestPromise
const getRequestPromise = axios.get("http://dog.ceo/api/breeds/image/random");

// Tell the program to call handleResponse when getRequestPromise resolves.
getRequestPromise.then(handleResponse);
```

Note that `handleResponse` receives a `response` parameter. Because the above promise is for an Axios request, the callback function receives an [Axios response object](https://axios-http.com/docs/res\_schema) as a parameter.

### Sequential Promises

Sometimes we may wish to perform multiple network calls sequentially. For example, when a user requests to change their password, we may wish to:

1. Send a request to change their password
2. When that request is complete, send an email through an email API
3. Render a success message after the email is sent

```javascript
axios
  .post(`https://myapp.com/change-password`, { password: "rocket123" })
  .then((response) => axios.get(`https://myapp.com/send-email`))
  // Render password change success
  .then((response) => console.log("success!"));
```

`.then` always returns a promise, regardless of whether the callback function passed to `.then` returns nothing, a promise, or anything else. Hence we can always call `.then` on the return value of any `.then` call. See [`.then` docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global\_Objects/Promise/then) for a more detailed description of this behaviour.

## Additional Resources

1. [Intuitive and deeper explanation of JavaScript Promises](https://javascript.info/promise-basics)
