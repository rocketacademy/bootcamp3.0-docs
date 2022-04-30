# CSS.1: Basic CSS

### Intro To CSS

In the beginning was HTML and only HTML. But programmers wanted to add styling to their web pages to help distinguish themselves from others on the web. Initially, the answer was no. But in October 1994, Håkon Wium Lie introduced Cascading Style Sheets to the world. Today it is better known as CSS.

Built on top of HTML to add more visual control and complexity, CSS specifies styles on an HTML element or set of elements. The CSS code specifies visual properties unrelated to the written content on an HTML page. In practice there are 2 uses for CSS: element styling and layout.

#### Element Styling&#x20;

CSS helps us change visual properties of HTML elements, such as fonts, background images, or rounded corners on buttons. Together with JS DOM manipulation, we can use CSS to implement visual logic within an application, such as hiding or showing cards and flipping elements 90 degrees.&#x20;

#### Layout&#x20;

CSS can help us divide our UI into visual sections. This is one of the most tricky aspects of CSS, because CSS was not originally intended for layout design. CSS content in Rocket's Bootcamp will focus on implementing UI layouts.

### How CSS Works&#x20;

CSS is a declarative language. It doesn't tell the browser what to do but rather describes the rules that the browser then uses to render the page. CSS became popular because it was predictable and forgiving in its syntax. It was also easy to learn.\
The concept of cascading styles is unique to CSS. To cascade means that styles can inherit and overwrite styles through its hierarchy called specificity. More on that in section 2. This concept also allowed for many style sheets to be applied to one page. That is what made CSS so popular.

As a declarative language, CSS uses selectors and declarations to apply styling rules to HTML pages. The syntax for CSS starts with a selector which tells the browser the rules for styling the selected elements. Then a code block is created using open and closing curly braces. Inside the code block declarations or rules are created. A declaration is made up of a property name followed by a colon and then the value of the property followed by a semi-colon. You can have as many declaration statements as needed. It is the standard to put each declaration on its own line in code. The semi-colon tells the browser that the end of the line is reached so be sure to add it at the end of every declaration.

#### Sample Syntax

```css
selector {
  property: value;
}
```

There are three places where CSS styling can occur:

1. in-line
2. internal
3. external.

#### In-Line Styling

**In-line styling** is written inside the HTML opening tag as an attribute-value pair. Like this:

```html
<p style="“color:" red;”>This text would be red</p>
```

If more than one style declaration is applied:

```html
<p style="“color:" red; font-weight: bold;”>This text is red and bold</p>
```

#### Internal Styling

**Internal styling** is placed inside the head tag of the page and is wrapped inside the style tag. In this example, the selector of p is chosen to style all the paragraph tags on the page.

```html
<html>
  <head>
    <title>Page Title</title>
    <style>
      p {
        color: white;
      }
    </style>
  </head>
  <body>
    <p>This text is white</p>
  </body>
</html>
```

#### External Styling

**External styling** links a css stylesheet to the HTML page. This is done by adding a link tag in the head of the HTML file.

```html
<link src=“style.css” rel=“type/stylesheets” />
```

The stylesheet would contain the same css coding that would be put in the head directly.

**External Styling is the standard and should always be used.** The other two ways should seldom if ever be used.

## CSS Example&#x20;

In these examples, we will be using internal styling as it makes it easier for teaching purposes. However, in the coding world, all css should be externally linked to the html page.

Remember that every browser has a CSS engine and that engine has default declarations for HTML elements. So to change the look of an h2 tag requires that a declaration block be made to apply new rules to the h2 tags in the file. Let's start with the following file.

```html
<html>
  <head>
    <title>Page Title</title>
  </head>
  <body>
    <h2>Styling H2 tags</h2>
  </body>
</html>
```

Copy and paste the above code snipet and save the file as index.html. Then open the file in a browser and notice how the text looks.

Next insert the following code just after the title tag and just above the closing head tag.

```html
<style>
  h2 {
    background-color: blue;
    color: white;
  }
</style>
```

This code targets all h2 tags in the file and makes the background-color blue and the color of the text white.

Refresh your browser and you should see that the h2 has a blue background-color and white text.

### Selector Combinations

So far we have been looking at a single selector and applying declarations for that element. CSS offers many ways to target more than one element or get very specific about which element to style using selector combinations.

Below is a table that shows how to use different selector combinations and the elements they target.

|  Selector Type   |     Example     | Explanation                                                     |
| :--------------: | :-------------: | --------------------------------------------------------------- |
|    universal     |       \*        | Targets all elements                                            |
|      single      |        p        | Targets all p tags                                              |
|     multiple     |   p , h1, h3    | Targets p, h1 and h3 tags                                       |
|    descendant    |      div p      | Targets p tags that are descendants of a div                    |
|      child       |     div > p     | Targets p tags that are immediate children of a div             |
| adjacent sibling |     h2 + p      | Targets p tag that is immediately adjacent to an h2 tag         |
|    attribute     | \[attr="value"] | Targets elements that contain the specified attribute and value |
|      class       |   .class_name   | Targets all elements with the class of class_name               |
|        id        |    #id_name     | Targets the one element with the id of id_name                  |

## Exercise Tips / Cheatsheet

### Don't Write Placeholder Text

Install the [Lorem Ipsum plugin for VS Code](https://marketplace.visualstudio.com/items?itemName=Tyriar.lorem-ipsum) to quickly get placeholder text.

### Get Placeholder Images for CSS

Use [Lorem Picsum](https://picsum.photos) to get placeholder images.

### Use Readily-Available Icons

[Fontawesome](https://fontawesome.com) makes it easy to put icons on a page using HTML elements and CSS. Read full Fontawesome documentation [here](https://fontawesome.com/how-to-use/on-the-web/referencing-icons/basic-use).

As the CSS styles link below is based on `v4.7` of Fontawesome, we'll follow the link [here](https://fontawesome.com/v4.7/icons/) to get the icons that you want

#### CSS styles link

```css
<link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/font-awesome/4.7.0/css/font-awesome.min.css" crossorigin="anonymous">
```

#### Usage:

```css
<i class="fa fa-camera"></i>
```

{% hint style="info" %}
Fontawesome docs may give examples where the icon base classes must change- `fas` might need to be changed to `fa` if the icon doesn't appear.
{% endhint %}

### Consider Using Google Fonts

Google's font collection is a relatively standard font collection of readable fonts. See their catalogue of fonts [here](https://fonts.google.com) and an exercise on how to use Google fonts [here](https://www.freecodecamp.org/learn/responsive-web-design/basic-css/import-a-google-font).

### Use Viewport Tag for Mobile Views (Important!)

{% hint style="warning" %}
Many students miss this, causing CSS layout issues in mobile views. Please add this to websites we want to work on mobile.
{% endhint %}

For mobile first layouts we need to add a scaling `meta` tag in our `head` tag. This is to develop for mobile on desktop without squinting. Chrome DevTools assumes we have this scaling tag when debugging mobile layouts. Read more about the `viewport` tag [here.](https://developer.mozilla.org/en-US/docs/Web/HTML/Viewport_meta_tag)

```markup
<meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">
```

## Exercises

We will complete the 44 exercises in [Free Code Camp's Basic CSS module](https://www.freecodecamp.org/learn/responsive-web-design/basic-css/).

### Part 1 (Exercises 1-22)

Complete Free Code Camp's Basic CSS Exercises 1-22. Start from [Change the Color of Text](https://www.freecodecamp.org/learn/responsive-web-design/basic-css/change-the-color-of-text) and end at [Use Clockwise Notation to Specify the Margin of an Element](https://www.freecodecamp.org/learn/responsive-web-design/basic-css/use-clockwise-notation-to-specify-the-margin-of-an-element).

### Part 2 (Exercises 23-36, Skip Last 8 Exercises)

Complete Free Code Camp's Basic CSS Exercises 23-36. Start from [Use Attribute Selectors to Style Elements](https://www.freecodecamp.org/learn/responsive-web-design/basic-css/use-attribute-selectors-to-style-elements) and end at [Use RGB to Mix Colors](https://www.freecodecamp.org/learn/responsive-web-design/basic-css/use-rgb-to-mix-colors). Skip last 8 exercises (i.e. 37-44) because they are not particularly relevant.
