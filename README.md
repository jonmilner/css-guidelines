
# CSS Guidelines

## Folder and File Structure

A variation of the [7-1 Pattern](http://sass-guidelin.es/#the-7-1-pattern) by Hugo Giraudel.

```
css/
|
| -- 0_vendor/
| -- 1_utilities/
| -- 2_base/
| -- 3_components/
| -- 4_layout/
```

## Naming Convention

Use [BEM](http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/) naming convention:

```css
.block { ... }
.block__element { ... }
.block--modifier { ... }
.block__element--modifier { ... }
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
