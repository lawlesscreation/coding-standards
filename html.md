# HTML

- [General coding style](#general-coding-style)
- [Doctype](#doctype)
- [Conditional comments](#conditional-comments)
- [JavaScript detection](#javascript-detection)
- [Multiple classes](#multiple-classes)
- [Validation](#validation)

## General coding style

- Closing tags for large blocks of content should end with a comment e.g.: `<!-- .selector -->`;
- Always close tags, including self-closing tags, e.g.: `<br />`, `<link />`;
- Remove any unnecessary attributes e.g.: `<script src="" />` instead of `<script type="text/javascript" src="" />`;
- styles at the top, scripts at the bottom;
- HTML attributes should be in alphabetical order for consistency and readability;
- A boolean attribute does not need to be declared, e.g.: `disabled` instead of `disabled="disabled"`;

```html
<div class="selector" role="banner">
  <br />
</div><!-- .selector -->
```

## Doctype

For simplicity (and future proofing), use the HTML5 doctype:

```html
<!DOCTYPE html>
```

## Conditional comments

Using conditional comments on the `<html>` tag means you are able to place all CSS for Internet Explorer into one file and prefix the selectors, `.ie8 .selector {}`.
They are designed to cascade back through versions so IE7 will also get IE9 and IE8 fixes. This generally reduces the repetition of CSS fixes across versions.

```html
<!--[if IE 7]> <html class="lte9 lte8 lte7" lang="en"> <![endif]-->
<!--[if IE 8]> <html class="lte9 lte8" lang="en"> <![endif]-->
<!--[if IE 9]> <html class="lte9" lang="en"> <![endif]-->
<!--[if gt IE 9]><!--> <html lang="en"> <!--<![endif]-->
```

## Multiple classes

Use multiple classes to help with OO CSS, for example:

```html
<a class="btn btn--large">button text</a>
```

But don't go *crazy*.

## Validation

Always validate code [W3C HTML validator](http://validator.w3.org).
