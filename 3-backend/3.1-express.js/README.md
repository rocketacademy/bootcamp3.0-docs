# 3.1: Express.js

## What is a Server

According to [Wikipedia](https://en.wikipedia.org/wiki/Server\_\(computing\)), a server is "a piece of computer hardware or software that provides functionality for other programs or devices, called 'clients'". In the context of building apps, this means **software that listens for requests from "clients" (e.g. browsers or mobile apps) over the Internet, and sends back relevant responses (e.g. HTML or app data)**. Servers are typically running 24/7 waiting for requests, such that clients can access their functionality 24/7.

## Example Server

Let's create a server with Node. Node has a built-in global `http` module with a [`createServer`](https://nodejs.org/api/http.html#http\_http\_createserver\_options\_requestlistener) function that creates an [`http.Server`](https://nodejs.org/api/http.html#http\_class\_http\_server) object (instance of a Server class defined in the `http` module). This server object has built-in server functionality like the `listen` method that starts the server listening on a given port. When this server receives a request, it responds with "Yay!".

#### index.js

```javascript
// createServer comes from the http module built-in to Node.
import { createServer } from "http";

const handleIncomingRequest = (request, response) => {
  console.log("Received request!");

  // response.end tells the server to send the completed response and mark
  // this request-response interaction complete.
  // https://nodejs.org/api/http.html#http_response_end_data_encoding_callback
  response.end("Yay!", "utf-8");
};

// createServer creates the server object. It accepts a request listener function.
// The server calls the function every time it receives a request.
// The listen method tells server to start listening for requests on given port.
createServer(handleIncomingRequest).listen(3004);
```

#### Sample Command

```javascript
node index.js
```

This server is available at: [http://localhost:3004](http://localhost:3004). `localhost` is the default domain name for all servers running on our local machines, e.g. in our terminal programs. The port is specified from within the server application code, e.g. `index.js` above. We avoid port 80 to prevent port conflicts between this server and other apps potentially running on `localhost`.

Note that when we run `index.js` the server runs indefinitely. It waits for incoming requests until we terminate the program with `Ctrl+C`, which sends an interrupt signal to the process. When the server is running, look for the running process in Task Manager (Windows) or Activity Monitor (Mac).

## Express

Express.js is an NPM package and web server framework for responding to HTTP requests.

![This is the architecture of the apps we are about to build in Module 3.](../../.gitbook/assets/express.jpg)

## Node HTTP vs. Express

The following are examples of the same server functionality written with the Node HTTP library and Express. What are the differences?

#### Node HTTP

```javascript
import { createServer } from "http";

const handleIncomingRequest = (request, response) => {
  console.log("request came in");
  response.end("yay", "utf-8");
};

const server = createServer(handleIncomingRequest);

server.listen(3004);
```

#### Express

```javascript
import express from "express";

const app = express();

const handleIncomingRequest = (request, response) => {
  console.log("request came in");
  response.send("yay");
};

app.get("/", handleIncomingRequest);

app.listen(3004);
```

The main difference between the 2 code examples is the presence of the `app.get` line in Express. While the Express code is slightly longer in this simple example, Express functionality like `app.get` allows our server code to be much better decomposed and organised than Node HTTP does. We will elaborate on this in the following section.

## Express Routes

Unlike the Node HTTP library where we set the request handler callback for ALL requests when we create the server with `createServer`, Express sets the request listener only for a specific path `/` with `app.get`. This simple but significant change allows Express to provide different request handler callbacks for each type of request it gets, greatly improving the decomposition of our server. It provides a framework for Express to support larger applications with more types of requests.

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

Because Express paths no longer correspond to files, we could give our paths random names like `wow-bananas`. However, best practice is to name application paths more precisely, to help app users better anticipate what we will show them.

Routing methods of the format `app.<METHOD>` are 1 form of Express "middleware", where middleware are functions with access to Express request and response objects, that are executed in the order they are bound to the `app` object, until any middleware sends a response back to the client.

**Middleware is a crucial topic in Express, because all Express logic happens through middleware. We recommend students read more about Express middleware** [**here**](https://expressjs.com/en/guide/using-middleware.html)**.**

## Exercises

### Setup

1. Clone the [base Node repo](https://github.com/rocketacademy/base-node-bootcamp)
2. Install the `express` library
3. Reproduce the Express server above

### Dice Roll

1. Create an Express app that rolls a dice when the user sends a request to the `/dice-roll` route.
2. Send a response back to the client with the dice roll value.
3. Format the response output so it's easy to read.

### Two Dice Rolls

1. Add another "route" to the app `/two-dice-rolls` that rolls two dice and outputs their values to the client.
2. Request `/two-dice-rolls` with Chrome and with `curl`. Verify we get the same responses.

## Further Reading

Past students have found the following videos helpful in introducing Express routing middleware and Express middleware in general.

1. [https://www.youtube.com/watch?v=JlgKybraoy4](https://www.youtube.com/watch?v=JlgKybraoy4)
2. [https://www.youtube.com/watch?v=lY6icfhap2o](https://www.youtube.com/watch?v=lY6icfhap2o)
3. RESTful API in 100 seconds (using Express): [https://www.youtube.com/watch?v=-MTSQjw5DrM](https://www.youtube.com/watch?v=-MTSQjw5DrM)

## Testing Servers Locally

1. When developing and testing applications, we almost always want to run both frontend and backend code locally (i.e. on the computer in front of us) first to speed up development by avoiding network latency.
2. Once we've started our server locally, we can send requests to it through its local IP address or domain name, `127.0.0.1` or `localhost` respectively.
3. Once our server code works locally, we can deploy it to the cloud so others can access the server.

## Exercise

1. Clone [the base Node repo](https://github.com/rocketacademy/base-node-bootcamp).
2. Set up a server that listens for requests.
3. Make a GET request to your server.
4. Make a GET request to google.com.
5. Make a GET request to [http://info.cern.ch/](http://info.cern.ch/)
6. Use Chrome's Network tab to view your request details. Look for HTTP method and status code header details.
7. Set a response header of `rocketacademy` with value `true` in your server using the `response.writeHead` method (example above). Confirm you receive it in Chrome's Network tab after sending a request.
8. Set other status codes in the response header such as [206](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/206), [418](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/418) and [507](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/507). What do they do?
9. Set the special status code 301 like the following code snippet. What does it do? What do we see in the Network tab after receiving this response?

```javascript
response.writeHead(301, { Location: "http://info.cern.ch/" });
```
