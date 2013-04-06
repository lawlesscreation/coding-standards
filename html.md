# HTML

## General coding style

- Closing tags for large blocks of content should end with a comment e.g.: `<!-- /selector -->`;
- Always close tags, including self-closing tags, e.g.: `<br />`, `<link />`;
- Remove any unnecessary attributes e.g.: `<script src="" />` instead of `<script type="text/javascript" src="" />`;
- styles up top, scripts down bottom;

```html
<div class="selector">
  <br />
</div><!-- /selector -->
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
<!--[if IE 7]> <html lang="en" class="no-js lte9 lte8 lte7"> <![endif]-->
<!--[if IE 8]> <html lang="en" class="no-js lte9 lte8"> <![endif]-->
<!--[if IE 9]> <html lang="en" class="no-js lte9"> <![endif]-->
<!--[if gt IE 9]><!--> <html lang="en" class="no-js"> <!--<![endif]-->
```

## JavaScript detection

With the use of [Modernizr](http://modernizr.com/) you can detect if JavaScript is available (or not) with the `.no-js` class. This class gets toggle to `js` by Modernizr.
You can then easily provide a gracefully degraded version for visitors without JavaScript if required.

## Multiple classes

Use multiple classes to help with OO CSS, for example:

```html
<a class="btn btn-large">button text</a>
```

But don't go *crazy*.

## Validation

Always validate code [W3C HTML validator](http://validator.w3.org).