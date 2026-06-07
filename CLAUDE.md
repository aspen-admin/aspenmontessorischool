# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project overview

Static HTML/CSS website for Aspen Montessori School, hosted on GitHub Pages at `www.aspenmontessorischool.com` (configured via `CNAME`). Two campuses: **Bothell** and **Kenmore**, WA. No build step, no package manager, no framework — just HTML, CSS, and vendored Bootstrap 5 assets.

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
| `my-logo.png` | School logo, displayed in navbar at 80×80px |
| `favicon-32x32.png` | Browser tab favicon |
| `assets/dist/css/` | Vendored Bootstrap 5 CSS (do not edit) |
| `assets/dist/js/` | Vendored Bootstrap 5 JS bundle (do not edit) |

## Brand

- **Primary green:** `#2D5A3A` (dark variant `#1e3f28`, light tint `#eef4f0`)
- **Accent yellow:** `#E8A838` (dark variant `#c48a20`)
- All colors are defined as CSS variables in `:root` at the top of the `<style>` block — edit there, not inline
- Logo file: `my-logo.png` in project root

## Contact info

- **Email:** aspenmontessorischool@gmail.com
- **Phone:** 425-318-9956
- **Campuses:** Bothell, WA and Kenmore, WA
- **Hours:** Mon–Fri, 7:30 am – 6:00 pm

## Page sections (in order)

| Section | id | Notes |
|---|---|---|
| Navbar | — | White background, logo + school name + nav links |
| Hero | `#hero` | Gradient green background, tagline, two CTA buttons |
| About | `#about` | Three value cards (child-led, community, materials) |
| Now Enrolling | `#enroll` | Yellow band announcing Kenmore Campus enrollment; "Schedule a Tour" button links to `#contact` |
| Testimonials | `#testimonials` | Three parent quote cards with star ratings |
| Contact/CTA | `#contact` | Green band, email + phone buttons, two campus locations |
| Join Our Team | `#careers` | Light green band; hiring copy + email button → aspenmontessorihr@gmail.com |
| Footer | — | Copyright, Privacy/Terms links |

## Age range

Serves children **12 months to 5 years**.

## Deployment

Pushing to `main` triggers GitHub Pages deployment automatically (see `.github/workflows/`). The custom domain is set via `CNAME` — do not delete that file.
