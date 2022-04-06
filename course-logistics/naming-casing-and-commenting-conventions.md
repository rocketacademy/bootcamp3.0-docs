# Naming, Casing, and Commenting Conventions

Naming, casing, and commenting are critical to software engineering because they help us communicate what our code does, preventing miscommunication and bugs. The following are a set of naming, casing, and commenting conventions to follow during Coding Bootcamp \(primarily for JavaScript\), and hopefully beyond.

## Naming

### General

In general, variable names should be as specific as possible to prevent miscommunication. For example, for a game with 2 JS Objects, 1 an HTML element representing a playing card and 1 a JS Object containing playing card's name, suit, and rank, we might name the former `cardElement` and the latter `cardMetadata`. Avoid naming either variable `card` to prevent miscommunication.

Avoid using shorthand in variable names that might be common in [SMS language](https://en.wikipedia.org/wiki/SMS_language), because such naming may not be universal and can cause confusion and bugs. Strive for precision and concision, prioritising the former whenever necessary.

For example, in Singapore it may be common to use the letter "n" as an abbreviation for "and" and the letter "w" as an abbreviation for "with". Avoid these in variable names because they may not be universal.

### Functions

Function names should start with a verb. This is to distinguish functions from data that might take a similar name. For example, the function `getRandomNum` may return a random number that gets stored in a variable `randomNum`.

### Booleans

Boolean variable names should start with a question word. This is to clearly communicate that this variable stores a boolean. For example, `isGameOver` and `hasPlayerWon` would be preferred boolean variable names than `gameOver` and `playerWon` because the former more explicitly store booleans.

### Event Handlers

Callback functions that handle events are typically prefixed with `handle` and suffixed with the event type. For example, for the on-click callback function for a deal cards button, we might call it `handleDealButtonClick`.

### Express.js

#### Views and Public Asset Folders

You must have directories named `views` and `public` for view templates and public asset files respectively. You can change this in the configs, but we recommend keeping the defaults.

#### EJS File Names

EJS files are named the same as their respective routes in kebab-case. For example, the `/recipes` route should correspond to an EJS file called `recipes.ejs`.

#### Routes

The following are common naming conventions for routes, helping to communicate the functionality of each path-method combination.

| URL Path | Method | Purpose |
| :--- | :--- | :--- |
| /&lt;RESOURCE&gt; | GET | Render a form that will create a new resource. |
| /&lt;RESOURCE&gt; | POST | Accept a POST request to create a new resource. |
| /&lt;RESOURCE&gt;/:id | GET | Render a single resource. |
| / | GET | Render a list. |
| /&lt;RESOURCE&gt;/:id/edit | GET | Render a form to edit. |
| /&lt;RESOURCE&gt;/:id/edit | PUT | Accept a request to edit. |
| /&lt;RESOURCE&gt;/:id/delete | DELETE | Accept a request to delete. |

## Casing

### Variables

By default, JavaScript uses [camelCase](https://en.wikipedia.org/wiki/Naming_convention_%28programming%29#Examples_of_multiple-word_identifier_formats) for variable names. Treat acronyms like regular words and use [camelCase for the acronym](https://stackoverflow.com/questions/15526107/acronyms-in-camelcase#:~:text=When%20using%20acronyms%2C%20use%20Pascal,in%20identifiers%20or%20parameter%20names) for greater readability, e.g. `cardHtmlElement` instead of `cardHTMLElement`.

### Constants

Sometimes we have variables that are constant in our program and used in multiple places, for example game modes. To communicate clearly what these constants are and prevent bugs due to string or number misspelling, we often store these variables in "constant" variables, often near the top of our file or in a separate `constants.js` file.

Constants are typically cased with [SCREAMING\_SNAKE\_CASE](https://en.wikipedia.org/wiki/Naming_convention_%28programming%29#Examples_of_multiple-word_identifier_formats) by convention, e.g. `GAME_MODE_DEAL_CARDS`.

### Environment Variables

SCREAM\_CASE. `MY_ENV_VAR`.

### File Names

JavaScript file names typically use [lowerCamelCase](https://en.wikipedia.org/wiki/Naming_convention_%28programming%29#Examples_of_multiple-word_identifier_formats). Other file and folder names typically use [kebab-case](https://en.wikipedia.org/wiki/Naming_convention_%28programming%29#Examples_of_multiple-word_identifier_formats) or [snake\_case](https://en.wikipedia.org/wiki/Naming_convention_%28programming%29#Examples_of_multiple-word_identifier_formats) for easy typing and autocomplete in the terminal.

### HTML Tags

Lowercase. E.g. `<div>`

### HTML Attributes

Lowercase kebab-case. E.g. `<div my-attr="banana">hello</div>`

### CSS

IDs and classes in kebab-case. Prefix classes with identifiers for common grouping, if any, e.g. "card" for card-related CSS classes. `.card-image` and `.card-text`.

### Git Branches

Git branches are typically named with kebab-case, e.g. `my-new-feature`.

### URLs

URL entities that consist of multiple words are separated by hyphens. For example, `www.mysite.com/my-url-entity`.

### SQL Table and Column Names

SQL column names should be in snake\_case. SQL is case-insensitive, and SQL commands such as CREATE and WHERE are often capitalised, thus lowercase is preferred for column names. Underscores are preferred over hyphens to separate words because hyphens are special characters in some SQL implementations.

## Commenting

For function-level comments, consider using [JSDoc format](https://jsdoc.app/about-getting-started.html#adding-documentation-comments-to-your-code) for clearer identification of functions and what they do.

