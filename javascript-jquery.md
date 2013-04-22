# jQuery

## General coding style

- Use `.on()` fot attaching event handlers e.g.: `.on('click', function() {...});` instead of `.click(function() {...})`;

### Naming conventions

- Any variable returning a jQuery object should be prefixed with `$` e.g.: `$variable_name`;
- Prefix your **global** function with 'jquery' so its easily recognised as a jQuery function e.g.: `jqueryFunctionName`.
Functions *inside* an already names jQuery function or plugin local scope don't necessarily need this;

## Plug-ins

Useful background reading [jQuery plugin authoring](http://docs.jquery.com/Plugins/Authoring) particularly regarding namespacing and methods.

- Use the [jQuery boilerplate](https://github.com/jquery-boilerplate/boilerplate) for plugin creation;
- Prefix your plugin name with 'jquery' so its easily recognised as a jQuery plugin e.g.: `jqueryFunkyCarousel`;
- Prefix your folder name with 'jquery' e.g.: /jquery.funky-carousel/;
- Prefix your file name with 'jquery' e.g.: jquery.funky-carousel.js;

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

## CDN

I personally think its still a good idea to grab jQuery and jQuery UI from a CDN:

```html
<script src="//ajax.googleapis.com/ajax/libs/jquery/1.9.0/jquery.min.js"></script>
<script>window.jQuery || document.write('<script src="js/jquery/1.9.0/jquery.min.js"><\/script>')</script>
<script src="//ajax.googleapis.com/ajax/libs/jqueryui/1.10.0/jquery-ui.min.js"></script>
<script>window.jQuery.ui || document.write("<script src='plugins/jqueryui/1.10.0/jquery-ui.min.js'>\x3C/script>")</script>
```

## Validation

Always validate code [JS Hint](www.jshint.com).