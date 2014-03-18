# jQuery

- [General coding style](#general-coding-style)
- [Selectors](#selectors)
- [DOM Manipulation](#dom-manipulation)
- [Plug-ins](#plug-ins)
- [Performance](#performance)
- [CDN](#cdn)
- [Validation](#validation)

## General coding style

- Use `.on()` fot attaching event handlers e.g.: `.on('click', function() {...});` instead of `.click(function() {...})`;
- If a chain grows over 3 links, use appropriate line breaks and indentation to make the code readable;

```javascript
$("#myLink")
  .addClass("bold")
  .on("click", myClickHandler)
  .on("mouseover", myMouseOverHandler)
  .show();
```


### Functions

- Prefix your **global** function with 'jquery' so its easily recognised as a jQuery function e.g.: `jqueryFunctionName`.
Functions *inside* an already names jQuery function or plugin local scope don't necessarily need this;

### Variables

- All variables that are used to store/cache jQuery objects should have a name prefixed with a `$` e.g.: `var $myDiv = $("#myDiv");`;


## Selectors

- Use find for Id->Child nested selectors. The `.find()` approach is faster because the first selection is handled without going through the Sizzle selector engine;

```javascript
// BAD, a nested query for Sizzle selector engine
var $productIds = $("#products div.id");

// GOOD, #products is already selected by document.getElementById() so only div.id needs to go through Sizzle selector engine
var $productIds = $("#products").find("div.id");
```


## DOM Manipulation

- Use string concatenation or `array.join()` over `.append()`;

```javascript
// BAD
var $myList = $("#list");
for(var i = 0; i < 10000; i++){
  $myList.append("<li>"+i+"</li>");
}

// GOOD
var array = [];
for(var i = 0; i < 10000; i++){
  array[i] = "<li>"+i+"</li>";
}
$myList.html(array.join(''));
```

- Don’t Act on Absent Elements;

```javascript
// BAD: This runs three functions before it realizes there's nothing in the selection
$("#nosuchthing").slideUp();
 
// GOOD
var $mySelection = $("#nosuchthing");
if ($mySelection.length) {
  $mySelection.slideUp();
}
```


## Plug-ins

Useful background reading [jQuery plugin authoring](http://docs.jquery.com/Plugins/Authoring) particularly regarding namespacing and methods.

- Use the [jQuery boilerplate](https://github.com/jquery-boilerplate/boilerplate) for plugin creation;
- Prefix your plugin name with 'jquery' so its easily recognised as a jQuery plugin e.g.: `jqueryFunkyCarousel`;
- Prefix your folder name with 'jquery' e.g.: /jquery.funky-carousel/;
- Prefix your file name with 'jquery' e.g.: jquery.funky-carousel.js;

### Check if a plugin function exists

Sometimes its good to check if a function exist before trying to use it. Particularly if its a 3rd party plug-in:

```javascript
if ($.isFunction($.fn.FUNCTION_NAME)) {
  // Code for calling the function etc goes here
}
```

## Performance

### Don't use jQuery, for everything

Sometimes vanilla JavaScript can be even simpler than jQuery.

Why use the attr() method to search for an ID?

```javascript
$('a').on('click', function() {
  console.log( $(this).attr('id') );
});
```

If you can can get this attribute natively and faster through this:

```javascript
$('a').on('click', function() {
  console.log( this.id );
});
```

### Avoid using `document.ready`

This is because by putting your scripts at the end of the DOM (before the `</body>` tag) you know the DOM is going to be compiled by the time your scripts run.

## CDN

I personally think its still a good idea to grab jQuery and jQuery UI from a CDN:

```html
<script src="//ajax.googleapis.com/ajax/libs/jquery/1.9.0/jquery.min.js"></script>
<script>window.jQuery || document.write('<script src="js/jquery/1.9.0/jquery.min.js"><\/script>')</script>
<script src="//ajax.googleapis.com/ajax/libs/jqueryui/1.10.0/jquery-ui.min.js"></script>
<script>window.jQuery.ui || document.write("<script src='plugins/jqueryui/1.10.0/jquery-ui.min.js'>\x3C/script>")</script>
```

## Validation

Always validate code [JS Hint](http://jshint.com/). My own [jshintrc](.jshintrc) and [jscsrc](.jscsrc) file can be found in this repo for use during development.
