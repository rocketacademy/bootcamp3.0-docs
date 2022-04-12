# 3.2: EJS

## Introduction

![EJS is a template engine that operates on the backend to simplify HTML page generation.](../../.gitbook/assets/ejs.jpg)

1. EJS (Embedded JavaScript) is an NPM library that we can integrate with Express to inject JS variables into HTML templates.
2. We can re-use the EJS HTML templates (aka EJS templates) to inject different data into the same HTML page structures.
3. EJS integrates with Express' `response.render` function to produce an HTML string with the given template and data to return to the client.
4. We will split our app into separate files by putting EJS templates in their own folder.

## Views

1. The term "**view**" comes from the [Model-View-Controller or MVC framework](https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller) that defines views as the looks of an application, i.e. what the user is able to "view".
2. In our Express apps, we will create a `views` folder and store our EJS templates in it.
3. When we run `response.render` to render an HTML response to the client, `render` will tell EJS which EJS template to use and pass relevant data to inject into that template.

![EJS combines EJS HTML templates and dynamic data to generate HTML pages for responses](../../.gitbook/assets/ejs2.jpg)

{% hint style="warning" %}
**EJS and DOM Manipulation are Independent Concepts**

1. Both EJS and DOM manipulation help generate HTML content dynamically, but they are independent concepts. EJS operates in the backend and DOM manipulation operates in the frontend.
2. DOM manipulation can be used to generate HTML content dynamically once a page has loaded. EJS generates static HTML pages dynamically from the backend, such that different URL paths can yield different HTML pages, each of which can be generated from the same EJS template.
3. RA's Noodle App is an example of EJS and DOM working together in the same application. EJS templates dynamically generate recipe pages for URL paths `recipe/0` and `recipe/1`. Once loaded in the client, those recipe pages can then be manipulated by DOM JS code, where clicking on elements on the pages further updates the UI.
{% endhint %}

## Using EJS

### Configuration

1.  Install the EJS library.

    ```bash
    npm install ejs
    ```
2. Install the [EJS syntax highlighter for VSCode](https://marketplace.visualstudio.com/items?itemName=DigitalBrainstem.javascript-ejs-support). This enables JS syntax highlighting and formatting within EJS files.
3.  Configure Prettier to format EJS as HTML by adding the following setting to the [VSCode JSON Settings](https://basics.rocketacademy.co/course-logistics/required-hardware-and-software#vscode-formatters).

    ```
    "emmet.includeLanguages": {
      "ejs": "html"
    },
    ```

### File Structure

Our server apps will have the following file structure.

```
└── my-app
    ├── index.js
    └── public
       └── styles.css
    └── views
       └── fruit.ejs
```

#### index.js

1.  In `index.js`, set EJS as the [Express template engine](https://expressjs.com/en/guide/using-template-engines.html) to generate HTML responses. Insert the following line below where we initialise `app` and above any routes.

    ```javascript
    app.set('view engine', 'ejs');
    ```
2. Within a request handler callback, when ready to respond with HTML, call `response.render` with the following 2 params.
   1. A string containing the path/name of the EJS template (without file extension) in the `views` folder.
   2. An object containing data to inject in the EJS template.
3.  Our code might look like the following.

    ```javascript
    import express from 'express';

    const app = express();

    // Set view engine
    app.set('view engine', 'ejs');

    app.get('/fruit', (request, response) => {
      // Obtain data to inject into EJS template
      const data = {
        fruit: {
          name: 'banana',
        },
      };
      // Return HTML to client, merging "index" template with supplied data.
      response.render('fruit', data);
    });

    app.listen(3004);
    ```

#### fruit.ejs

`fruit.ejs` is a sample EJS template for this example. EJS templates look like HTML files, except with "templating syntax" to inject JS variables into the HTML. In this example, we inject the properties of the `data` object in `index.js` to `fruit.ejs`. Templating concepts and syntax are similar across most web application frameworks, including Ruby on Rails, Python Django, and Java Spring.

```markup
<html>
  <head>
    <!-- AFTER HTML loads in browser, browser will request for CSS. -->
    <link rel="stylesheet" href="styles.css">
  </head>
  <body>
    <h2><%= fruit.name %></h2>
  </body>
</html>
```

{% hint style="warning" %}
**Browser Retrieves Static Files AFTER HTML Loads**

1. When our HTML references static files like CSS, image, or JS files, EJS does NOT read or load those files into the initial response.
2. EJS compiles HTML with the EJS template and provided data, and Express sends that HTML back to the client.
3. After the client reads the response HTML, it requests for the additional static files that the HTML may reference.
{% endhint %}

### Static/Public Folder

Our CSS may not load yet because we haven't told Express how to serve static files. To enable our server to respond with the `styles.css` file, we need to enable Express' built-in file server and configure it to serve files from the folder where our CSS is. The following expression enables Express to serve files from a local folder called `public`. Read more about static files[ here](https://expressjs.com/en/starter/static-files.html) and `express.static` [here.](https://expressjs.com/en/4x/api.html#express.static)

```javascript
app.use(express.static('public'));
```

1. Create a folder in the repo called `public`. Move all CSS files to this folder.
2. Add the above expression (`app.use(express.static(...))`) to our `index.js` file above our routes to enable the file server.
3.  Verify the file server works by making an HTTP request for a CSS file inside the `public` folder. The URL path can be a relative path relative to the `public` folder.

    ```
    http://localhost:3004/styles.css
    ```



### **EJS Naming Convention**

By convention, we name EJS templates after the routes that render them. For example, a route like the following should render an EJS file called `fruit.ejs`. There are few exceptions to this convention.

```javascript
app.get('/fruit/apple', /* ... */)
```

### (Optional) Add .prettierignore File for Prettier to Ignore EJS

VSCode interprets EJS files as HTML, and sometimes we do not want Prettier to format EJS as HTML. We will add a `.prettierignore` file at the root of the folder open in VSCode to ignore files with a `.ejs` file extension.

Please add a `.prettierignore` file at the root of the folder open in VSCode with the following contents. For example, if my `rocket` folder is open in VSCode with many subfolders such as `ice`, `prce`, `poce`, `projects`, I will add `.prettierignore` to the `rocket` folder and not any of its subfolders. More info on Prettier Ignore [here](https://prettier.io/docs/en/ignore.html).

Occasionally we may wish to comment out the `*.ejs` line in `.prettierignore` for Prettier to format the HTML in our EJS templates.

```
# Ignore all EJS files
*.ejs
```

## Exercise

1. Create a server with the above code and return HTML with EJS templating.
2. Add an `h1` element to `fruit.ejs` and fill it with another attribute in the `data` object.
3. Create a new route with a path param like `/fruits/:name`. Inject the path param value in the response HTML by adding the param to the `data` object, then referencing it in the EJS template.
