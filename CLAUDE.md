# CLAUDE.md

This file provides comprehensive guidance to Claude Code (claude.ai/code) when working with this Jekyll-based academic website repository.

## Project Overview

This is a personal academic website built with **Jekyll** using the [Academic Pages](https://academicpages.github.io/) template, which is a fork of the Minimal Mistakes theme. The site generates a static academic portfolio hosted on GitHub Pages and features:

- Publication management with detailed citation handling
- CV generation (both Markdown and JSON formats)
- Teaching experience showcase
- Academic talks and presentations
- Blog post capability
- Responsive design with customizable themes
- Social media and academic profile integration

## Development Environment Setup

### Local Development (Ruby)

```bash
# Install dependencies (first time setup)
bundle install

# Start local server with live rebuild
jekyll serve -l -H localhost

# Alternative using bundle exec
bundle exec jekyll serve -l -H localhost
```

Site available at `http://localhost:4000`. Changes to `.md` and `.html` files rebuild automatically. Changes to `_config.yml` require restarting the server.

### Docker Development

```bash
chmod -R 777 .
docker compose up
```

Site available at `http://localhost:4000`.

## Project Architecture

### Directory Structure

```
├── _config.yml              # Main site configuration
├── _data/                   # Site data files
│   ├── navigation.yml       # Header navigation menu
│   ├── cv.json             # CV data in JSON format
│   └── ui-text.yml         # UI text localization
├── _includes/              # Reusable HTML components
│   ├── author-profile.html # Sidebar author profile
│   ├── head.html          # HTML head section
│   ├── footer.html        # Site footer
│   └── masthead.html      # Site header/navigation
├── _layouts/               # Page templates
│   ├── default.html       # Base layout
│   ├── single.html        # Single page layout
│   └── talk.html          # Talk-specific layout
├── _pages/                 # Static pages
│   ├── about.md           # Homepage (permalink: /)
│   ├── cv.md              # CV page
│   ├── publications.html  # Publications listing
│   └── teaching.html      # Teaching experience
├── _publications/          # Publication markdown files
├── _teaching/             # Teaching experience files
├── _talks/                # Academic talks/presentations
├── _posts/                # Blog posts
├── _sass/                 # Sass stylesheets
├── assets/                # Static assets (CSS, JS, images)
├── files/                 # Downloadable files (PDFs, etc.)
├── images/               # Site images and icons
└── _site/                # Generated site (auto-generated, not committed)
```

### Jekyll Collections

The site uses Jekyll collections for content organization:

- **Publications**: Research papers and articles (`_publications/`)
- **Teaching**: Teaching experience and courses (`_teaching/`)
- **Talks**: Academic presentations and seminars (`_talks/`)
- **Portfolio**: Project showcases (`_portfolio/`)
- **Posts**: Blog posts (`_posts/`)

All collections are configured in `_config.yml` with `output: true` for individual page generation.

## Content Management

### Site Configuration (`_config.yml`)

**Basic Settings** (Lines 10-19):
- `title`: Site title and page header
- `name`: Author's name used throughout site
- `description`: Site meta description
- `url`: Base site URL for GitHub Pages
- `repository`: GitHub repository name

**Author Profile** (Lines 24-81):
- `author.avatar`: Profile image filename (place in `/images/`)
- `author.bio`: Short bio description for sidebar
- `author.location`: Geographic location
- `author.email`: Contact email
- Academic profiles: Google Scholar, ORCID, ResearchGate, etc.
- Social media links: GitHub, LinkedIn, Twitter, etc.

**Collections Configuration** (Lines 223-235):
Defines content collections with permalink structures.

### Navigation Menu (`_data/navigation.yml`)

Controls header navigation links:
```yaml
main:
  - title: "Publications"
    url: /publications/
  - title: "Teaching"  
    url: /teaching/
  # Comment out to hide from menu
  # - title: "Talks"
  #   url: /talks/
```

### Homepage Content (`_pages/about.md`)

The main landing page with:
- Permalink: `/` (homepage)
- Author profile sidebar
- Main content area for introduction/bio
- Automatic redirects from `/about/` and `/about.html`

### Publications Management

#### Adding New Publications

Create `.md` files in `_publications/` with comprehensive front matter:

```yaml
---
title: "Full Paper Title"
collection: publications
category: manuscripts  # or conferences, books, preprints
permalink: /publication/2024-paper-key
date: 2024-10-17
venue: 'Journal/Conference Name'
paperurl: 'https://doi.org/...'
repourl: 'https://github.com/username/repo'
citation: 'Author, A. et al. (2024). Paper Title. Journal Name.'
authors:
  - name: "First Author"
    equal_contribution: true
  - name: "Second Author"
    corresponding: true
---

Paper abstract and description content here.
```

#### Publication Features

- **Author Management**: Automatic highlighting of site owner, equal contribution markers (‡), corresponding author markers (*)
- **Multiple URLs**: Paper, slides, BibTeX, code repository links
- **Categories**: Organized by publication type (conferences, journals, preprints)
- **Citation Handling**: Automatic citation display and formatting

### Teaching Experience (`_teaching/`)

Add teaching roles with:
```yaml
---
title: "Course Title"
collection: teaching
type: "Teaching Assistant"
venue: "University Name"
date: 2024-09-01
location: "City, Country"
---
```

### Academic Talks (`_talks/`)

Presentation records with:
```yaml
---
title: "Talk Title"
collection: talks
type: "Conference Presentation"
venue: "Conference Name"
date: 2024-05-15
location: "City, Country"
---
```

## Customization and Theming

### Theme Selection
Set in `_config.yml`:
```yaml
site_theme: "default"  # Options: "default", "air"
```

### Styling (`_sass/` and `assets/css/`)
- Main styles: `assets/css/main.scss`
- Theme variations: `_sass/theme/`
- Layout styles: `_sass/layout/`
- Component styles: `_sass/include/`

### Assets Management
- **CSS**: Compiled from Sass files in `_sass/`
- **JavaScript**: Main JS in `assets/js/`
- **Images**: Store in `images/` directory
- **Files**: PDFs and downloads in `files/`

## Advanced Features

### CV Management

**Markdown CV** (`_pages/cv.md`):
- Standard markdown formatting
- Automatic layout with `cv-layout.html`

**JSON CV** (`_data/cv.json`):
- Structured data format
- Generated page at `/cv-json/`
- Convertible using `scripts/cv_markdown_to_json.py`

### Automated Tools

**Markdown Generators** (`markdown_generator/`):
- `publications.py`: Generate publication pages from TSV/CSV
- `talks.py`: Generate talk pages from data
- Jupyter notebooks for interactive generation

**Talk Map** (`talkmap.py`):
- Geographic visualization of presentations
- Leaflet.js integration for interactive maps

### SEO and Analytics

**SEO Configuration**:
- Meta descriptions and titles
- Open Graph tags for social sharing
- Schema.org structured data

**Analytics Setup**:
- Google Analytics integration
- Custom tracking provider support

## Deployment

### GitHub Pages
- **Branch**: Push to `master` branch for auto-deployment
- **Custom Domain**: Configure in repository settings
- **HTTPS**: Automatically enabled for GitHub Pages

### Build Process
1. GitHub Actions triggers on push to `master`
2. Jekyll builds site from source files
3. Generated `_site/` content deployed to GitHub Pages
4. Site accessible at `https://username.github.io`

### Local Testing
Always test locally before pushing:
```bash
bundle exec jekyll serve -l -H localhost
```

## Troubleshooting

### Common Issues
- **Gem Dependencies**: Run `bundle install` if missing gems
- **Config Changes**: Restart Jekyll server after `_config.yml` changes
- **Permalinks**: Ensure unique permalink values for all content
- **Images**: Use relative paths and place in `/images/` directory

### Build Errors
- Check Jekyll build logs in GitHub Actions
- Validate YAML front matter syntax
- Ensure all required fields are present

### Performance
- Optimize images for web
- Minimize custom CSS/JS
- Use Jekyll's built-in compression settings

## Security Considerations
- Never commit sensitive data or API keys
- Use environment variables for production settings
- Regularly update gem dependencies
- Review third-party plugins for security

# Important Instructions for Claude Code
- Always test changes locally before deployment
- Preserve existing content structure and formatting
- Follow Jekyll conventions for file organization
- Maintain responsive design principles
- Ensure accessibility compliance
- Validate all YAML front matter syntax
- Check for broken links and missing assets