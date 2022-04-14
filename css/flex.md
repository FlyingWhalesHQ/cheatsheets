---
layout: default
title: Flex
parent: CSS
nav_order: 1
---

# CSS Flex Cheatsheet

Properties and attributes for flex containers/parents

```css
display: flex | inline-flex;

flex-direction: row | row-reverse | column | column-reverse;
flex-wrap: nowrap | wrap | wrap-reverse;
flex-flow: column wrap;
justify-content: flex-start | flex-end | center | space-between | space-around | space-evenly | start | end | left | right; /* ... + safe | unsafe; */
align-items: stretch | flex-start | flex-end | center | baseline | first baseline | last baseline | start | end | self-start | self-end; /* + ... safe | unsafe */
align-content: flex-start | flex-end | center | space-between | space-around | space-evenly | stretch | start | end | baseline | first baseline | last baseline;
 /* + ... safe | unsafe */

/* Gaps */
gap: 10px;
gap: 10px 20px; /* row-gap column gap */
row-gap: 10px;
column-gap: 20px;
```

Properties for flex items/childrens

```css
order: 5; /* default is 0 */
flex-grow: 4; /* default 0 */
flex-shrink: 3; /* default 1 */
flex-basis:  20% /* default auto */
/* Shothand for flex-grow, flex-shrink and flex-basis */
flex: none | [ <'flex-grow'> <'flex-shrink'>? || <'flex-basis'> ];
```

## Links

- [A Complete Guide to Flexbox - CSS Tricks](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
- [Flex interactive demos by Yoksel](https://yoksel.github.io/flex-cheatsheet/)
