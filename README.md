# CSS Guidelines

## Principles
* Consistency
* Maintainability
* Readability
* Scalability

## Tools
PostCSS

## Architecture

### Folder Structure
We prefix our directories with the number associated with the order in which it's imported in my main styles.css file.
```
css/
|
| -- 0_vendor/
| -- 1_utilities/
| -- 2_base/
| -- 3_components/
| -- 4_layout/
```

### File Names
The main file, `styles.css`, looks something like this:
```css
/* ==========================================================================
 * Styles
 * ========================================================================== */

/* Vendor */
@import "vendor.css";

/* Utilities */
@import "1_utilities/...";

/* Base */
@import "2_base/...";

/* Components */
@import "3_components/...";

/* Layout */
@import "4_layout/...";

/* Helpers */
@import 5_helpers/...";
```

## Namespacing
We use the following namespacing:

| Type             | Prefix          | Example                       |
| ---------------- | --------------- | ----------------------------- |
| Components       | `c-`            | `c-button`<br>`c-card`        |
| Layout Modules   | `l-`            | `l-container`<br>`l-grid`     |
| Helpers          | `h-`            | `h-clearfix`                  |
| States           | `is-`<br>`has-` | `is-active`<br>`has-loaded`   |
| JavaScript Hooks | `js-`           | `js-accordion`                |

## Naming Convention
We use the [BEM](http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/) naming convention:

```css
.block { ... }
.block__element { ... }
.block--modifier { ... }
.block__element--modifier { ... }
```

### BEM Do's and Don'ts
* Don't use a modifier outside of the context of its owner.

#### 👎 DON'T
```html
<button class="c-button--large"></button>
```

#### 👍 DO
```html
<button class="c-button c-button--large"></button>
```

### BEM Things to Avoid
* Avoid combining multiple BEM entities on a single DOM node.
  ```html
  <!-- Avoid -->
  <button class="c-button c-icon">...</button>

  <!-- Instead -->
  <button class="c-button">
    <span class="c-icon">...</span>
  </button>
  ```
  
## Nesting Order
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
* Stylelint: http://stylelint.io/

## Credits / Inspiration
* [cssguidelin.es](http://cssguidelin.es/)
* [sass-guidelin.es](http://sass-guidelin.es)
* [chris-pearce/css-guidelines](https://github.com/chris-pearce/css-guidelines/)
