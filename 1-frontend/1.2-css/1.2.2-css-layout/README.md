# 1.2.2: CSS Layout

## Learning Objectives

1. CSS layout is about organising HTML elements into nested boxes and determining their positions

## Introduction

![Organise HTML elements into conceptual boxes before planning how to use CSS for layout. Source: W3Schools](<../../../.gitbook/assets/1.3 - CSS Layout - 1 - Layout Example.gif>)

When determining how to layout elements with CSS, first organise elements into nested boxes, then determine which CSS styles need to apply to which boxes. By default browsers will render all HTML elements in a single vertical column.

## `display` CSS Property

The `display` CSS property determines whether HTML elements follow inline (width of element only) or block (full screen width) layout. By default, every HTML element follows either inline or block layout. We cannot customise vertical spacing above and below inline elements.

![Block layout stacks vertically; Inline layout stacks horizontally. Inline Block layout is a hybrid. Source: Stack Overflow](<../../../.gitbook/assets/1.3 - CSS Layout - 2 - Inline and Block.png>)

## CSS Box Model

![Margin is spacing outside the content's border. Padding is spacing inside the content's border. Source: W3Schools](<../../../.gitbook/assets/1.3 - CSS Layout - 3 - Box Model.png>)

​

The CSS Box model describes how much room a given element on the page takes up.

{% hint style="warning" %}
The following page describes some common box properties, but in general a layout should avoid relying on multiple layout boxes being an exact pixel size, because multiple interacting boxes can be complicated to manage with CSS.

A good default is to allow, as much as is possible, for the CSS rendering engine to lay out the boxes in a "natural" way.
{% endhint %}

### Base Box Size

Without any CSS a box (element) will be the size of it's contents. If the box is `display` `block`, it's width will expand to the parent (containing) container, then it will expand downward.

### Width & Height

There are several common ways to set the dimensions of a box:

#### Pixel

For elements that are display block, you can manually set the size of an element:

```css
p {
  width: 100px;
  height: 100px;
}
```

#### Percent

We can set the width of a box using relative measurements:

```css
p {
  width: 50%;
  height: 100px;
}
```

#### Viewport

We can set the size of a box using viewport units.

```css
p {
  width: 100vw;
  height: 100vh;
}
```

See more on viewport units here: [https://css-tricks.com/fun-viewport-units/](https://css-tricks.com/fun-viewport-units/)

### LImitations of Width & Height

You cannot set width & height on inline elements.

You cannot set percentage height, unless the parent container has a fixed size.

Without [flexbox](../../../1-frontend-fundamentals/css.3-flexbox), writing CSS that vertically centers boxes is difficult / not recommended.

### Seeing and Manipulating the Box

For every element that Chrome puts on the screen, we can see a helpful graphic that describes how much size the box takes up.

If you select an element in the elements tab and scroll to the bottom of the CSS pane you'll see the box model section.

![](../../../.gitbook/assets/dev-t-b-model.png)

With this tool you can highlight each part of the box. The size of the box reported in the tool should match the CSS styles applied (although other factors besides directly set CSS values may affect the size of the box).

![](../../../.gitbook/assets/dev-t-b-model-2.png)

Here you can see that the hovered section in the dev tools box model diagram is **highlighted in the same green** **color** on screen. Also note the size of the padding, 50px, matches the style applied in the pane above.

### Box Size Calculations

Note that the box model tools calculate the final size of the box in pixels. If we give a relative measurement in CSS like percent, the box diagram gives us the measurement in pixels.

![](../../../.gitbook/assets/dev-t-b-model-3.png)

### Consistent Sizing

One flaw of the default behavior of the box model is that the size of a box doesn't include it's padding. Consider the following example:

```css
p {
  width: 200px;
  padding: 50px;
}
```

This CSS produces a box 300px wide (padding adds 50px to EACH side), not 200px wide.

#### Box Sizing

With the box-sizing style we can set the dimension to include padding. This code sets the correct size calculation for every single element in the document. We'll use this code for every HTML page we style.

```css
*,
*:before,
*:after {
  box-sizing: border-box;
}
```

See more about box sizing here: [https://css-tricks.com/box-sizing/](https://css-tricks.com/box-sizing/)

## Further Reading

Video on box sizing: [https://www.youtube.com/watch?v=dLGr1Qb2nKc](https://www.youtube.com/watch?v=dLGr1Qb2nKc)

## 1.2.2.4: Layout: Fixed, Percent and Max Width

## Layout with Block

When we create our CSS layouts we'll be using container elements. These will form the underlying structure of our page layout. The first of these elements will be block elements. We will mostly use `div` elements as a plain, generic CSS layout container element.

Given this HTML:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8" />
    <link href="styles.css" rel="stylesheet" />
  </head>
  <body>
    <div class="main">
      <h1>All About Noodles</h1>
      <p>
        Noodles are a type of food made from unleavened dough which is rolled
        flat and cut, stretched or extruded, into long strips or strings.
        Noodles can be refrigerated for short-term storage or dried and stored
        for future use.
      </p>
      <p>
        Noodles are usually cooked in boiling water, sometimes with cooking oil
        or salt added. They are also often pan-fried or deep-fried. Noodle
        dishes can include a sauce or noodles can be put into soup. The material
        composition and geocultural origin is specific to each type of a wide
        variety of noodles. Noodles are a staple food in many cultures (see
        Chinese noodles, Japanese noodles, Korean noodles, Filipino noodles,
        Vietnamese noodles, and Italian pasta).
      </p>
      <h2>Origin</h2>
      <p>
        The earliest written record of noodles is found in a book dated to the
        Eastern Han period (25–220 CE). It became a staple food for the people
        of the Han dynasty. Food historians generally estimate that pasta's
        origin is from among the Mediterranean countries: homogenous mixture of
        flour and water called itrion as described by 2nd century Greek
        physician Galen, among 3rd to 5th centuries Palestinians itrium as
        described by the Jerusalem Talmud and itriyya (Arabic cognate of the
        Greek word), string-like shapes made of semolina and dried before
        cooking as defined by the 9th century Aramean physician and
        lexicographer Isho bar Ali.
      </p>
    </div>
  </body>
</html>
```

## Centering a Box

For boxes whose width is smaller than the parent box there is an easy way to horizontally center them: `margin` `auto`

```css
.main {
  width: 100px;
  margin: 0 auto; /* left and right margin auto*/
}
```

## Fixed Width Layout

By using this centering technique we can make a nice box that is centralized in the middle of the page.

By constraining the size of the content area this prevents the behavior where the text is spread all the way across a horizontal box, making it hard to read.

```css
.main {
  width: 600px; /* reasonable default size of a central box */
  background-color: white;
  padding: 20px;
  margin: 40px auto; /* left and right margin auto*/
}
```

#### Before

![](../../../.gitbook/assets/fixed-width-before.png)

#### After

![](../../../.gitbook/assets/screen-shot-2021-04-14-at-8.28.23-pm.png)

## Percent Width Layout

Another kind of design might call for a box that is always a percentage with of the page.

```css
.main {
  width: 80%;
  background-color: white;
  padding: 20px;
  margin: 40px auto; /* left and right margin auto*/
}
```

## Max Width

One major issue with this CSS is that if the device screen is less than 600px, the page will be cut off and scroll to one side.

To prevent this we can have it take up the entire screen width below a certain size. (To put it conversely, we can constrain the size of the box to no more than a certain number).

```css
.main {
  max-width: 600px; /* be 100% width, until 600px */
  background-color: white;
  padding: 20px;
  margin: 40px auto; /* left and right margin auto*/
}
```

## Height

Notice that in the examples the white box does not take up the rest of the vertical space of the page. This is because elements only fill up to the size in the vertical dimension. Some of these height issues can be solved with the Bootstrap library and/or flexbox.

## 1.2.2.5: Display: Inline Block

`inline-block` `display` style is used when we want to have box (block) like boxes next to each other in a layout.

There are older ways of doing this, involving `float`, and newer ways involving flexbox and CSS grid, but inline-block is one of the basic ways to get box-like elements to sit next to each other.

```html
<div class="article">
  Noodles are a type of food made from unleavened dough.
</div>
<div class="article">Veniam deserunt labore ullamco ea laboris esse sit.</div>
<div class="article">Irure ad ut nisi ut amet.</div>
<div class="article">
  Id minim amet dolor sint ex voluptate esse dolore duis minim consequat dolore
  adipisicing ut.
</div>
```

```css
body {
  background-color: pink;
}
.article {
  display: inline-block;
  background-color: white;
  padding: 20px;
  margin: 20px;
}
```

![](../../../.gitbook/assets/inline-block.png)

#### Properties of `inline-block`

- unlike `inline`, vertical margins and padding can be set on inline-block elements
- unlike `inline`, elements do not break within themselves to a new line.
- unlike `block`, the element does not take up 100% width by default.

## CSS Layout Gotchas

### White Spacing Between Elements

When using `inline-block`, whitespace in the HTML can affect the spacing of elements.

{% embed url="https://patrickbrosset.medium.com/when-does-white-space-matter-in-html-b90e8a7cdd33" %}

## Further Reading

Video on block, inline-block (also includes position fixed and absolute): [https://www.youtube.com/watch?v=x_i2gga-sYg](https://www.youtube.com/watch?v=x_i2gga-sYg)
