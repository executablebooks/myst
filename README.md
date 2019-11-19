# Myst - Markedly Structured Text

*Note: This is a proof-of-concept repository to discuss extending rST to behave more like Markdown in some cases, it's meant for brainstorming and discussing, and should not be treated as a final plan or commitment!*

Myst is a markup text format that tries to marry the extensibility and strong semantic markup properties of reStructuredText with some features of Markdown that the Myst authors have found extremely convenient in practice. It should be easy to pick up for users of either language.

The syntax choices of Myst are such that many relatively simple Markdown or reST files will be automatically compliant Myst documents. For example, Markdown documents with no raw HTML and reST ones whose choice of header markers matches the Myst spec, will automatically be valid Myst.

**Note:** there's an implementation of [reStructuredText in JavaScript](https://www.npmjs.com/package/restructured) that includes an [online demo](https://seikichi.github.io/restructured), it could be useful as a reference for client-side tooling.

## Features

### From the perspective of reST

A few areas of reST have been restricted or modified:

* [Setext headers](https://github.github.com/gfm/#setext-headings) are **only** recommended for a few semantic roles that don't really exist in Markdown (which maps purely to H1..H6 HTML levels): document title, subtitle and parts.  These are mapped in html to H1, H2 and H3 respectively, but with additional class attributes to support custom styling:

    - `=` with overline, for the document title (maps to `<h1 class="title">` and a `<title>` tag is also emitted)
    - `-` with overline, for the document subtitle (maps to `<h2 class="subtitle">`)
    - `#` with overline, for parts (maps to `<h3 class="part">`)

* For other heading levels, [ATX headers](https://github.github.com/gfm/#atx-heading) are used. Setext headers are allowed for backwards compatibility with reST, but with a fixed interpretation of the levels, as follows (this is the convention used in the [Python documentation guide](https://docs.python.org/devguide/documenting.html#sections)):

    - `*` with overline, for chapters (maps to `<h1 class="chapter">`)
    - `=`, for sections (maps to `<h2 class="section">`)
    - `-`, for subsections (maps to `<h3 class="subsection">`)
    - `^`, for subsubsections (maps to `<h4 class="subsubsection">`)
    - `"`, for paragraphs (maps to `<h5 class="paragraph">`)
    - `'`, for paragraphs (maps to `<h6 class="paragraph">`)

* For ATX headers, the above six levels correspond to `#` ... `######`.

* Single-backticks inline are *always* interpreted as preformatted (code) text. This is equivalent to saying that the default role has been hardcoded to be code.

### Additions from Markdown 

* Markdown link syntax, `[My site](http://example.com)`, is supported, with the addition that extra attributes can be passed in an optional `{}` block:

```
[My site](http://example.com){target=_blank rel=external}
```

* Triple-backticks blocks with optional language header for source code blocks (from GitHub-flavored Markdown)

  ```{r}
  x<-seq(1, 10)
  ```

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
