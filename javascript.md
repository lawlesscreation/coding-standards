# JavaScript

- [General coding style](#general-coding-style)
- [Naming conventions](#naming-conventions)
- [Functions](#functions)
- [Selectors](#selectors)
- [Commenting](#commenting)
- [Performance](#performance)
- [Validation](#validation)

## General coding style

- Use `===` instead of `==`;
- `'use strict'` when possible;
- Use single quotes for strings e.g.: `document.getElementById('id')`;
- Comma seperate multiple variables e.g.:

```javascript
var string = 'string',
    another_string = 'another string',
    third_string = 'third string';
```

## Naming conventions

- All functions should be named using `camelCase`;
- All variables should be named using an `under_score`, if more than 1 word;

### CSS selector naming

- Try to prefix all JavaScript created ID's or classes with `js-`. The idea is that you should be able to tell which classes have been inserted with JavaScript, e.g.: `js-tabs`, `js-is-hidden`;

## Functions

### Basic function syntax

This is the syntax for a basic JavaScript function and how to call it, nothing exciting:

```javascript
function functionName() {
  // Code to be executed ONLY when the function is called
}

// Calling the function
functionName();
```

### Self-executing functions

It's quite simple to make a function run automatically when a page loads, or when a parent function is called. Simply wrap your function in parenthesis, and then append an additional set, which essentially calls the function:

```javascript
(function functionName() {
  // Code to be self-executed
})();
```

## Selectors

- Cache your selectors <strong>once</strong> at the start of the file (if global) or function;
- Use the cached selectors to find other elements, rather than searching the whole DOM again;

```javascript
function functionName() {
  var foo = document.getElementById('foo');
  //BAD
  var bar = document.getElementsByClassName('bar');
  // GOOD
  var bar = foo.getElementsByClassName('bar');
  ...
}
```

## Commenting

JavaScript files should have an explanation at the top, which includes details such as name, description, author, version, license where appropriate: 

```javascript
/*!
 * Awesome scripts|plugin
 *
 * Does something really cool!
 *
 * @version: 0.1
 * @author: @lawlesscreation
 * @license: licenced under MIT - http://opensource.org/licenses/mit-license.php
 */
```

Functions should have a comment block `/* */` at the start that explains what they do and what, if anything, is returned:

```javascript
/*
 * Function name
 *
 * A function that does something really really cool
 *
 * @requires: libraries or plugins that are required
 * @url: url to function or plugin if available
 * @return boolean|string: - true or whatever is returned
 */
function functionName() {
  return true;
}
```

Inline comments should use `//` this allows them to be easily commented out for debugging:

```javascript
var string = 'string'; // a string
```

## Performance

### Use async, when appropriate

Using async means the script is downloaded asynchronously while the rest of the page continues to get parsed.
The script is guaranteed to be executed as soon as the download is complete. Keep in mind that multiple async scripts will be executed in no specific order.

```html
<script async src="example.js"></script>
```

## Validation

Always validate code [JS Hint](http://jshint.com/). My own [jshintrc](.jshintrc) and [jscsrc](.jscsrc) file can be found in this repo for use during development.
