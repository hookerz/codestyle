#CSS Style Guide

##Introduction

CSS can feel like a cumbersome step when you’re developing a webapp but it’s important to get it right. In general, always write your CSS with the idea that someone else may have to jump in and work on it at any time. Within this guide you will learn the general rules, syntax, formatting, and file structure for writing CSS at Hook. We’re always open to suggestions as this is more of a living document than writing etched in stone, so be sure to speak up if you see something that could be improved.

If you come up with any questions while reading, feel free to hit up your boss. They’ll point you in the right direction or hook you up with someone to ping whenever something comes up.

##General

First off, we use Stylus. Read through the documentation here: https://learnboost.github.io/stylus/

- All CSS should look like one person wrote it.
- One level of indentation is achieved with 4 space characters.
- When grouping selectors, keep individual selectors to a single line.
- Comma-separated property values should include a space after each comma (e.g., box-shadow).
- Don't include spaces after commas within rgb(), rgba(), hsl(), hsla(), or rect() values. This helps differentiate multiple color values (comma, no space) from multiple property values (comma with space).
- Don't prefix property values or color parameters with a leading zero (e.g., .5 instead of 0.5 and -.5px instead of -0.5px).
- Lowercase all hex values, e.g., #fff. Lowercase letters are much easier to discern when scanning a document as they tend to have more unique shapes.
- Use shorthand hex values where available, e.g., #fff instead of #ffffff.
- Quote attribute values in selectors, e.g., input[type="text"]. They’re only optional in some cases, and it’s a good practice for consistency.
- Avoid specifying units for zero values, e.g., margin: 0; instead of margin: 0px;.

## Declaration order

Related property declarations should be grouped together following the order:

- Positioning
- Box model
- Typographic
- Visual

Positioning comes first because it can remove an element from the normal flow of the document and override box model related styles. The box model comes next as it dictates a component's dimensions and placement.

Everything else takes place inside the component or without impacting the previous two sections, and thus they come last.

```
.declaration-order
  /* Positioning */
  position absolute
  top 0
  right 0
  bottom 0
  left 0
  z-index 100

  /* Box-model */
  display block
  float right
  width 100px
  height 100px

  /* Typography */
  font normal 13px "Helvetica Neue", sans-serif
  line-height 1.5
  color #333
  text-align center

  /* Visual */
  background-color #f5f5f5
  border 1px solid #e5e5e5
  border-radius 3px

  /* Misc */
  opacity 1
```

## Media query placement

Place media queries as close to their relevant rule sets whenever possible. Don't bundle them all in a separate stylesheet or at the end of the document. Doing so only makes it easier for folks to miss them in the future. Here's a typical setup.

```
.element
  style
.element-avatar
  style
.element-selected
  style

@media (min-width: 480px)
  .element
    style
  .element-avatar
    style
  .element-selected
    style

```

