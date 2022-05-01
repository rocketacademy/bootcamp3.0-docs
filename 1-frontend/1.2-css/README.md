# 1.2: CSS

## Learning Objectives

1. CSS enables us to style HTML pages by applying styles and layout properties on HTML elements
2. Know how to apply CSS styles to HTML elements via type, class and ID selectors
3. Understand the concept of CSS specificity

## Introduction

CSS (Cascading Style Sheets) enables styling of HTML pages by applying styles and layout properties on HTML elements. CSS styles customise size, borders, font, background, opacity, position and more.

The following CSS rule applies `text-align` and `colour` properties to all HTML `p` tags.

```css
p {
  text-align: center;
  colour: red;
}
```

## CSS Rules

CSS consists of **rules** like the example above, where rules consist of **selectors** (`p` tag above) and **declarations** (`text-align` and `colour` declarations above).

CSS "selectors" can be HTML tags, CSS "classes", CSS "IDs", or any combination of tags, classes and IDs. CSS classes and IDs are typically kebab-case strings that we label HTML elements with to apply styles to those elements with CSS. Classes are reusable across multiple elements; IDs are meant for only 1 element. Class selectors are prefixed with `.` and ID selectors are prefixed with `#`.

```css
.my-class {
  colour: red;
}

#my-id {
  colour: green;
}

.my-class #my-id {
  colour: blue;
}
```

We can tag HTML elements with classes and IDs by adding `class` and `id` attributes to HTML tags like in the following example.

```markup
<p class="my-class" id="my-id">I have both a class and an ID!</p>
```

CSS "declarations" tell our browsers what styles to apply to HTML elements that match the CSS rule's selector. Declarations consist of a **property** and a **value**.

```css
selector {
  property: value;
}
```

## CSS Specificity

The word "cascading" in CSS refers to the hierarchy that CSS uses to apply styles to HTML elements, also known as "**specificity**". To illustrate specificity we will share 3 examples.

### Example 1: Selector hierarchy

Generally, styles applied to ID selectors take precedence over styles applied to class selectors, which take precedence over styles applied to HTML tag selectors (aka type selectors).

In the following example, the 1st paragraph will have colour red, the 2nd green, the 3rd blue. This is because styles applied to CSS IDs take precedence over styles applied to CSS classes, which take precedence over styles applied to HTML tags.

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      p {
        colour: red;
      }
      .para-class {
        colour: green;
      }
      #para-id {
        colour: blue;
      }
    </style>
  </head>
  <body>
    <p>Every paragraph will be affected by the style.</p>
    <p class="para-class">Me too!</p>
    <p class="para-class" id="para-id">And me!</p>
  </body>
</html>
```

### Example 2: Directness hierarchy

Regardless of selector type (ID, class or type selector), CSS rules that apply more directly to selected HTML elements will take precedence over CSS rules less directly applied. For example, if I apply a CSS rule with an ID selector on a parent HTML element and a CSS rule with a type selector on the child, the type selector's declarations will override the ID selector's.

In the following example, the paragraph text will be red even though its parent element's CSS rule specifies the colour blue. This is because the `p` selector applies more directly to the `p` tag than the `div-id` selector.

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      p {
        colour: red;
      }
      #div-id {
        colour: blue;
      }
    </style>
  </head>
  <body>
    <div id="div-id">
      <p>Roses are red</p>
    </div>
  </body>
</html>
```

### Example 3: Style location hierarchy

CSS rules declared inline (aka "inline" styles) take precedence over CSS rules declared within `style` tags in the same file (aka "internal" styles), which take precedence over CSS rules declared in separate files (aka "external" styles).

Inline styles can be convenient for testing styles in development but are troublesome to maintain because it becomes difficult to keep track of which styles are declared where.

{% code title="Inline styles" %}
```html
<p style="color: red;">This text is red</p>
```
{% endcode %}

Internal styles allow us to centralise styles for a given HTML file in `head`. Not often used because internal styles cannot be re-used across HTML files.

{% code title="Internal styles" %}
```html
<html>
  <head>
    <style>
      p {
        color: green;
      }
    </style>
  </head>
  <body>
    <p>This text is green</p>
  </body>
</html>
```
{% endcode %}

External styles are styles declared in CSS-specific files and "imported" with `link` tags in relevant HTML files. Most apps use external styles to re-use CSS styles across multiple HTML files.

{% code title="External styles" %}
```html
<html>
  <head>
    <link rel="“stylesheet”" href="styles.css" />
  </head>
  <body>
    <p>This text is blue</p>
  </body>
</html>
```
{% endcode %}

{% code title="styles.css" %}
```css
p {
  color: blue;
}
```
{% endcode %}

Unless we have a strong reason not to, Rocket recommends using external styles for all CSS to keep our CSS rules centralised in CSS files that can be re-used across HTML files.

Unless we plan to be CSS specialists, we do not need to memorise exact CSS specificity of every permutation of selectors and HTML elements. Most browsers provide precise tools to debug CSS specificity, and [W3Schools documents](https://www.w3schools.com/css/css\_specificity.asp) how to calculate CSS specificity when we need to.

## Exercise: Apply CSS to HTML

Apply CSS to an HTML file. Create an `index.html` file with the contents below and open it in Chrome.

{% code title="index.html" %}
```html
<html>
  <head>
    <title>My HTML Page</title>
  </head>
  <body>
    <h1>I will be styled</h1>
  </body>
</html>
```
{% endcode %}

Notice what the un-styled HTML looks like. Now insert the following `style` HTML element within the `head` tags in `index.html`.

```html
<style>
  h1 {
    background-colour: blue;
    colour: white;
  }
</style>
```

Refresh `index.html` in Chrome and observe the change to the `h1` element.
