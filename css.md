# CSS Style Guide

## Introduction

CSS can feel like a cumbersome step when you’re developing a webapp but it’s important to get it right. In general, always write your CSS with the idea that someone else may have to jump in and work on it at any time. Within this guide you will learn the general rules, syntax, formatting, and file structure for writing CSS at Hook. We’re always open to suggestions as this is more of a living document than writing etched in stone, so be sure to speak up if you see something that could be improved.

If you come up with any questions while reading, feel free to hit up your boss. They’ll point you in the right direction or hook you up with someone to ping whenever something comes up.

## General

First off, we use SCSS. Read through the documentation here: http://sass-lang.com/documentation/file.SASS_REFERENCE.html#syntax

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

##B.E.M - Block Element Modifier

B.E.M. is an easy, flexible and modular methodology we use to structure and organize our CSS at Hook.  It is a strict methodology that makes our css more readable, easier to work with, more robust, explicit and easier to scale. (http://www.getbem.com)

Block: Standalone entity that is meaningful on it’s own.
Examples: header, container, menu, checkbox, input

Element: A part of a block that has no standalone meaning and is semantically tied to its block.
Examples: menu item, list item, checkbox caption, header title

Modifier: A flag on a block or element.  Use them to change appearance or behavior.
Examples: disabled, highlighted, checked, fixed, size big, color yellow

```
.main-dialog {
  background: #fff;
  left: 50%;
  max-width: 550px;
  position: absolute;
  top: 50%;
  transform: translate(-50%, -50%);
  width: 100%;

  &__header {
    display: block;
    padding: 25px 60px 0 60px;
    width: auto;
  }

  &__content {
    padding: 60px;
    position: relative;
  }

  &__footer {
    padding: 0 60px 25px 60px;
  }

  .__footer--highlight {
      background: #e71b0f;
      color: #fff;
    }
  }
```

## Declaration order

CSS declaration order should be alphabetical.  This also happens to fall within google standards which is both convenient and easy for everyone to understand.

```
.declaration-order {
  background: #fff;
  display: block;
  height: 500px;
  left: 50%;
  position: absolute;
  top: 50%;
  width: 500px;
}
```

## Media query placement

Place media queries at the end of the document and comment accordingly. Doing so consistently makes it very clear on where responsive styling is located.

##Shorthand notation

Strive to limit use of shorthand declarations to instances where you must explicitly set all the available values. Common overused shorthand properties include:

- padding
- margin
- font
- background
- border
- border-radius

Often times we don't need to set all the values a shorthand property represents. For example, HTML headings only set top and bottom margin, so when necessary, only override those two values. Excessive use of shorthand properties often leads to sloppier code with unnecessary overrides and unintended side effects.

##Comments

Code is written and maintained by people. Ensure your code is descriptive, well commented, and approachable by others. Great code comments convey context or purpose. Do not simply reiterate a component or class name.

Be sure to write in complete sentences for larger comments and succinct phrases for general notes.

##Class Names

- Keep classes lowercase and use dashes (not underscores or camelCase). Dashes serve as natural breaks in related class (e.g., .btn and .btn-danger).
- Avoid excessive and arbitrary shorthand notation. .btn is useful for button, but .s doesn't mean anything.
- Keep classes as short and succinct as possible.
- Use meaningful names; use structural or purposeful names over presentational.
- Prefix classes based on the closest parent or base class.
- Use .js-* classes to denote behavior (as opposed to style), but keep these classes out of your CSS.

It's also useful to apply many of these same rules when creating Stylus variable names.

##Selectors

- Use classes over generic element tag for optimum rendering performance.
- Avoid using several attribute selectors (e.g., [class^="..."]) on commonly occuring components. Browser performance is - known to be impacted by these.
- Keep selectors short and strive to limit the number of elements in each selector to three.
- Scope classes to the closest parent only when necessary (e.g., when not using prefixed classes).

##Organization

- Organize sections of code by component.
- Develop a consistent commenting hierarchy.
- Use consistent white space to your advantage when separating sections of code for scanning larger documents.
- When using multiple CSS files, break them down by component instead of page. Pages can be rearranged and components moved.
