# Naming, Casing, and Commenting Conventions

Naming, casing, and commenting are critical to software engineering because they help us communicate what our code does, preventing miscommunication and bugs. The following are Rocket Academy's naming, casing, and commenting conventions.

## Naming

### General

In general, variable names should be as specific as needed to prevent miscommunication. For example, for a card game with 2 representations of a card, one the card's HTML element and one a JS Object containing the card's name, suit, and rank, we might name the former `cardElement` and the latter `cardMetadata`. Avoid naming either variable `card` to prevent miscommunication.

Avoid using shorthand in variable names that might be common in [SMS language](https://en.wikipedia.org/wiki/SMS\_language), because such terminology may not be universal and can cause confusion and bugs. Strive for precision and concision, prioritising the former where necessary. For example, in Singapore it may be common to use the letter "n" as an abbreviation for "and" and the letter "w" as an abbreviation for "with". Avoid these in variable names because they may not be universal.

### Functions

Function names should start with a verb. This is to distinguish functions from data that might take a similar name. For example, the function `getRandomNum` may return a random number that gets stored in a variable `randomNum`.

### Booleans

Boolean variable names should start with a question word. This is to clearly communicate that this variable stores a boolean. For example, `isGameOver` and `hasPlayerWon` would be preferred boolean variable names than `gameOver` and `playerWon` because the former more explicitly store booleans.

### Event Handlers

By convention, we typically name callback functions that handle events with the prefix `handle` and suffix event type. For example, we would name the callback function for an `onClick` event `handleClick`.

## Casing

### Variables

By default, JavaScript uses [camelCase](https://en.wikipedia.org/wiki/Naming\_convention\_\(programming\)#Examples\_of\_multiple-word\_identifier\_formats) for variable names. Treat acronyms like regular words and use [camelCase for the acronym](https://stackoverflow.com/questions/15526107/acronyms-in-camelcase) for greater readability, e.g. `cardHtmlElement` instead of `cardHTMLElement`.

### Constants

Sometimes we have variables that are constant in our program and used in multiple places, for example number of starting points in a game. To communicate clearly what these constants are and prevent bugs due to string or number misspelling, we often store these variables in "constant" variables, typically near the top of our file or in a separate `constants.js` file.

Constants are typically cased with [SCREAMING\_SNAKE\_CASE](https://en.wikipedia.org/wiki/Naming\_convention\_\(programming\)#Examples\_of\_multiple-word\_identifier\_formats) by convention, e.g. `NUM_STARTING_POINTS`.

### Environment Variables

SCREAMING\_SNAKE\_CASE. `MY_ENV_VAR`.

### File Names

There is no definitive file naming case convention for JS. Rocket Academy prefers [kebab-case](https://en.wikipedia.org/wiki/Naming\_convention\_\(programming\)#Examples\_of\_multiple-word\_identifier\_formats) because it's easier to navigate between words than [snake\_case](https://en.wikipedia.org/wiki/Naming\_convention\_\(programming\)#Examples\_of\_multiple-word\_identifier\_formats), where word processors do not consider underscores to be word separators. Some teams use CamelCase for React component file names; this is subjective so long as we are consistent.

### HTML Tags

Lowercase. E.g. `<div>`

### HTML Attributes

Lowercase kebab-case. E.g. `<div my-attr="lowercase">hello</div>`

### React Components

UpperCamelCase. E.g. `MyReactComponent`

### CSS

IDs and classes in kebab-case. Prefix related classes with common prefix for organisation, e.g. `.card-image` and `.card-text`.

### Git Branches

Git branches are typically named with kebab-case, e.g. `my-new-feature`.

### URLs

URL entities that consist of multiple words are separated by hyphens. For example, `www.mysite.com/my-url-entity`.

### SQL Table and Column Names

SQL table names should be plural and in snake\_case, and column names should be singular and in snake\_case. SQL is case-insensitive, and SQL commands such as CREATE and WHERE are often capitalised, thus lowercase is preferred for column names. Underscores are preferred over hyphens to separate words because hyphens are special characters in some SQL implementations.

## Commenting

### Inline Comments

1. Comments should only exist to clarify code
2. Start comments with a capitalised word like we would an English sentence
3. Inline comments go directly above the line or lines they are commenting on

### Function-Level Comments

For function-level comments in JS, consider using [JSDoc format](https://jsdoc.app/about-getting-started.html#adding-documentation-comments-to-your-code) for clearer identification of functions and what they do. JSDoc is a standard format for JS comments, as well as a tool that auto-generates HTML pages that document code files.

```javascript
/**
 * A function that sums numbers
 * @param  a {number} number to add together
 * @param  b {number} number to add together
 * @return {number}   a and b added together
 */
var add = function (a, b) {
  return a + b;
};
```

The `@` symbol in JSDocs signifies a "tag"- some structure of the code to document. In Rocket Academy JavaScript documentation we will be almost exclusively using only the `param` and `return` tags in JSDoc formatted comments. See the full list of tags [here](https://jsdoc.app/index.html#block-tags).
