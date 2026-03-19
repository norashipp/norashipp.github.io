# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

Static academic website for Nora Shipp (astronomy professor at UW), hosted on GitHub Pages at norashipp.com. The site uses Jekyll only for GitHub Pages deployment — there is no build step locally. All pages are plain HTML files that can be previewed by opening them directly in a browser.

## Deployment

Pushing to `master` automatically deploys via GitHub Pages. No build command needed.

To preview locally with Jekyll (optional):
```bash
bundle exec jekyll serve
```

## Architecture

**No build system or framework** — every page is self-contained HTML. All pages share:
- A consistent `<nav>` with links to all pages; set `class="active"` on the current page's link
- `<link rel="stylesheet" href="assets/css/main.css">` in `<head>`
- A `<footer>` at the bottom

**Single stylesheet:** [assets/css/main.css](assets/css/main.css) — contains all styles. CSS custom properties in `:root` control the palette and fonts:
- Colors: `--purple` (#4a1f66), `--purple-mid`, `--purple-light`, `--bg` (#faf9f7)
- Fonts: `--font-serif` (Palatino), `--font-sans` (Gill Sans)

**Page width variants:**
- `.page` — max-width 860px, used by most pages
- `.page-wide` — max-width 1000px, used by wider content

## Page-Specific Patterns

**Publications** ([publications.html](publications.html)): Uses `<ul class="pub-list">` with `<li class="pub-item">` elements. Each item has `.pub-num`, `.pub-title` (italic), `.pub-authors` (bold `<strong>` for lab members), and `.pub-meta` (journal/arXiv link). Add `class="pub-advised"` to items led by group members (adds a star prefix). Shipp's name is always `<strong>Shipp</strong>`.

**People** ([people.html](people.html), [undergrads.html](undergrads.html)): Uses `.people-grid` containing `.person-card` elements with `.person-photo`, `.person-name`, `.person-role`, and `.person-links`.

**Home page** ([index.html](index.html)): Two-column `.home-hero` (text left, GIF right), followed by `.home-split` (two-column grid for recent publications and news). News items use `.news-item` with `.news-date` and `.news-text`.

**Research** ([research.html](research.html)): `.research-item` blocks with optional `.research-figure` and `.figure-caption`. Related papers listed under `.key-papers`.

**CV** ([cv.html](cv.html)): `.cv-section` with `.cv-entry` (grid: content left, date right as `.cv-date`). Talks use `.cv-table`.

**Visuals** ([visuals.html](visuals.html)): `.viz-post` blocks (inline `<style>` in the file) with `.viz-date`, `.viz-title`, `.viz-img`, `.viz-caption`, and `.viz-credit`. Uses page-local CSS rather than classes in main.css.

## Content Updates

- **New publication:** Add to both [publications.html](publications.html) (full list) and [index.html](index.html) (recent 3 on home page).
- **New person:** Add a `.person-card` in [people.html](people.html); photos go in `images/`.
- **New news item:** Add `.news-item` in [index.html](index.html) at the top of the news section.
