# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a personal academic website built with **Jekyll** using the [Academic Pages](https://academicpages.github.io/) template (forked from Minimal Mistakes theme). It generates a static site hosted on GitHub Pages.

## Development Commands

### Local Development

```bash
# Install dependencies (first time setup)
bundle install

# Start local server with live rebuild
jekyll serve -l -H localhost

# Alternative using bundle exec
bundle exec jekyll serve -l -H localhost
```

Site available at `http://localhost:4000`. Changes to `.md` and `.html` files rebuild automatically. Changes to `_config.yml` require restarting the server.

### Using Docker

```bash
chmod -R 777 .
docker compose up
```

Site available at `http://localhost:4000`.

## Content Management

### Key Files

| File | Purpose |
|------|---------|
| `_config.yml` | Site-wide settings (title, author info, social links) |
| `_data/navigation.yml` | Navigation menu configuration |
| `_pages/about.md` | Homepage content (permalink: `/`) |
| `_publications/` | Academic papers (add `.md` files here) |
| `_posts/` | Blog posts (dated markdown files) |
| `_talks/` | Academic presentations |
| `_teaching/` | Teaching experience |
| `_data/cv.json` | CV data in JSON format |

### Adding Publications

Create a new `.md` file in `_publications/` with front matter:

```yaml
---
title: "Paper Title"
collection: publications
type: "Conference"
permalink: /publication/2024-paper-key
date: 2024-10-17
venue: "Conference Name"
citation: "Your Name, Co-author. (2024). Paper Title..."
---
```

### Navigation Menu

Edit `_data/navigation.yml` to show/hide pages in the header. Comment out entries to hide them.

## Architecture

- **Collections**: Publications, talks, teaching, and portfolio are Jekyll collections defined in `_config.yml` with `output: true`
- **Layouts**: Page layouts in `_layouts/` - `single.html` for most pages, `talk.html` for talks
- **Components**: Reusable HTML fragments in `_includes/` (header, footer, author profile, etc.)
- **Static Assets**: CSS in `assets/css/`, JS in `assets/js/`, images in `images/`
- **Build Output**: Generated site in `_site/` (not committed to git)

## GitHub Pages Deployment

Push to `master` branch triggers automatic deployment via GitHub Actions. Check `.github/workflows/` for build configuration.
