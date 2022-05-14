# 2.3.2: React Router

## Learning Objectives

1. React Router allows us to keep our app URLs in sync with components we are viewing.
2. How to use React Router

## Introduction

React Router is a React library that enables us to keep our app URLs in sync with components we are viewing. Prior to React Router our app URL would never update, which is fine for single-page apps but less good when our apps get more complex.

Scroll through the [React Router homepage](https://reactrouter.com/) for a visual motivation for React Router.

## Official Tutorial

Complete the official React Router tutorial to familiarise yourself with React Router. Rocket recommends we use the online IDE StackBlitz that the tutorial recommends to complete the tutorial. Once we learn the mechanics of React Router we will integrate it into our apps with Create React App.

{% embed url="https://reactrouter.com/docs/en/v6/getting-started/tutorial" %}
React Router official tutorial
{% endembed %}

1. We will not be using Remix at Rocket, the other framework mentioned in the tutorial
2. Pay attention to how we can use nested `Route`s and the `Outlet` component to re-use components with React Router
3. Always add the "no match" case in our apps for robustness
4.

## Old

Basic Example from here: [https://codesandbox.io/s/competent-mclaren-ezyg1](https://codesandbox.io/s/competent-mclaren-ezyg1)

```jsx
import React from "react";
import { BrowserRouter as Router, Switch, Route, Link } from "react-router-dom";

export default function App() {
  return (
    <Router>
      <div>
        <nav>
          <ul>
            <li>
              <Link to="/">Home</Link>
            </li>
            <li>
              <Link to="/about">About</Link>
            </li>
            <li>
              <Link to="/users">Users</Link>
            </li>
          </ul>
        </nav>

        {/* A <Switch> looks through its children <Route>s and
            renders the first one that matches the current URL. */}
        <Switch>
          <Route path="/about">
            <About />
          </Route>
          <Route path="/users">
            <Users />
          </Route>
          <Route path="/">
            <Home />
          </Route>
        </Switch>
      </div>
    </Router>
  );
}

function Home() {
  return <h2>Home</h2>;
}

function About() {
  return <h2>About</h2>;
}

function Users() {
  return <h2>Users</h2>;
}
```
