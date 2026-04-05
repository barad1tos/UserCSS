# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This repository contains UserCSS dark theme stylesheets for various websites. These are installed via browser extensions (Stylus for Firefox/Chrome/Opera, Cascadea for Safari) and override website styling.

**Stylesheets:**
- `last-fm.user.css` - Last.fm dark theme
- `discogs.user.css` - Discogs dark theme
- `google.user.css` - Google dark theme
- `ptp.user.css` - PassThePopcorn dark theme (Raise mod)

## UserCSS Format

Each `.user.css` file follows the UserCSS specification with a metadata block:

```css
/* ==UserStyle==
@name        Site Name
@namespace   gomgon
@version     X.Y.Z
@homepageURL https://github.com/gomgon/UserCSS
@updateURL   https://raw.githubusercontent.com/gomgon/UserCSS/master/filename.user.css
@license     CC-BY-SA-4.0
@author      gomgon
@advanced color variable-name "Display Name" #HEXVAL
@advanced dropdown option-name "Display Name" { ... }
==/UserStyle== */
```

**Key metadata fields:**
- `@advanced color` - User-configurable color variables referenced as `/*[[variable-name]]*/` in CSS
- `@advanced dropdown` - Toggle options with inline CSS blocks
- `@advanced text user-css` - Custom user CSS injection point

## CSS Patterns

**Document targeting:**
```css
@-moz-document domain("example.com") {
  /* styles */
}
```

**Variable usage:**
```css
background: /*[[bg]]*/;
color: /*[[main-text]]*/;
```

## Version Updates

When modifying stylesheets, increment the `@version` field following semver (MAJOR.MINOR.PATCH).

## Installing / Deploying

There is no build step. The `.user.css` files are loaded directly by browser extensions:

```
# Firefox / Chrome / Opera
Install: Stylus extension → "Write new style" → paste file contents (or import URL)

# Safari
Install: Cascadea extension → paste file contents

# Local install from file
Stylus: Manage → Import → select .user.css file
```

After modifying a stylesheet, the browser extension will auto-update if installed via the raw GitHub URL. For local development, manually re-import the file after changes.

## Tech Stack

- **Language**: CSS (UserCSS spec)
- **Format**: `.user.css` with `==UserStyle==` metadata block
- **Distribution**: Browser extension (Stylus / Cascadea), installed via raw GitHub URL or manual import
- **No build tooling**: Pure CSS files, no compilation step required
