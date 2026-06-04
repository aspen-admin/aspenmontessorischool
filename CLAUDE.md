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

## Brand

- **Primary green:** `#2D5A3A` (dark variant `#1e3f28`, light tint `#eef4f0`)
- **Accent yellow:** `#E8A838` (dark variant `#c48a20`)
- **Logo:** drop your logo file in the project root and update the `<img src="logo-placeholder.png">` in the navbar

## Page sections (in order)

| Section | id | Notes |
|---|---|---|
| Navbar | — | Fixed top, green background, logo + nav links |
| Hero | `#hero` | Gradient green background, tagline, two CTA buttons |
| About | `#about` | Three value cards (child-led, community, materials) |
| Programs | `#programs` | Three cards: Toddler (18mo–3yr), Primary (3–6yr), Extended Care |
| Testimonials | `#testimonials` | Three parent quote cards |
| Contact/CTA | `#contact` | Green band, email + phone buttons, address line |
| Footer | — | Copyright, Privacy/Terms links |

## Still needs real content


## Deployment

Pushing to `main` triggers GitHub Pages deployment automatically (see `.github/workflows/`). The custom domain is set via `CNAME` — do not delete that file.
