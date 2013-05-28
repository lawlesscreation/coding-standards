# JavaScript

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

### Selectors

- Try to prefix all JavaScript created selectors with `js-`. The idea is that you should be able to tell a which classes have been inserted with JavaScript;

## Commenting

JavaScript files should have an explanation at the top, which includes details such as name, description, author, version, license where appropriate: 

```javascript
/*
 * Name: Awesome plugin
 * Description: Does something really cool!
 * Version: 0.1
 * 
 * Author: Matt Lawson
 * License: licenced under MIT - http://opensource.org/licenses/mit-license.php
 */
```

Functions should have a comment block `/* */` at the start that explains what they do and what, if anything, is returned:

```javascript
/*
 * Function that does something cool
 * @return true or whatever is returned
 */
function functionName() {
  return true;
}
```

Inline comments should use `//` this allows them to be easily commented out for debugging:

```javascript
var string = 'string'; // a string
```

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

## Performance

### Use async, when appropriate

Using async means the script is downloaded asynchronously while the rest of the page continues to get parsed.
The script is guaranteed to be executed as soon as the download is complete. Keep in mind that multiple async scripts will be executed in no specific order.

```html
<script async src="example.js"></script>
```

## Validation

Always validate code [JS Hint](www.jshint.com).
