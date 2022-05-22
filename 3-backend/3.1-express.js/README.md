# 3.1: Express.js

## Learning Objectives

1. Express.js is a server application framework that allows us to quickly set up server applications to receive requests from clients and respond with data.

## Introduction

Express.js is a JavaScript server application framework that allows us to quickly set up server applications. Servers are computers without a screen that receive requests from clients and respond with data. This is also the general purpose of the "backend".

## Basic Express App

TODO: Example with just the listener and "Hello World" response. Stackblitz?

## Routes

Express sets the request listener only for a specific path `/` with `app.get`. This allows Express to provide different request handler callbacks for each type of request it gets, greatly improving the decomposition of our server. It allows Express to support larger applications with more types of requests.

Express methods like `app.get` are called "**routing methods**", and they help Express send each request to the relevant request handlers. We often refer to routing methods as "**routes**" for short. There are 2 ways in which routing methods filter requests: HTTP Methods and URL Paths.

#### Sample Express Routing Method

```javascript
app.get("/", handleIncomingRequest);
```

### HTTP Methods

Express routing methods are named after HTTP methods. To designate a request handler for a GET method we would use `app.get`. To set a request handler for a POST method we would use `app.post`. The same applies for PUT and DELETE.

### URL Path

The first parameter to Express routing methods is a URL path matcher, also called a "route". This means Express forwards requests whose HTTP method matches the routing method and whose URL path matches the path parameter to the corresponding request handler.

For example, a GET request to the following URL...

```bash
http://localhost:3004/wow-bananas
```

...would match the following routing method, sending the request to the `handleIncomingRequest` callback.

```javascript
app.get("/wow-bananas", handleIncomingRequest);
```

We could give our paths random names like `wow-bananas`. However, best practice is to name application paths more precisely, to help app users better anticipate what we will show them.

## Middleware

Routing methods of the format `app.<METHOD>` are 1 form of Express "middleware", where middleware are functions with access to Express request and response objects, that are executed in the order they are bound to the `app` object, until any middleware sends a response back to the client.

**Middleware is a crucial topic in Express, because all Express logic happens through middleware. We recommend students read more about Express middleware** [**here**](https://expressjs.com/en/guide/using-middleware.html)**.**

## Exercises

### Dice Roll

1. Create an Express app that rolls a dice when the user sends a request to the `/dice-roll` route.
2. Send a response back to the client with the dice roll value.
3. Format the response output so it's easy to read.

### Two Dice Rolls

1. Add another "route" to the app `/two-dice-rolls` that rolls two dice and outputs their values to the client.
2. Request `/two-dice-rolls` with Chrome and with `curl`. Verify we get the same responses.

## Additional Resources

Past students have found the following videos helpful in introducing Express routing middleware and Express middleware in general.

1. [https://www.youtube.com/watch?v=JlgKybraoy4](https://www.youtube.com/watch?v=JlgKybraoy4)
2. [https://www.youtube.com/watch?v=lY6icfhap2o](https://www.youtube.com/watch?v=lY6icfhap2o)
3. RESTful API in 100 seconds (using Express): [https://www.youtube.com/watch?v=-MTSQjw5DrM](https://www.youtube.com/watch?v=-MTSQjw5DrM)
