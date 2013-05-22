# SCSS

## General coding style

Many of the CSS coding standards also apply to SCSS, obviously, but here are a few other things to note.

- Use `//` for SCSS comments (instead of `/* */`), SCSS comment will be removed from the CSS when compiled;
- Prefix any file that doesn't need to be compiled with an _underscore.scss e.g.: partials or files that are only ever imported;
- When nesting selectors, ask yourself if it's really necessary to do so. Heavy nesting can lead to bloated stylesheets;
- Keep track of your CSS file size(s) and periodically review your nesting strategy to avoid style bloat;
- Place a line break between each (s)css selector including nested selectors;

```scss
header {
  padding: 10px 20px;

  nav {
    float: left;
  
    li {display: block; }

    a {color: #fff; } //Note: this isn't nested in the <li> to help reduce code bloat

  }

}
```

## Variables
- Any `$variable` that is used in more than one file should be put in _vars.scss, others should be put at the top of the file where they're used;
- Create variables for your CSS animation properties, especially duration and delay. Consistent animation timing ensures eye-pleasing UI effects;
- Variables containing more than one word should use an underscore e.g.: `$variable_name`.

## Mixins
- Mixins should use hyphens for multiple words and/or underscores for media queries;

```scss
@mixin related-links_mobile {
  ...
}

@include related-links_mobile;
```
