# Myst - Markedly Structured Text

Myst is a markup text format that tries to marry the extensibility and strong semantic markup properties of reStructuredText with some features of Markdown that the Myst authors have found extremely convenient in practice. It should be easy to pick up for users of either language.

The syntax choices of Myst are such that many relatively simple Markdown or reST files will be automatically compliaint Myst documents. For example, Markdown documents with no raw HTML and reST ones whose choice of header markers matches the Myst spec, will automatically be valid Myst.


## Features

### From the perspective of reST

A few areas of reST have been restricted:

* ATX-style headers as in markdown is preferred.  Only for titles/subtitles should overline/underline headers (see below) be used.

* Underline/overline headers are still allowed for ease of integration, but they are discouraged (other than for ) and the interpretation of the level markers is hardcoded. Only the following are allowed:

    - `=` with overline, for the document title (maps to `<h1 class="title">` and a `<title>` tag is also emitted)
    - `-` with overline, for the document subtitle (maps to `<h2 class="subtitle">`)
    - `#` with overline, for parts (maps to `<h3 class="part">`)
    - `*` with overline, for chapters (maps to `<h1 class="chapter">`)
    - `=`, for sections (maps to `<h2 class="section">`)
    - `-`, for subsections (maps to `<h3 class="subsection">`)
    - `^`, for subsubsections (maps to `<h4 class="subsubsection">`)
    - `"`, for paragraphs (maps to `<h5 class="paragraph">`)
    - `'`, for paragraphs (maps to `<h6 class="paragraph">`)

* Single-backticks inline are *always* interepreted as preformatted (code) text. This is equivalent to saying that the default role has been hardcoded to be code.

### Additions from Markdown 

* Markdown link syntax (`[My site](http://example.com)`) is supported, with the addition that extra attributes can be passed in an optional `{}` block:

```
{target=_blank rel=external}[My site](http://example.com)
```

* Triple-backticks blocks with optional language header for source code blocks (from Github-flavored Markdown)


### Other features

* The dollarmath sphinx extension is built-in, supporting LaTeX math between single-dollar signs for inline math. For displayed math, using `.. math::` is still recommended, as it isn't that much more typing and it allows for additional infromation such as labels to be passed.

* For images, the markdown syntax is supported with one addition: extra arguments can be passed via `{}`:

```
!{width=80% height=50%}[My logo](fig/logo.png)
```


## License

This project is licensed under the terms of the "New" BSD license.
