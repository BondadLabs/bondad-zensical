# bondad

A [Zensical](https://zensical.org/) theme with the bondad.org colours: a dark
scheme (`bondad-dark`), a light one (`bondad-light`), and optional terminal
accents (mono headings, a coral prompt, a blinking cursor).

This site is the theme's demo. Every page shows a group of components; flip
the scheme with the toggle in the header to check both.

## Enable it

```toml
[project.theme]
name = "bondad"
```

That's all a site needs. The theme brings its own palette, fonts, favicon
and logo. Set any of them in `[project.theme]` to override the default.

## What's on each page

| Page | Shows |
|------|-------|
| [Typography](typography.md) | Headings, links, lists, tables, inline code, keys, mark, insert and delete, footnotes |
| [Admonitions](admonitions.md) | Every admonition type, plain and collapsible |
| [Code](code.md) | Code blocks in several languages, highlighted lines, annotations, tabs |
| [Diagrams](diagrams.md) | Mermaid flowchart and sequence diagram |
| [Blog](blog/index.md) | Post excerpts, authors, categories, tags, read time, a pinned post, a draft (shown under `serve` only), pagination, archive |

Search lives in the header; the footer has previous/next links, the
copyright and social icons.
