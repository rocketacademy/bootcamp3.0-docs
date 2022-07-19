# 4.1: Testing

## Learning Objectives

1. Programmatic software testing is a crucial feature of software development that all tech companies practice
2. Programmatic testing allows us to quickly verify we did not break existing features when building new ones
3. Programmatic testing involves writing code to test our code
4. There are 3 general categories of programmatic tests: unit tests, integration tests and end-to-end tests

## Introduction

Every mature software product has software tests to verify intended functionality. Without software tests, every time we write a new feature we might not know whether we broke an existing one. This lack of clarity can cause stress, especially when existing features are crucial to user experiences. Engineers working on early-stage products often omit writing tests because their product requirements change often, but once product requirements start to stabilise and mature, testing is necessary to maintain engineer sanity.

Software tests are code written using 1 or more test frameworks that programatically verify that functions, groups of functions, or entire features produce expected output when provided with specific input. Engineers typically merge these tests to repos at the same time they merge the tested feature, guaranteeing tests for every feature in the product. Some engineers prefer to write tests before writing the feature (aka test-driven development), and others prefer to write tests after or while writing the feature (more common).

There are 3 most common categories of software tests: unit tests, integration tests and end-to-end tests. Unit tests typically test individual functions, especially ones with non-trivial logic such as calculations. Integration tests typically test groups of functions, for example a function that triggers functionality in multiple helper functions. End-to-end tests typically test entire features by using frameworks to simulate user actions, and verifying that those actions cause the desired database and UI changes in the app. Unit tests are the simplest and most common form of testing, and engineers often omit end-to-end testing until their product matures.

## Unit Testing in JavaScript

For illustration purposes we will demonstrate a unit test in JavaScript. We will write a unit test for one of our backend functions, since backend functionality tends to change less often than frontend UI.

Mocha and Chai are common test frameworks used together to test JavaScript backends. Mocha is the framework that enables us to run tests. It provides functions in which we can write tests, and a test runner script we can use to run all of a subset of our tests. Chai is an "assertion framework" that allows us to verify values in our code match what we expect, values such as the return value of the function we are testing.

TODO(kai): Make example with more realistic code if possible

### Setup

Let's get a simple test running with a bare-bones Mocha and Chai setup.

Clone the base repo and install the libraries.

```bash
git clone https://github.com/rocketacademy/base-node-bootcamp.git mocha
```

```javascript
cd mocha
```

```javascript
npm install mocha chai
```

Mocha expects a directory called test that holds the test files.

```javascript
mkdir test
```

For this example we'll create a simple calculator to test.

```javascript
touch calculator.js
```

#### calculator.js

```javascript
export default function add(a, b) {
  return a + b;
}
```

Because we are doing unit testing, we are creating a library module to use as in this `index.js` below.

#### index.js

```javascript
import { add } from "./calculator.js";

console.log(add(2, 3));
```

However, we won't be testing any functionalities inside the `index.js` itself. We'll only be running code in the `caluclator.js` file.

Now let's create the file that will run our tests.

#### test/calculator.js

```javascript
import { expect } from "chai";

import { add } from "../calculator.js";

describe("Calculator", function () {
  describe("Basic Operations", function () {
    it("Adds two numbers", function () {
      const result = add(2, 2);
      expect(result).to.equal(4);
    });
  });
});
```

To run the tests, make a change to the `package.json`:

```javascript
{
  "name": "base-node-swe1",
  "version": "1.0.0",
  "description": "# basic-node-swe1",
  "main": "index.js",
  "scripts": {
    "test": "mocha"
  },
  "repository": {
    "type": "git",
    "url": "git+https://github.com/rocketacademy/base-node-swe1.git"
  },
  "keywords": [],
  "author": "",
  "type": "module",
  "license": "ISC",
  "bugs": {
    "url": "https://github.com/rocketacademy/base-node-swe1/issues"
  },
  "homepage": "https://github.com/rocketacademy/base-node-swe1#readme",
  "dependencies": {
    "chai": "^4.3.3",
    "mocha": "^8.3.1"
  },
  "devDependencies": {
    "eslint": "^7.12.1",
    "eslint-config-airbnb-base": "^14.2.0",
    "eslint-plugin-import": "^2.22.1",
    "nodemon": "^2.0.6"
  }
}
```

On line 7 we changed the test key so that Mocha will run:

```javascript
npm run test
```

We should then see output like this:

![](../../.gitbook/assets/screen-shot-2021-03-11-at-1.45.24-am.png)

Let's talk about the test code and the test run output.

### Describe

On line 5 & 6 of `test/calculator.js` we are calling the `describe` function. This function segregates the different tests and formats the output according to what was called inside these functions.

### It

`it` is the smallest piece of a unit test suite. The first argument to `it` is a string that describes what this code is testing.

```javascript
it("Adds two numbers", function () {
  const result = add(2, 2);
  expect(result).to.equal(4);
});
```

#### Expect

Expect is the code that actually evaluates that a result is correct. In this case we are checking for the number 4. There are many other kinds of comparisons besides `to.equal`.

## Further Reading

1. [Mocha website](https://mochajs.org/)
2. [Chai documentation](https://www.chaijs.com/api/bdd/)
3. [Mocha & Chai tutorial](https://semaphoreci.com/community/tutorials/getting-started-with-node-js-and-mocha)

## Exercises

1. Run the above code
2. Run the test to see the output
3. Break the test on purpose to see what a failing test looks like
4. Add a `multiply` function to the calculator and write a test for it
