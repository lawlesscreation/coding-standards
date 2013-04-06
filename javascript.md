# JavaScript

## General coding style

- use `===` instead of `==`;
- `'use strict'` when possible;
- use single quotes for strings e.g.: `document.getElementById('id')`;

## Naming conventions

- All functions should be named using `camelCase`;
- All variables should be named using an `under_score`, if more than 1 word;

## Commenting

Inline comments should use // this allows them to be easily commented out for debugging:

```javascript
var string = 'string'; // a string
```

Functions should have a comment block /* */ at the start that explains what they do and what is returned:

```javascript
/*
 * Function that does something cool
 * @return string: something that is returned
 */
functionName: function () {
  return string;
},
```

JavaScript files should have an explanation at the top similar to a function but that includes details such as name, description, author, version, license where appropriate: 

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

## Performance

### Use async, when appropriate

Using async means the script is downloaded asynchronously while the rest of the page continues to get parsed.
The script is guaranteed to be executed as soon as the download is complete. Keep in mind that multiple async scripts will be executed in no specific order.

```html
<script async src="example.js"></script>
```

## Validation

Always validate code [JS Hint](www.jshint.com).