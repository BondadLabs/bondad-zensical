# bondad-zensical

The Bondad theme for [Zensical](https://zensical.org/): the bondad.org colours
as two schemes, `bondad-dark` and `bondad-light`, plus optional terminal
accents (mono headings, a coral `>` prompt before the page title, a blinking
cursor after the site name).

Needs Zensical 0.1.0 or later (Python 3.11+).

## Install

From a built wheel or a checkout of this repository:

```sh
uv add path/to/bondad_zensical-0.1.0-py3-none-any.whl
# or
uv add path/to/Bondad-Zensical
```

## Enable

```toml
[project.theme]
name = "bondad"
```

No `extra_css` is needed. The theme sets these defaults, and any of them can
be overridden in `[project.theme]`:

| Setting | Default |
|---------|---------|
| `palette` | Follow the system, with a toggle: system → `bondad-light` → `bondad-dark` |
| `font.text` / `font.code` | Inter / JetBrains Mono |
| `favicon` | `assets/images/favicon.svg`: the `b_` tile, inverted in dark browser themes |
| `logo` | `assets/images/logo.svg`: the same tile, fixed dark |

An override replaces the whole key. A site that sets `[[project.theme.palette]]`
replaces the three-entry palette entirely. To use a single scheme with no
toggle:

```toml
[project.theme.palette]
scheme = "bondad-dark"
primary = "custom"
accent = "custom"
```

Always use `primary = "custom"` and `accent = "custom"` with the Bondad
schemes. Any other value applies one of Zensical's built-in colours on top.

### If you override `main.html`

The theme loads its stylesheets from its own `main.html`. If a site's
`custom_dir` also has a `main.html`, copy the `fonts` and `styles` blocks
from [`src/bondad_zensical/main.html`](src/bondad_zensical/main.html) into
it. Otherwise the schemes won't load.

## Options

```toml
[project.extra.bondad]
terminal = false
```

| Option | Default | Effect |
|--------|---------|--------|
| `terminal` | `true` | Mono, extra-bold `h1` to `h3`; coral `> ` before the page title; blinking `_` cursor after the site name in the header; brand-coloured text selection. Set to `false` for a plain recolour. |

The accents only apply under the Bondad schemes. The cursor stops blinking
when the reader prefers reduced motion.

## Palette

| | `bondad-dark` | `bondad-light` |
|---|---|---|
| Background | `#0E1116` | `#F6F7F9` |
| Text | `#F2F4F8` (body `#E3E7EE`) | `#0E1116` |
| Muted text | `#9AA3B2` | `#4E5663` |
| Primary / links | `#FF6B57` | `#C0391F` |
| Code background | `#151A22` | `#ECEEF2` |
| Borders / raised surfaces | `#262D38` | `#D9DEE5` |

The light primary is `#C0391F`, not the logo's `#D0402C`, because the logo
colour is 4.4:1 against the light background, under WCAG AA for small text.

Syntax highlighting and admonitions share five hues per scheme:

| Hue | Dark | Light | Admonitions |
|-----|------|-------|-------------|
| Blue | `#4CB8FF` | `#0B5FA3` | note, info, todo |
| Violet | `#B9A6FF` | `#5B3FB8` | abstract, summary, tldr, example |
| Green | `#3DDC97` | `#13784F` | tip, hint, important, success, check, done |
| Amber | `#FFB86B` | `#8F5200` | question, help, faq, warning, caution, attention |
| Coral | `#FF6B57` | `#C0391F` | failure, fail, missing, danger, error, bug |
| Muted | `#9AA3B2` | `#4E5663` | quote, cite |

### Contrast

All text in the theme's own styles is at least 4.5:1 against what it sits on,
including composited tints: admonition backgrounds, highlighted code lines,
the active nav item and marked text. This was measured in Chrome across every
demo page in both schemes. UI elements (admonition icons, Mermaid node
borders) are at least 3:1. Light-mode tints are capped at 8% for this reason,
and highlighted code lines in light mode use an opaque tint lighter than the
code background.

One known gap is upstream: Zensical's search dialog draws its secondary text
(result count, breadcrumbs) at 45–54% opacity inside a shadow root, which a
theme can't restyle. That text is 3.0–4.2:1, with these schemes and with
Zensical's own.

## Adding a scheme

[`bondad.css`](src/bondad_zensical/assets/stylesheets/bondad.css) is split so
that a new scheme is one block of `--bondad-*` tokens:

1. Copy the `[data-md-color-scheme="bondad-dark"]` (or `-light`) block in
   section 1 and change the values.
2. Name it `bondad-<name>-dark` or `bondad-<name>-light`. The suffix selects
   the mode rules in section 2 (`color-scheme`, tints, shadows,
   `#only-dark` / `#only-light` images). The `bondad-` prefix selects the
   shared mapping and component rules.
3. Reference it from a site's palette, or add it to
   [`mkdocs_theme.yml`](src/bondad_zensical/mkdocs_theme.yml) to make it a
   default.

Then re-run the contrast checks on the new values.

## Development

```sh
uv sync                  # installs the theme in editable mode with zensical
uv run zensical serve    # demo site from docs/, uses name = "bondad"
uv build                 # wheel and sdist in dist/
```

The demo site in `docs/` covers headings, links, lists, tables, every
admonition type, code in several languages, inline code, keys, mark,
insert/delete, tabs, Mermaid, search and the footer. It also has a blog
(`docs/blog/`) with a pinned post, a draft, two pages of posts, categories,
tags, an author with an avatar, an archive and related links. The draft
only shows under `zensical serve`. Check changes in both
schemes and through the system toggle.

## Known issues

- Zensical copies every file in the theme folder into the built site, so
  `__init__.py`, `mkdocs_theme.yml` and (once Python has imported the
  package) `__pycache__/` appear at the site root. They're harmless.
  Other packaged themes, such as catppuccin-zensical, have the same problem.
