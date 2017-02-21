# CSS Guidelines

- [Principles](#principles)
- [Tools](#tools)
- [Architecture](#architecture)
- [Naming Conventions](#naming-conventions)
- [Linting](#linting)
- [Credits/Inspiration](#credits--inspiration)

## Principles

* Consistency
* Maintainability
* Readability
* Scalability

## Tools

PostCSS details coming soon

## Architecture

### Folder Structure

We prefix our directories with the number associated with the order in which it's imported in my main styles.css file.

```
css/
|
| -- 0_vendor/
| -- 1_settings/
| -- 2_base/
| -- 3_components/
| -- 4_layout/
| -- 5_helpers/
| -- 6_overrides/
```

#### Vendor

`0_vendor` includes any third party CSS that can't be imported via npm.

#### Settings

`1_settings` is a place to store global variables, mixins, etc. that don't directly compile into CSS.

#### Base

`2_base` is where classless element selectors are given some basic styles.

#### Components

`3_components` includes all of our repeatable patterns, or components. Component classes are prefixed with `c-`.

#### Layout

`4_layout` includes styles for more structural elements like page layouts and grids. Layout classes are prefixed with `l-`.

#### Helpers

`5_helpers` is where "helper" classes are defined. Helper classes are prefixed with `h-` and include an `!important` rule.

#### Overrides

`6_overrides` - Override vendor styles, write hacky CSS due to framework limitations, etc.

### File Names

The main file, `styles.css`, looks something like this:

```css
/* ==========================================================================
 * Styles
 * ========================================================================== */

/* Vendor */
@import "normalize.css";
@import "0_vendor/...";

/* Settings */
@import "1_settings/...";

/* Base */
@import "2_base/...";

/* Components */
@import "3_components/...";

/* Layout */
@import "4_layout/...";

/* Helpers */
@import "5_helpers/...";

/* Overrides */
@import "6_shame/...";
```

## Naming Conventions

### Namespacing

We use the following namespacing:

| Type             | Prefix          | Example                       |
| ---------------- | --------------- | ----------------------------- |
| Components       | `c-`            | `c-button`<br>`c-card`        |
| Layout Modules   | `l-`            | `l-container`<br>`l-grid`     |
| Helpers          | `h-`            | `h-clearfix`                  |
| States           | `is-`<br>`has-` | `is-active`<br>`has-loaded`   |
| JavaScript Hooks | `js-`           | `js-accordion`                |

### BEM

We use the [BEM](http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/) naming convention:

```css
.block { ... }
.block__element { ... }
.block--modifier { ... }
.block__element--modifier { ... }
```

#### BEM Do's and Don'ts

* Don't use a modifier outside of the context of its owner.

##### 👎 DON'T

```html
<button class="c-button--large"></button>
```

##### 👍 DO

```html
<button class="c-button c-button--large"></button>
```

* Don't combine multiple BEM entities on a single DOM node.

##### 👎 DON'T

```html
<button class="c-button c-icon">...</button>
```

##### 👍 DO

```html
<button class="c-button">
  <span class="c-icon">...</span>
</button>
```
  
## Order

### Declaration Order

Coming Soon

### Nesting Order

Use the following order for nesting selectors:

```css
.card {
  /* CSS Variables */
  /* Note: Not fully supported as of 8/1/2016 http://caniuse.com/#feat=css-variables */
  --color: #fff;
  
  /* Applies and Mixins */
  @apply --example;
  @mixin --something;
  
  /* Declaration List */
  display: block;
  ...
  z-index: 1;

  /* Media Queries */
  @media screen and (min-width: 900px) {
    ...
  }

  /* Pseudo States */
  &:hover {
    ...
  }

  /* Pseudo Elements */
  &::before,
  &::after {
    ...
  }

  &:nth-child(odd) {
    ...
  }

  /* Modifiers */
  &--small {
    ...
  }

  /* Concatenated Selectors */
  &.is-active {

  }

  /* Nested Elements */
  &__body {
    ...
  }
  
  /* Nested Selectors */
  .label {
    ...
  }
}
```

## Linting
* [Stylelint](https://github.com/jonmilner/stylelint-config)

## Credits / Inspiration
* [cssguidelin.es](http://cssguidelin.es/)
* [sass-guidelin.es](http://sass-guidelin.es)
* [chris-pearce/css-guidelines](https://github.com/chris-pearce/css-guidelines/)
