# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Official documentation repository for Convergio AI — architecture, APIs, setup guides, and developer reference. Built with Material for MkDocs. Owned by Instinct Bits, MIT licensed.

## Brand Hierarchy

- **Organization:** Digitech Nomads
- **Project:** Convergio AI
- **Produced by:** Instinct Bits Lab
- **Documentation domain:** https://docs.instinctbits.com

## Tech Stack

- **Framework:** MkDocs with Material for MkDocs theme
- **Language:** Python (documentation toolchain)
- **Deployment:** GitHub Actions → GitHub Pages (`gh-pages` branch)
- **Versioning:** mike (future)
- **Domain:** docs.instinctbits.com (custom CNAME)

## Common Commands

```bash
# Install dependencies
pip install -r requirements.txt

# Local development server with live reload
mkdocs serve

# Production build
mkdocs build

# Deploy (handled by GitHub Actions, rarely needed locally)
mkdocs gh-deploy --force
```

## Repository Structure

```
convergioai-docs/
├── .github/workflows/deploy.yml   # Auto-deploy on push to main
├── docs/                          # All documentation content
│   ├── index.md                   # Landing page
│   ├── getting-started/           # Setup, quickstart, configuration
│   ├── platform/                  # Architecture, core concepts
│   ├── api/                       # API reference
│   ├── guides/                    # Deployment, best practices
│   ├── sdks/                      # SDK documentation
│   ├── changelog.md               # Release history
│   └── assets/                    # Images, CSS, JS
├── overrides/                     # Material theme template overrides
│   └── main.html                  # Announcement bar
├── mkdocs.yml                     # Main MkDocs configuration
├── requirements.txt               # Python dependencies
├── CNAME                          # Custom domain for GitHub Pages
└── README.md                      # Project README
```

## Key Files

- `mkdocs.yml` — Central configuration. All navigation, theme features, plugins, and extensions.
- `docs/assets/stylesheets/extra.css` — Brand color overrides and custom styling.
- `overrides/main.html` — Announcement bar and theme template customizations.
- `.github/workflows/deploy.yml` — CI/CD pipeline.

## Conventions

- All documentation pages must have YAML frontmatter with `title` and `description`.
- Use Material admonitions (`!!! info`, `!!! warning`, etc.) for callouts.
- Use content tabs (`=== "Tab"`) for multi-language code examples.
- Use Mermaid for diagrams (fenced code blocks with `mermaid` language).
- Section index pages use `index.md` within their directory.
- Navigation structure is defined explicitly in `mkdocs.yml` `nav:` section.

## Git

- **Remote:** https://github.com/InstinctBits/convergioai-docs.git
- **Default branch:** main
- **Deploy branch:** gh-pages (auto-managed by `mkdocs gh-deploy`)
