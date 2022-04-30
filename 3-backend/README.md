# 3 Backend

## Introduction

In Rocket's Bootcamp we will learn to build applications that interact with the Internet. To start, we will learn how these applications run and important fundamentals about the Internet.

In Module 3 we will build apps using the NPM library and web server framework Express, and store data in a SQL database on a separate DB server.

![Our Express app will have this architecture.](../.gitbook/assets/express-4.jpg)

## Architecture

For clarity, let's define the back-end and front-end of our app architecture.

### Front End

1. Frontend typically refers to a browser, mobile, or desktop application where users can perform actions like clicking and typing.
2. Some user actions on the frontend will trigger HTTP requests to the backend to store or retrieve data.
3. The frontend sends requests to the backend and handles responses. In Module 3 our responses will mostly consist of HTML, and our frontends will render that HTML.

### Back End

1. Backend typically refers to the server that manages the database.
2. The server listens for incoming requests from the frontend. When it receives a request, it runs logic to determine what response to send back.
3. Until now, our servers only responded with files specified in the URL path. Now we'll add additional logic to our backend to support our apps' needs.

## What is a Backend?

The word backend defines the overall architecture of a system. It can mean different things depending on the context, but for the context of this course it will always refer to the web server application. In Bootcamp this also means a JavaScript program. The word backend and frontend also distinguish the _client_ and the _server_: the part of the application doing the requesting (the client) and the part that listens for incoming requests (the server).

In this module "backend" also implies discussing the properties of an application that runs in a backend environment- an environment that has different properties to a frontend (browser) environment. In this environment we can write JavaScript that interacts more directly with important hardware representations of the computer, such as the hard drive and the networking card. Being in a backend coding context means dealing more directly with the machine that the code is running on. This is in contrast to running JavaScript in a browser environment, which is mostly agnostic to which operating system or browser brand it is running on.

This context means doing away with all of the GUI representations of the running code, like buttons, images and emojis. The transition to a backend environment means that all the code is run from the terminal- the environment where we can programmatically interface directly with the computer.

In addition, this backend context allows us to introduce and talk about the basics of how the internet works- a crucial piece of how all our applications behave.

![Diagram of how the frontend communicates with the backend](../.gitbook/assets/server.drawio.svg)

## Where We Are Going

This module is a transitional section that puts in place some fundamental concepts as we work our way towards the cornerstone application we'll be building upon: the backend web application. We'll begin working on that code starting in module 3.

### Bigger Picture

Frontend and backend are relative terms. As our apps get more complex they may involve multiple servers, for example 1 to serve frontend files and another to serve backend logic. Each of these servers can be considered to have "frontend" and "backend" components.

In general, frontend refers to the web, mobile, or desktop client and/or the server that serves the UI to that client, and backend refers to the server(s) managing the database.

## Learning Objectives

1. Understand basic internet infrastructure (domain name, IP address, ports) and how we send data across the internet
2. Deploy apps to the internet with Heroku
3. Build backend apps that can listen for and respond to requests from the internet

## What We Will Learn

At the end of this module we will be able to build apps where users on the Internet can input data and we can manipulate, store, and retrieve that data persistently.

1. Send HTTP requests from frontend to backend
2. Respond from backend with appropriate data and HTML
3. Store data in backend first using JSON, then SQL

We will spend time practising a concept called "database design" where we will practise designing the structure of our databases to be most relevant for our apps. Similar to Tic Tac Toe where the game relied on a specific structure of data (e.g. a 2D array), it will be important for our upcoming apps to have appropriate DB structures.

This module is an optimization and evolution of the [Noodle Recipe Website](../1-frontend-basics/1.poce-post-class-exercises/1.poce.1-noodles.md): how do we display on the internet an interlinked set of recipes, such that:

1. We store and represent these recipes not as HTML code / files, but as abstracted linked data.
2. We make the content of these recipes dynamic and changeable to the users on the public internet who access the website, not just to those who can edit the files.
3. We keep useful properties of HTML website code, such as one URL for each recipe.

Checkout a live version of the backend-powered noodle site here: [https://codesandbox.io/s/noodle-ejs-x5m8u](https://codesandbox.io/s/noodle-ejs-x5m8u)

## Module 2 Setup

## Install Packages

### Ngrok

Install [ngrok](https://ngrok.com) using the commands below. We will use `ngrok` for one of in-class exercises to expose our local servers to the Internet.

#### Mac

```javascript
brew install --cask ngrok
```

#### Ubuntu

```
sudo npm install -g ngrok
```

## WSL

For Windows, Module 2 marks a point that we will change the way files are stored and edited. From now on all files will be created and saved inside the Ubuntu / WSL part of the computer.

#### Working between WSL and Windows files

Apart from the terminal, all the files in your WSL Ubuntu instance can also be accessed from a Windows file explorer window. Type the following path into the address bar of any file explorer window:

```
\\wsl$
```

#### Opening Windows File Explorer from VSCode Terminal

Directly access files from a Windows file explorer window from the terminal by running explorer from within Ubuntu:

```
/mnt/c/windows/explorer.exe <SOME_UNIX_PATH_TO_FILE>
```

Example: Open the current terminal directory:

```
/mnt/c/windows/explorer.exe .
```

Open a new VSCode window for the current directory from the terminal:

```
code .
```

#### Further Reference

[https://devblogs.microsoft.com/commandline/do-not-change-linux-files-using-windows-apps-and-tools/](https://devblogs.microsoft.com/commandline/do-not-change-linux-files-using-windows-apps-and-tools/)\
\
[https://www.howtogeek.com/426749/how-to-access-your-linux-wsl-files-in-windows-10/](https://www.howtogeek.com/426749/how-to-access-your-linux-wsl-files-in-windows-10/)
