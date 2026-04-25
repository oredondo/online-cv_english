# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Running locally

```bash
docker-compose up
```

Opens at `http://localhost:4000`. Live reload is enabled — changes to `_data/*.yml` are picked up automatically after a short delay.

Without Docker:

```bash
bundle install
bundle exec jekyll serve
```

## Architecture

This is a Jekyll static site with two pages:

- **`/`** (`index.html`) — the CV, rendered with the `default` layout
- **`/cover-letter`** (`cover-letter.html`) — rendered with the `letter` layout

### Where content lives

All CV content is in `_data/data.yml`. This is the only file that needs editing for content changes. It contains: sidebar info, tagline, career profile (both `summary` and `summary_short` variants), experiences, projects, skills, certifications, and education.

Cover letter content is in `_data/cover-letter.yml`.

### How sections render

Each section of the CV (`career-profile`, `experiences`, `projects`, `skills`, etc.) has a corresponding partial in `_includes/`. The `index.html` page includes them in order. Each partial reads from `site.data.data.*`.

Most sections have two text variants in `data.yml`:
- Full version (e.g. `details`, `tagline`) — used in the default web view
- Short version (e.g. `details_short`, `tagline_short`) — used in the print layout (`print.html`)

### Layouts

- `default.html` — sidebar + main content, includes a print-to-PDF button
- `letter.html` — standalone layout for the cover letter
- `print.html` — condensed layout using `_short` text variants

### Styling

Theme skin is set in `_config.yml` (`theme_skin: blue`). Options: `blue turquoise green berry orange ceramic`. Changing the skin requires restarting the Jekyll server.

SCSS lives in `_sass/`.
