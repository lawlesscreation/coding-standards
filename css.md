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
- Quote attribute values in selectors, e.g.: `input[type="text"]`;

```css
.selector {font-size: 100%; }

.selector,
.another-selector {
  background: rgba(0,0,0,.5);
  color: #fff;
  font-size: 100%;
}
```

## Naming conventions

### Selectors

- A good rule is to never go more than four levels deep (the Inception Rule!);
- It is helpful if classes used to show <i>state</i> have a prefix, for example `is-locked`, `has-children`;
- CSS selectors should use a loose [BEM naming](http://coding.smashingmagazine.com/2012/04/16/a-new-front-end-methodology-bem/) convention. For example:

```css
.menu {} /* block */

.menu_item {} /* block_element */

.menu_item--current {} /* block_element--modifier */
```

Whilst not as string as BEM's `__` convention, it should allow for a clean, logical, OO naming convention. 


## Properties

- Use shorthand properties where suitable e.g.: `font:` or `background:`;
- Omit leading 0's from values e.g.: padding: .25em;
- Use hex color codes #000 unless using rgba and lowercase all hex values;
- Use font weight numbers instead of words e.g.: `font-weight: 400;`;
- Use percentages for font sizes instead of absolute units (EM, REM etc are also fine, just be consistent);
- Provide a fallback for older browsers that do not support modern CSS properties or values such as background gradients, rgba etc;
- Vendor prefixes should be avoided but if required, place them before the non-prefixed property;
- Alphabtically order your properties or group related properties;
- Don't include spaces after commas within `rgb()`, `rgba()` etc;

```css
.selector {
  background: #000; /* fallback */
  background: rgba(0,0,0,.8);
  -moz-border-radius: 5px; /* only if required */
  -webkit-border-radius: 5px; /* only if required */
  border-radius: 5px;
  position: abosolute;
  left: 0;
  top: 0;
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
/*!
 * File name ( e.g.: Main styling / Print )
 *
 * Description:   Describes the files purpose ( e.g.: contains all styling for screen / print )
 * Author:        Usually me...
 *
 * Version:       0.0.1
 */

/* A COLLECTION ( e.g.: COMPONENTS )
  --------------------------------------------------------------------------------*/
.selector {}


/* AN ITEM ( e.g.: HEADER )
------------------------------------------*/
.selector {}


/* An item element ( e.g.: header search) */
.selector {}

.selector {} /* an inline note */



/*------------------------------------------------------------------------------------
  MEDIA QUERY START COMMENT
------------------------------------------------------------------------------------*/
@media only screen {

  /* A COLLECTION ( e.g.: COMPONENTS )
  ----------------------------------------------------------------------------------*/
  .selector {}

} /* end media */
```

## Specificity (id vs. class)

Elements that occur exactly once inside a page *could* use IDs, otherwise always use classes.
If in doubt, use a class.

- Good candidates for ids: homepage, header, footer;
- Bad candidates for ids: navigation, item listings.

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

Always validate your CSS [W3C CSS validator](http://jigsaw.w3.org/css-validator/).

Running your CSS through [CSS Lint](http://csslint.net/) is also wise. My own [csslintrc](.csslintrc.json) file can be found in this repo for use during development.
