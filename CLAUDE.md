# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

This is a single-file static personal website for Riely Chen (`index.html`). There is no build system, no package manager, and no dependencies beyond a Google Fonts stylesheet loaded from a CDN. To preview, open `index.html` directly in a browser.

## Architecture

Everything lives in `index.html`:

- **CSS** — all styles are in a `<style>` block in `<head>`. Layout uses a centered `.wrap` container (max 650px). Theming uses CSS custom properties (`--ink`, `--muted`, `--bg`, `--rule`, `--toggle-bg`, `--toggle-hover`) defined on `:root`/`[data-theme="light"]` and overridden on `[data-theme="dark"]`.
- **HTML** — content sections use `.section` + `.section-label` for labelled groups of `<ul>` items, plain `<p>` tags for prose, and `<hr>` as a section divider before the footer.
- **JavaScript** — a single inline `<script>` at the bottom handles three things:
  1. **Theme toggle**: reads `localStorage` + `prefers-color-scheme`, sets `data-theme` on `<html>`, persists the choice.
  2. **Email copy**: clicking the Email link copies `rielychen@gmail.com` to the clipboard and temporarily changes the link text to "Copied!".
  3. **Analog clock**: an SVG clock in the footer with `#clock-hour` and `#clock-minute` lines rotated every second via `setInterval`.

## Design conventions

- Font is STIX Two Text (serif), loaded from Google Fonts.
- All colors are referenced through CSS custom properties — never use hard-coded color values.
- The theme toggle button is fixed top-right; it shows a moon icon in light mode and a sun icon in dark mode, toggled via `[data-theme="dark"]` CSS selectors.
- The footer is a flex row: social links on the left, year + clock on the right.
- Mobile breakpoint is `max-width: 600px`, which reduces `.wrap` padding.
