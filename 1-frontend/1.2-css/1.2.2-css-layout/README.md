# 1.2.2: CSS Layout

## Learning Objectives

1. CSS layout is about organising HTML elements into nested boxes and determining their positions

## Introduction

![Organise HTML elements into conceptual boxes before planning how to use CSS for layout. Source: W3Schools](<../../../.gitbook/assets/1.3 - CSS Layout - 1 - Layout Example.gif>)

When determining how to layout elements with CSS, first organise elements into nested boxes, then determine which CSS styles need to apply to which boxes. By default browsers will render all HTML elements in a single vertical column.

## CSS Box Model

![Margin is spacing outside the content's border. Padding is spacing inside the content's border. Source: W3Schools](<../../../.gitbook/assets/1.3 - CSS Layout - 3 - Box Model.png>)

​

The CSS box model controls how much space an element takes on screen with CSS properties such as content `width`, content `height`, `margin` (area outside border), `border` (area surrounding content) and `padding` (area inside border but outside content). While helpful for controlling exact size of HTML elements, we recommend using flexbox properties (covered in later submodule) to layout HTML elements for a more robust layout.

### 3 common ways to specify box dimensions

#### 1) Pixel count

Only works for block display elements. Generally less recommended because difficult to create responsive (mobile and desktop-friendly) layouts with fixed pixel sizes.

```css
p {
  width: 100px;
  height: 100px;
}
```

#### 2) Percent of parent container

Percentage is relative to the parent container, allows responsive sizing. Percentage height does not work unless parent has fixed size.

```css
p {
  width: 50%;
  height: 100px;
}
```

#### 3) Percent of viewport (window)

Viewport sizing allows for most responsive sizing based on screen size, but needs to be coordinated with other elements on screen since sizing is not relative to other elements.

```css
p {
  width: 100vw;
  height: 100vh;
}
```

[W3Schools documents](https://www.w3schools.com/cssref/css\_units.asp) all ways to specify box size.

### Debugging CSS boxes

Chrome helps us visualise CSS box properties of every element on every page at the bottom of the Styles window in the Elements tab in Chrome DevTools. To see box properties of any HTML element, right click the element and click "Inspect". Box properties in the box visualisation should match the most-specific box properties at the top of the CSS styles list (ordered in decreasing specificity).

![Chrome DevTools helps us visualise box properties of every HTML element on screen](<../../../.gitbook/assets/1.3 - CSS Layout - 3 - Box Model Chrome.png>)

{% hint style="info" %}
**Apply `box-sizing` CSS property to include padding and border in box size**

CSS does not include padding and border in box size by default. In the following example, CSS produces a box 300px wide (including 50px of padding on both sides), even though we specify width of 200px.

```css
p {
  width: 200px;
  padding: 50px;
}
```

To make `width` and `height` include padding and border space, apply the `box-sizing` CSS property to all elements.

```css
* {
  box-sizing: border-box;
}
```

[More on `box-sizing` by W3Schools](https://www.w3schools.com/css/css3\_box-sizing.asp).
{% endhint %}

## CSS `display` Property

The CSS `display` property controls the way target elements render on screen. The 2 most basic `display` values are `block` (full screen width) and `inline` (width of element only). By default, every HTML element has either block or inline layout.

`inline-block` is a 3rd `display` property that enables `inline` elements with `block` properties such as spacing on all sides. `inline` elements cannot have custom spacing around them.

![block, inline and inline-block are the most basic CSS display values. Source: Stack Overflow](<../../../.gitbook/assets/1.3 - CSS Layout - 2 - Inline and Block.png>)

## Centring Elements on Screen

The `margin` property's `auto` value allows us to automatically set left and right margins to centre an element on screen. Only `block` elements can be centred.&#x20;

```css
.main {
  margin: 0 auto; /* 0 top and bottom margin, auto left and right margin */
}
```

### Constraining element width

In addition to centring elements, we may also want to constraint element width to prevent content from becoming hard to read across the full width of a horizontal screen. We will look at fixed, percent and max width layout to do this.

#### Fixed-Width Layout

Fixed-width layout fixes the width of the target element, regardless of how small or large the screen size is. This works for large screen sizes but may look poor on small screen sizes.

```css
.main {
  width: 600px; /* 600px is reasonable default width of centre column */
  margin: 0 auto; /* 0 top and bottom margin, auto left and right margin */
}
```

#### Percent-Width Layout

Percent-width layout fixes width to be a percentage of screen width. This makes our content responsive but may not be what we want, especially if we want layout to be different across mobile and desktop.

```css
.main {
  width: 80%;
  margin: 0 auto; /* 0 top and bottom margin, auto left and right margin */
}
```

#### Max-Width Layout

Max-width layout allows our element to occupy 100% of screen width at smaller screen sizes but only a specified width at larger screen sizes. This helps when we wish to maximise screen real estate on mobile devices but not make content too wide on desktop devices.

```css
.main {
  max-width: 600px; /* be 100% width, until 600px */
  margin: 0 auto; /* 0 top and bottom margin, auto left and right margin */
}
```
