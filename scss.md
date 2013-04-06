# SCSS

## General coding style

Many of the CSS coding standards also apply to SCSS, obviously, but here are a few other things to note.

- Use // for SCSS comments (instead of /* */), SCSS comment will be removed from the CSS when compiled;
- Prefix any file that doesn't need to be compiled with an _underscore.scss e.g.: partials or files that are only ever imported;
- Any `$variable` that is used in more than one file should be put in _vars.scss, others should be put at the top of the file where they're used;
