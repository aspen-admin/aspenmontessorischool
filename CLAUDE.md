# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project overview

Static HTML/CSS website for Aspen Montessori School (Bothell, WA), hosted on GitHub Pages at `www.aspenmontessorischool.com` (configured via `CNAME`). No build step, no package manager, no framework — just HTML, CSS, and vendored Bootstrap 5 assets.

## How to preview

Open `index.html` directly in a browser, or serve it locally:

```
npx serve .
# or
python -m http.server 8080
```

## Structure

| Path | Purpose |
|---|---|
| `index.html` | Single-page site — all content lives here |
| `carousel.css` | Custom styles layered on top of Bootstrap |
| `assets/dist/css/` | Vendored Bootstrap 5 CSS (do not edit) |
| `assets/dist/js/` | Vendored Bootstrap 5 JS bundle (do not edit) |

## Current state — everything is placeholder
Key placeholder locations in `index.html`:


## Deployment

Pushing to `main` triggers GitHub Pages deployment automatically (see `.github/workflows/`). The custom domain is set via `CNAME` — do not delete that file.
