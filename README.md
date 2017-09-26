# Myst - Markedly Structured Text

Myst is a markup text format that tries to marry the extensibility and strong semantic markup properties of reStructuredText with some features of Markdown that the Myst authors have found extremely convenient in practice. It should be easy to pick up for users of either language.

The syntax choices of Myst are such that many relatively simple Markdown or reST files will be automatically compliant Myst documents. For example, Markdown documents with no raw HTML and reST ones whose choice of header markers matches the Myst spec, will automatically be valid Myst.


## Features

### From the perspective of reST

A few areas of reST have been restricted or modified:

* Only ATX (#-style) headings are used.  The different levels, `#` through `######`, map to `h1` through `h6`.

* Braces can be used to specify additional class attributes on a heading, e.g., `# Name of my Book {.title}` maps to `<h1 class="title">`.  By default, at least `title`, `subtitle`, and `chapter` are supported.

* Single-backticks inline are *always* interpreted as preformatted (code) text. This is equivalent to saying that the default role has been hardcoded to be code.

### Additions from Markdown

* Markdown link syntax, `[My site](http://example.com)`, is supported, with the addition that extra attributes can be passed in an optional `{}` block:

```
[My site](http://example.com){target=_blank rel=external}
```

* Triple-backticks blocks with optional language header for source code blocks (from GitHub-flavored Markdown)

### Other features

* Supports LaTeX math between single-dollar signs for inline math (e.g., [math_dollar.py](https://github.com/matthew-brett/texext/blob/master/texext/math_dollar.py)). For displayed math, using `.. math::` is still recommended, as it isn't that much more typing and it allows for additional information such as labels to be passed.

* For images, the markdown syntax is supported:

```
![My logo](fig/logo.png)
```

and extra arguments can be passed via `{}`:

```
![My logo](fig/logo.png){width=80% height=50%}
```

## License

This project is licensed under the terms of the "New" BSD license.
