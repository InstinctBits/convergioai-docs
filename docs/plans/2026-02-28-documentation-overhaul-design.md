# Documentation Overhaul Design

**Date:** 2026-02-28
**Approach:** Incremental (3 phases, each independently deployable)

## Context

Update convergioai-docs with:
1. Digitech Nomads branding (from digitechnomads.com)
2. n8n-inspired documentation structure (from docs.n8n.io)
3. Content polish on existing pages

## Phase 1: Theme & Branding

### Color Palette

| Token | Light Mode | Dark Mode |
|-------|-----------|-----------|
| Primary | `#f15a24` (Digitech Nomads orange) | `#f15a24` |
| Primary dark | `#d14d1e` | `#d14d1e` |
| Primary light | `#ff7043` | `#ff7043` |
| Accent | `#f15a24` | `#ff7043` |
| Background | `#ffffff` / `#f9fafb` | `#111111` / `#1a1a1a` |
| Text | `#333333` | `#e5e5e5` |

### Typography

- Headings: **Manrope** (matches digitechnomads.com)
- Body: **Inter** (readability for docs)
- Code: **JetBrains Mono** (keep current)

### Changes Required

- `extra.css`: Replace indigo/blue variables with orange palette
- `mkdocs.yml`: Set `primary: custom`, `accent: custom`, add Manrope font
- `logo.svg`: Update colors to orange tones
- `overrides/main.html`: Orange announcement bar
- Grid cards: Orange hover border
- Status badges: Keep green/red

## Phase 2: Navigation Restructure

### Current → Proposed

```
CURRENT (8 tabs):
Home | Getting Started | Features | Platform | API Reference | Integrations | Guides | Development | Changelog

PROPOSED (6 tabs):
Home | Using Convergio AI | Integrations | API Reference | Hosting & Deployment | Development
```

### Detailed Navigation Tree

```
Home
  └── index.md

Using Convergio AI
  ├── index.md (section overview + learning path)
  ├── Getting Started/
  │   ├── quickstart.md
  │   ├── installation.md
  │   └── configuration.md
  ├── Core Concepts/
  │   ├── architecture.md
  │   ├── concepts.md
  │   └── database.md
  ├── Email Automation/
  │   └── overview.md
  ├── AI Copilot/
  │   └── overview.md
  ├── StreamBoost/
  │   └── overview.md
  ├── Calendar/
  │   └── overview.md
  ├── Tasks/
  │   └── overview.md
  ├── Digital Audits/
  │   └── overview.md
  └── Best Practices/
      └── best-practices.md

Integrations
  ├── index.md
  ├── n8n.md
  ├── calcom.md
  └── platforms.md

API Reference
  ├── index.md
  ├── authentication.md
  ├── emails.md
  ├── tasks.md
  ├── ai.md
  ├── calendar.md
  ├── settings.md
  ├── streamboost.md
  └── errors.md

Hosting & Deployment
  ├── index.md
  ├── deployment.md
  └── self-hosting.md

Development
  ├── index.md
  ├── contributing.md
  ├── design-system.md
  └── changelog.md
```

### File Moves

- `docs/platform/*.md` → `docs/using/core-concepts/`
- `docs/features/*.md` → `docs/using/<feature>/overview.md`
- `docs/getting-started/*.md` → `docs/using/getting-started/`
- `docs/guides/best-practices.md` → `docs/using/best-practices/`
- `docs/guides/deployment.md` → `docs/hosting/deployment.md`
- `docs/guides/self-hosting.md` → `docs/hosting/self-hosting.md`
- `docs/changelog.md` → `docs/development/changelog.md`

## Phase 3: Content Polish

For each page:
1. Better introductions (1-2 sentences, audience + purpose)
2. Admonitions (`!!! tip`, `!!! warning`, `!!! info`)
3. Cross-linking ("Related pages" / "Next steps" at bottom)
4. Consistent frontmatter (`title`, `description`, `icon`)
5. Feature pages: Add Mermaid diagrams, config tables, "Common issues"
6. Landing page: Update grid cards for new nav, add learning path

### Out of Scope

- New pages for features that don't exist
- Video tutorials or interactive content
- Full API endpoint rewrite
