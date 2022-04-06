# Tools, Syntax, and Glossary

## General Coding Tools

### Opening HTML in Browser from VSCode

1. [https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer)
2. [https://marketplace.visualstudio.com/items?itemName=techer.open-in-browser](https://marketplace.visualstudio.com/items?itemName=techer.open-in-browser)

### Git, GitHub

Past students have found this [video playlist](https://www.youtube.com/playlist?list=PLRqwX-V7Uu6ZF9C0YMKuns9sLDzK6zoiV) helpful in better understanding Git and GitHub.

### Linux Commands

Past students have found [this video](https://www.youtube.com/watch?v=RzAkjX_9B7E) helpful in understanding Linux commands.

## CSS

### CSS Properties

1. Configure overflow content to the user: [https://www.w3schools.com/cssref/css3\_pr\_text-overflow.asp](https://www.w3schools.com/cssref/css3_pr_text-overflow.asp)

### Chrome Extensions

1. Past students have found the [Pesticide Chrome extension](https://chrome.google.com/webstore/detail/pesticide-for-chrome-with/neonnmencpneifkhlmhmfhfiklgjmloi) helpful in visualising CSS elements on a page.

### Tips

1. When applying media query styles in custom CSS, use Bootstrap widths as a standard.
   1. [https://getbootstrap.com/docs/4.1/layout/overview/\#responsive-breakpoints](https://getbootstrap.com/docs/4.1/layout/overview/#responsive-breakpoints)

## JavaScript

JavaScript \(like most languages\) has built-in functions that can help simplify our logic. Here are common functions that past students have found helpful.

### String Functions

#### Substring

Get a specified subset of a given string.

[https://www.w3schools.com/jsref/jsref\_substring.asp](https://www.w3schools.com/jsref/jsref_substring.asp)

#### Includes

Verify if a given string includes a given substring.

[https://www.w3schools.com/jsref/jsref\_includes.asp](https://www.w3schools.com/jsref/jsref_includes.asp)

### Objects

#### Object Dereferencing: myObj.foo vs myObj\[foo\] vs myObj\['foo'\]

`myObj.foo` and `myObj['foo']` are equivalent. ESLint prefers `.foo` syntax.

`myObj[foo]` returns the value that corresponds to the key with the value stored inside the variable `foo`. For example, if `foo === 'bar'`, then `myObj[foo]` is equal to `myObj.bar`. 

We cannot use `.foo` notation for numbers. For example, for an object key with value `'1'`, we cannot do `myObj.1`. We must do `myObj[1]` or `myObj['1']`, where JS auto-converts `1` in the former example to `'1'` since object keys can only be strings.

## JSDoc

JSDoc is a standardized format for JavaScript comments, as well as a tool that auto-generated HTML pages that document code files.

```javascript
/**
 * A function that sums numbers
 * @param  a {number} number to add together
 * @param  b {number} number to add together
 * @return {number}   a and b added together
 */
var add = function(a,b) {
    return a + b;
};
```

The `@` symbol in JSDocs signifies a "tag"- some structure of the code to document. In Rocket Academy JavaScript documentation we will be almost exclusively using only the `param` and `return` tags in JSDoc formatted comments. 

See a list of tags here: [https://jsdoc.app/index.html\#block-tags](https://jsdoc.app/index.html#block-tags)

See more on JSDoc here: [https://jsdoc.app/about-getting-started.html](https://jsdoc.app/about-getting-started.html)

## Glossary

The following are definitions of common terms we will use in Bootcamp.

### Frontend

Also known as "front-end" or "front end", front end refers to everything to do with the user interface of an application, and the logic that happens on the user's machine.

### Backend

Also known as "back-end" or "back end", back end refers to everything that happens behind the user interface, typically logic which gets executed "server-side", i.e. not on the user's device.

### Integrated Development Environment \(IDE\)

IDEs are programs in which software engineers write code. It's easier to code in IDEs than regular text editors because IDEs typically provide tools such as syntax highlighting, syntax formatting, and auto-completion that make coding easier.

### Command Line

The command line is a text-based interface that we can use to operate our computers through programs known as "terminals".

### Terminal

A terminal is an interface that we can use to operate our computers through a text-based "command line".

### Boilerplate

Code that is repeated in multiple places will little alteration. [https://en.wikipedia.org/wiki/Boilerplate\_code](https://en.wikipedia.org/wiki/Boilerplate_code)

### Application Programming Interface \(API\)

An API is an interface through which programmers can have computers perform pre-programmed logic. For example, data.gov.sg exposes an [API](https://data.gov.sg/dataset/realtime-weather-readings) for developers to obtain real-time weather information in their applications through the API.

### Schema

Schema can refer to a few things, but in general it refers to a "blueprint" or "plan" for a database structure.

1. Database Schema
2. Relation or Table Schema
3. PostgreSQL Schema

See this [Stack Overflow answer](https://stackoverflow.com/a/298765) for definitions of \#1 and \#2, and [Postgres documentation](https://www.postgresql.org/docs/13/ddl-schemas.html) for \#3. We will rarely be using definition \#3 in Coding Bootcamp.

