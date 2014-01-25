# CSS

- [General coding style](#general-coding-style)
- [Naming conventions](#naming-conventions)
- [Properties](#properties)
- [Commenting](#commenting)
- [Specificity (id vs. class)](#specificity-id-vs-class)
- [Multiple classes](#multiple-classes)
- [Media queries (mobile first)](#media-queries-mobile-first)
- [Validation](#validation)

## General coding style

- Put a space before `{` in rule declarations;
- Put a space after `:` in property declarations;
- Single CSS properties should appear on a single line;
- Multiple CSS selectors should each appear on a new line;
- Utilize CSS animations as best you can, they can save you a load of JavaScript code down the road;
- Avoiding qualified name selectors e.g.: `div.post {}`;


```css
.selector {font-size: 100%; }
```

```css
.selector,
.another-selector {
  font-size: 100%;
  color: #fff;
  background: rgba(0,0,0,.5);
}
```

## Naming conventions

### Selectors

- A good rule is to never go more than four levels deep (the Inception Rule!);
- It is helpful if classes used to show <i>state</i> have a prefix, for example `is-locked`, `has-children`;
- CSS selectors should use a loose [BEM naming](http://coding.smashingmagazine.com/2012/04/16/a-new-front-end-methodology-bem/) convention. For example:

```css
.menu {} /* block */

.menu_item {} /* block-element */

.menu_item--current {} /* block-element-modifier */
```

Whilst not as string as BEM's `__` convention, it should allow for a clean, logical, OO naming convention. 


## Properties

- Use shorthand properties where suitable e.g.: `font:` or `background:`;
- Omit leading 0's from values e.g.: padding: .25em;
- Use hex color codes #000 unless using rgba;
- Use font weight numbers instead of words e.g.: `font-weight: 400;`;
- Use percentages for font sizes instead of absolute units (EM, REM etc are also fine, if supported);
- Provide a fallback for older browsers that do not support modern CSS properties or values such as background gradients, rgba etc;
- If browser prefix properties are required, place them before the non-prefixed property;

```css
.selector {
  background: #000; /* fallback */
  background: rgba(0,0,0,.8);
  -moz-border-radius: 5px;
  -webkit-border-radius: 5px;
  border-radius: 5px;
}
```

### DRYing CSS properties

Try to write DRYer code when possible. DRY (Don't Repeat Yourself) code usually means two things:

1. Less actual code, meaning smaller file sizes, more efficient code, etc.
2. Less to maintain; not repeating yourself simplifies things when you come to make changes or additions in the future.

For example:

```css
.menu_item {
  background-position: 0 50%;
  background-repeat: no-repeat;
}

.menu_item--current {background-image: url(active.gif); }

.menu_item--disabled {background-image: url(disabled.gif); }

```

Abstracting out the repeated parts and avoiding using shorthand means writing a few more lines of code, but massively trims down the amount of repetition.

## Commenting

Comments can get messy, but I find this pattern works well for me - each to their own...

```css
/*
 * File name ( e.g.: Typography )
 *
 * Describes the files purpose ( e.g.: Contains all typography styling for headings, lists, etc )
 */

/* A COLLECTION ( e.g.: GRID )
----------------------------------------------------------------------------------*/
.selector {}


/* AN ITEM ( e.g.: NAVIGATION )
------------------------------------------*/
.selector {}


/* An item chunk ( e.g.: header search) */
.selector {}

.selector {} /* a selector/property inline comment */



/*------------------------------------------------------------------------------------
  MEDIA QUERY START COMMENT
------------------------------------------------------------------------------------*/
@media only screen and () {

  /* A COLLECTION ( e.g.: COMPONENTS )
  ----------------------------------------------------------------------------------*/
  .selector {}

} /* end media */
```

## Specificity (id vs. class)

Elements that occur exactly once inside a page *could* use IDs, otherwise always use classes.
If in doubt, use a class.

- Good candidates for ids: header, footer, modal popups;
- Bad candidates for ids: navigation, item listings, item view pages (ex: issue view).

## Multiple classes

To aid with BEM and OO CSS, sometimes using and chaining multiple classes can be useful (though it should be avoided whenever possible).
Just remember IE6 doesn't play nicely with these.

```css
.btn--large.btn--inline {}
```

## Media queries (mobile first)

Unless there is a good reason (sometimes there are), media queries should take the approach of mobile first and build up into the larger screen version.
What break points you use depends on the design and content that needs to adapt.

## Validation

Always validate code [W3C CSS validator](http://jigsaw.w3.org/css-validator/).
