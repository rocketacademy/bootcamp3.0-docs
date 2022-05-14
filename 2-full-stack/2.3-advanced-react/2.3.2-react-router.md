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
4. Note we need to import the React Router React Hook `useParams` from `react-router-dom` to get URL params
5. We can skip the section on Custom Behaviour; those use cases will most likely not apply to us and we can come back to this when we need to.
