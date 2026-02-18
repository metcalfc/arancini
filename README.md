# 🧆 arancini

arancini is a minimalist, responsive [hugo](https://gohugo.io) theme with full base16 color scheme support and enhanced syntax highlighting. Based on [risotto](https://github.com/joeroe/risotto) by [Joe Roe](https://joeroe.io).

[![Version](https://img.shields.io/badge/semver-v1.0.0-blue)](https://semver.org)
![hugo build status](https://github.com/metcalfc/arancini/actions/workflows/hugo-build-exampleSite.yml/badge.svg)
![Code size](https://img.shields.io/github/languages/code-size/metcalfc/arancini)

![Screenshot of the arancini theme](https://raw.githubusercontent.com/metcalfc/arancini/main/images/screenshot.png)

## Features

* Plain, semantic HTML with no Javascript
* Plain CSS – no frameworks, no preprocessors, just simple and easy-to-customise stylesheets
* Uses [CSS Grid](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_grid_layout) for native responsive behaviour without arbitrary breakpoints
* Comes with [16 built-in colour schemes](#colour-schemes) based on popular terminal themes plus the ability to use custom themes using the [base16 system](https://github.com/monicfenga/base16-styles)
* **Enhanced syntax highlighting** that automatically adapts to any base16 color scheme
* **Full base16 variable support** for consistent theming across all elements

## Install

### Method 1: Hugo Modules (Recommended)

Initialize your site as a Hugo module:

```shell
hugo mod init github.com/yourusername/yoursite
```

Add arancini to your `hugo.toml` or `config.toml`:

```toml
[module]
  [[module.imports]]
    path = "github.com/metcalfc/arancini"
```

Hugo will automatically download the theme when you build your site.

### Method 2: Git Submodule

Add arancini as a git submodule:

```shell
git submodule add https://github.com/metcalfc/arancini.git themes/arancini
git submodule update --init --recursive
```

### Method 3: Git Clone

Clone the repository into your `themes` directory:

```shell
git clone https://github.com/metcalfc/arancini themes/arancini
```

**Note:** This method works best for non-git sites or when you want to modify the theme directly.

### Method 4: Download Release

Download the [latest release](https://github.com/metcalfc/arancini/releases) and extract it to your project's `themes/arancini/` directory.

## Update

**Hugo Modules:**
```shell
hugo mod get -u
```

**Git Submodule:**
```shell
git submodule update --remote --merge
```

**Git Clone:**
```shell
cd themes/arancini && git pull
```

**Download:** Replace the theme directory with the latest release.

## Configure

To use the theme, add `theme = 'arancini'` to your site's `hugo.toml`, or `theme: arancini` to your `hugo.yaml`.

See `exampleSite/config.toml` for the theme-specific parameters you need to add to your site's `hugo.toml` or `hugo.yaml` to configure the theme.

### Colour schemes

arancini uses the [base16 framework](https://github.com/chriskempson/base16) to define colour schemes that can be used with the `theme.palette` parameter.
A selection of 24 palettes (16 dark, 8 light) are bundled with the theme:

**Dark themes:** `apprentice`, `base16-dark`, `catppuccin-mocha`, `dracula`, `github-dark`, `gruvbox-dark`, `material`, `nord`, `onedark`, `papercolor-dark`, `solarized-dark`, `tender`, `tokyo-night-dark`, `windows-95`

**Light themes:** `base16-light`, `catppuccin-latte`, `github-light`, `gruvbox-light`, `nord-light`, `onelight`, `papercolor-light`, `solarized-light`, `tokyo-night-light`, `windows-95-light`

The default is `nord`.

| Palette           | Preview                                                                                                                        |
| ----------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| apprentice        | <img align="center" width="250" src="images/palette/apprentice.png"        alt="risotto theme with apprentice palette">        |
| base16-dark       | <img align="center" width="250" src="images/palette/base16-dark.png"       alt="risotto theme with base16-dark palette">       |
| base16-light      | <img align="center" width="250" src="images/palette/base16-light.png"      alt="risotto theme with base16-light palette">      |
| dracula           | <img align="center" width="250" src="images/palette/dracula.png"           alt="risotto theme with dracula palette">           |
| gruvbox-dark      | <img align="center" width="250" src="images/palette/gruvbox-dark.png"      alt="risotto theme with gruvbox-dark palette">      |
| gruvbox-light     | <img align="center" width="250" src="images/palette/gruvbox-light.png"     alt="risotto theme with gruvbox-light palette">     |
| material          | <img align="center" width="250" src="images/palette/material.png"          alt="risotto theme with material palette">          |
| papercolor-dark   | <img align="center" width="250" src="images/palette/papercolor-dark.png"   alt="risotto theme with papercolor-dark palette">   |
| papercolor-light  | <img align="center" width="250" src="images/palette/papercolor-light.png"  alt="risotto theme with papercolor-light palette">  |
| solarized-dark    | <img align="center" width="250" src="images/palette/solarized-dark.png"    alt="risotto theme with solarized-dark palette">    |
| solarized-light   | <img align="center" width="250" src="images/palette/solarized-light.png"   alt="risotto theme with solarized-light palette">   |
| tender            | <img align="center" width="250" src="images/palette/tender.png"            alt="risotto theme with tender palette">            |
| tokyo-night-dark  | <img align="center" width="250" src="images/palette/tokyo-night-dark.png"  alt="risotto theme with tokyo-night-dark palette">  |
| tokyo-night-light | <img align="center" width="250" src="images/palette/tokyo-night-light.png" alt="risotto theme with tokyo-night-light palette"> |
| windows-95        | <img align="center" width="250" src="images/palette/windows-95.png"        alt="risotto theme with windows-95 palette">        |
| windows-95-light  | <img align="center" width="250" src="images/palette/windows-95-light.png"  alt="risotto theme with windows-95-light palette">  |

The easiest way to use other base16 styles is to place .css file from https://github.com/monicfenga/base16-styles/tree/master/css-variables and place it in your `static/css/palettes` directory.

Or to define a wholly custom theme, you will need to define the following CSS variables for the following base16 colours (see [base16-dark.css](blob/main/static/css/palettes/base16-dark.css) for an example):

| Base | Default colour                             | Used for            | Examples                             |
| ---- | ------------------------------------------ | ------------------- | ------------------------------------ |
| 00   | <span class="base00">Dark</span>           | Background          | Page background                      |
| 01   | <span class="base01">│</span>              | Alt. background     | Content background                   |
| 02   | <span class="base02">│</span>              | In-text backgrounds | `<pre>`, `<code>`, `<kbd>`, `<samp>` |
| 03   | <span class="base03">│</span>              | Muted text          | `:before` & `:marker` symbols        |
| 04   | <span class="base04">│</span>              | Alt. foreground     | Aside text                           |
| 05   | <span class="base05">│</span>              | Foreground          | Content text                         |
| 06   | <span class="base06">│</span>              |                     |                                      |
| 07   | <span class="base07">Light</span>          |                     |                                      |
| 08   | <span class="base08">Red</span>            |                     |                                      |
| 09   | <span class="base09">Orange</span>         |                     |                                      |
| 0A   | <span class="base0A">Yellow</span>         | Highlights          | Selected text, `<mark>`              |
| 0B   | <span class="base0B">Green</span>          | Primary accent      | Logo                                 |
| 0C   | <span class="base0C">Cyan</span>           | Active links        | `a:active`, `a:hover`                |
| 0D   | <span class="base0D">Blue</span>           | Links               | `a:link`, `a:visited`                |
| 0E   | <span class="base0E">Magenta</span>        |                     |                                      |
| 0F   | <span class="base0F">Brown</span>          |                     |                                      |

For light mode palettes, the sequence of 00–07 should be reversed (light to dark, not dark to light).
Note that not all colours are currently used in the theme.

You you use these colours directly in content using the convenience classes `.baseXX` and `.bg-baseXX`.
For example:

```html
<span class="base0A">Yellow text</span>
<mark class="bg-base0D">Text highlighted in green</mark>
```

## Favicon

arancini will automatically use favicons placed in the `static/` directory.
The following files will be detected and included in your site's `<head>` section:

* `favicon.ico`
* `favicon-16x16.png`
* `favicon-32x32.png`
* `apple-touch-icon.png`
* `site.webmanifest`

You can generate these from an image or emoji using [favicon.io](https://favicon.io/) or a similar service.
They must be placed directly under your site's `static/` directory, i.e. not in in a subdirectory or `themes/arancini/static/`.

## Acknowledgements

This theme is based on [risotto](https://github.com/joeroe/risotto) by [Joe Roe](https://joeroe.io). The arancini theme adds enhanced syntax highlighting with full base16 color scheme support.

The 'cooked rice' emoji originally used as a favicon for the risotto theme was created by the [Twemoji project](https://twemoji.twitter.com/) and is licensed under [CC-BY 4.0](https://creativecommons.org/licenses/by/4.0/).
