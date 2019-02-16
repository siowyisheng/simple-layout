# The Simple Guide to Layout

_Web layout explained simply._

[![GitHub license](https://img.shields.io/badge/license-MIT-blue.svg)](https://github.com/siowyisheng/simple-layout/blob/master/LICENSE) ![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)

## Table of Contents <!-- omit in toc -->

- [Overview](#overview)
- [Mobile Responsiveness](#mobile-responsiveness)
  - [Overlap elements](#overlap-elements)
  - [Center (left-right) all elements within a div](#center-left-right-all-elements-within-a-div)
  - [Center certain text within a div](#center-certain-text-within-a-div)
  - [Listing elements](#listing-elements)
  - [Mobile responsiveness](#mobile-responsiveness)
  - [Styling](#styling)

## Overview

Build your website quickly using **components**, then **format and lay them out**, all by giving html elements specific classes.

## Mobile Responsiveness

Define styles for mobile first, then add media queries for progressively larger screens. CSS ensures that the last-defined styles override the earlier defined ones.

Usually, having mobile styles first and then a set of desktop styles for screens above 768px will do fine.

```css
@media only screen and (min-width: 768px) {
  p {
    font-size: 16px;
  }
}
```

For greater specificity, you may want to specify landscape mobile styles above 576px, tablet styles above 768px and desktop styles above 992px. These are sensible breakpoints from [Bootstrap](https://getbootstrap.com/docs/4.2/layout/overview/#responsive-breakpoints).

### Overlap elements

```html
<div class="parent">
  <div class="child"></div>
  <div class="overlapsWithChild"></div>
</div>
```

```css
.parent {
  position: relative;
}

.overlapsWithChild {
  position: absolute;
  top: 0;
  left: 0;
}
```

### Center (left-right) all elements within a div

```css
div {
  display: flex;
  flex-direction: column;
  align-items: center;
}
```

### Center certain text within a div

```css
p {
  text-align: center;
}
```

### Listing elements

```html
<div class="parent">
  <div class="child">A</div>
  <div class="child">B</div>
  <div class="child">C</div>
  <div class="child">D</div>
  <div class="child">E</div>
  <div class="child">F</div>
  <div class="child">G</div>
</div>
```

```css
.parent {
  display: flex;
  flex-flow: column wrap;
  margin: -10px;
}
/* The negative margin offsets the 'outside padding' */
.child {
  flex: 0 0 25%;
  padding: 10px;
}
/* Some padding is often desired to space out the elements */
```

### Mobile responsiveness

#### Hide an element on small/large screens

```html
<div class="desktop">Desktop</div>
<div class="mobile">Mobile</div>
```

```css
.desktop {
  display: none;
  @media (min-width: 768px) {
    display: block;
  }
}

.mobile {
  display: block;
  @media (min-width: 768px) {
    display: none;
  }
}
```

#### Stack elements on a small screen

Here, the columns will stack on top of each other if the width is below 768px. Otherwise, they will be divided into 3 columns.

```html
<div class="parent">
  <div class="child">Your content</div>
  <div class="child">Your content</div>
  <div class="child">Your content</div>
</div>
```

```css
.parent {
  display: flex;
}

@media (min-width: 768px) {
  .child {
    flex: 0 0 33.333333%;
  }
}
```

#### Make an image responsive to the parent

```css
img {
  width: 100%;
  height: auto;
}
```

### Styling

#### Remove default browser list bullets

```html
<ul class="list-unstyled">
  <li>Your content</li>
  <li>Your content</li>
</ul>

<!-- or -->

<ol class="list-unstyled">
  <li>Your content</li>
  <li>Your content</li>
</ol>
```

#### Remove the default underlines from links

```html
<a class="text-decoration-none">Your link</a>
```
