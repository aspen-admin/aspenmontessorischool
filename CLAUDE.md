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
| `index.html` | Main single-page site — all enrollment/about/contact content |
| `careers.html` | Dedicated careers page — open positions, benefits, FAQ, application process |
| `llms.txt` | Plain-text site summary for AI/LLM crawlers — keep in sync with any content changes |
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

- **General email:** aspenmontessorischool@gmail.com
- **HR email:** aspenmontessorihr@gmail.com
- **Phone:** 425-318-9956
- **Campuses:** Bothell, WA and Kenmore, WA
- **Hours:** Mon–Fri, 7:30 am – 6:00 pm

## Campus addresses

| Campus | Address | Hours |
|---|---|---|
| Bothell | 4024 222nd Pl SE, Bothell, WA 98021 | Mon–Fri, 8:45 am – 4:45 pm |
| Kenmore | 17605 80th CT NE, Kenmore, WA 98028 | Mon–Fri, 7:30 am – 5:30 pm |

## Page sections

### index.html (in order)

| Section | id | Notes |
|---|---|---|
| Navbar | — | White background, logo (links to `#`) + school name + nav links; no "Home" item — logo serves that role; "Join Our Team" links to `careers.html` |
| Now Enrolling | `#enroll` | First section — full-width yellow band announcing Kenmore Campus enrollment; "Schedule a Tour" button links to `#contact` |
| Hero | `#hero` | Gradient green background, tagline, CTA button |
| About | `#about` | Kids activity carousel + three value cards (child-led, community, materials) |
| Testimonials | `#testimonials` | Three parent quote cards with star ratings |
| FAQ | `#faq` | Accordion — ages, campuses, hours, Montessori philosophy, enrollment, touring |
| Contact/CTA | `#contact` | Green band, email + phone buttons, two campus locations |
| Join Our Team | `#careers` | Light green teaser band; "View Open Positions" button → `careers.html`; email HR button |
| Footer | — | Copyright, Privacy/Terms links |

### careers.html (in order)

| Section | id | Notes |
|---|---|---|
| Navbar | — | Same as index; "Join Our Team" marked active |
| Hero | `#hero` | Green gradient, tagline, "View Open Positions" + "Contact HR" CTAs |
| Open Positions | `#positions` | Four job cards: Lead Montessori Teacher, Assistant Teacher, Floater, Office Admin |
| Why Join Aspen | `#benefits` | Four benefit cards: Meaningful Work, Supportive Team, Professional Growth, Competitive Benefits |
| How to Apply | `#process` | Four numbered steps: Resume → Call → Campus Visit → Welcome |
| FAQ | `#faq` | Accordion — hiring status, certification, pay, benefits, how to apply |
| CTA | `#cta` | Green band, "Email Our HR Team" button |
| Footer | — | Same as index |

## Open positions (careers.html)

| Role | Type | Campus | Pay |
|---|---|---|---|
| Lead Montessori Teacher | Full-Time | Bothell & Kenmore | $20.00–$25.00/hr |
| Assistant Teacher | Full-Time / Part-Time | Bothell & Kenmore | $18.00–$25.00/hr |
| Classroom Floater / Substitute | Part-Time | Bothell & Kenmore | — |
| Campus Director | Full-Time | Kenmore | — |
| School Office Administrator | Full-Time | Kenmore | — |

Assistant Teacher benefits: Health insurance, 401(k), paid time off, flexible schedule, employee discount.

## Age range

Serves children **12 months to 5 years**.

## Deployment

Pushing to `main` triggers GitHub Pages deployment automatically (see `.github/workflows/`). The custom domain is set via `CNAME` — do not delete that file.

---

## SEO & LLM optimization standards

Every HTML page on this site must follow these standards. Apply all of them whenever creating a new page or making content changes to an existing one.

### Required meta tags (every page)

```html
<title>[Page-specific title] | Aspen Montessori School – Bothell & Kenmore, WA</title>
<meta name="description" content="[150–160 chars, include primary keyword + location + CTA]">
<meta name="keywords" content="[8–12 comma-separated search terms, location-specific]">
<meta name="author" content="Aspen Montessori School">
<meta name="robots" content="index, follow">
<link rel="canonical" href="https://www.aspenmontessorischool.com/[page.html]">
```

- Description must be **150–160 characters**, include the primary keyword, location (Bothell/Kenmore WA), and an action phrase.
- Keywords must be **location-specific** ("Montessori teacher jobs Bothell WA") not generic ("teacher jobs").
- Keep title under **60 characters** for display in SERPs.

### Open Graph (every page)

```html
<meta property="og:type" content="website">
<meta property="og:url" content="https://www.aspenmontessorischool.com/[page.html]">
<meta property="og:title" content="[Same as <title>]">
<meta property="og:description" content="[Same as meta description, or slightly expanded]">
<meta property="og:image" content="https://www.aspenmontessorischool.com/assets/kidsactivities/1_.jpg">
<meta property="og:site_name" content="Aspen Montessori School">
<meta property="og:locale" content="en_US">
```

### Twitter Card (every page)

```html
<meta name="twitter:card" content="summary_large_image">
<meta name="twitter:title" content="[Same as <title>]">
<meta name="twitter:description" content="[Concise, under 200 chars]">
<meta name="twitter:image" content="https://www.aspenmontessorischool.com/assets/kidsactivities/1_.jpg">
```

### JSON-LD structured data

Add as `<script type="application/ld+json">` blocks in `<head>`, after the Twitter Card tags.

**Every sub-page (non-index)** must include a `BreadcrumbList`:

```json
{
  "@context": "https://schema.org",
  "@type": "BreadcrumbList",
  "itemListElement": [
    { "@type": "ListItem", "position": 1, "name": "Home", "item": "https://www.aspenmontessorischool.com/" },
    { "@type": "ListItem", "position": 2, "name": "[Page Name]", "item": "https://www.aspenmontessorischool.com/[page.html]" }
  ]
}
```

**Page-specific schema types to use:**

| Page | Schema types |
|---|---|
| `index.html` | `ChildCare` (business info + locations), `FAQPage` |
| `careers.html` | `BreadcrumbList`, `FAQPage` (hiring Q&A), `JobPosting` × N (one per open role) |
| Any new page | Use the most specific applicable Schema.org type |

**JobPosting required fields** (when adding/editing a job):
- `title`, `description`, `datePosted`, `validThrough`, `employmentType`
- `baseSalary` with `minValue`/`maxValue` and `unitText: "HOUR"` when pay is known
- `hiringOrganization` (name, sameAs, logo)
- `jobLocation` array with full `PostalAddress` for each campus
- `qualifications`, `jobBenefits`, `applicationContact`

**FAQPage** — include a `FAQPage` block whenever a page has a visible FAQ accordion. The Q&A text must exactly match what is visible on the page.

### Heading hierarchy

Every page must follow a strict h1→h2→h3→h4 outline. Do not skip levels.

| Level | Usage |
|---|---|
| `h1` | One per page — hero/page title only |
| `h2` | Section headings (`section-title` class) |
| `h3` | Card titles within sections (job cards, benefit cards, step cards, FAQ headers) |
| `h4` | Sub-labels within cards (e.g. "Responsibilities", "Requirements") |

Use CSS to control visual size — never choose a heading level for its default font size.

### Section accessibility

Every `<section>` must have an `aria-label` describing its content:

```html
<section id="positions" aria-label="Open Positions">
```

### llms.txt — keep in sync

`llms.txt` is the AI-crawler-facing summary of the entire site. Update it whenever:
- A job title, pay range, campus, or location changes
- A new page is added
- FAQ answers change
- Contact info or hours change

The file lives at `https://www.aspenmontessorischool.com/llms.txt` and is indexed by LLMs, Perplexity, ChatGPT browsing, and similar tools. Stale data here means AI engines give wrong answers about the school.

### Checklist for new or edited pages

- [ ] Title tag under 60 characters, includes location
- [ ] Meta description 150–160 chars, includes keyword + location + CTA
- [ ] Keywords are location-specific (8–12 terms)
- [ ] Open Graph tags complete and accurate
- [ ] Twitter Card tags complete and accurate
- [ ] Canonical URL set to the page's absolute URL
- [ ] `BreadcrumbList` JSON-LD (sub-pages only)
- [ ] Page-appropriate JSON-LD schema (FAQPage, JobPosting, etc.)
- [ ] Heading hierarchy correct (h1→h2→h3→h4, no skips)
- [ ] All `<section>` tags have `aria-label`
- [ ] `llms.txt` updated to reflect any content changes
