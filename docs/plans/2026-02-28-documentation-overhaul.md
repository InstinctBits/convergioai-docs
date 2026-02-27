# Documentation Overhaul Implementation Plan

> **For Claude:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task.

**Goal:** Rebrand convergioai-docs with Digitech Nomads orange theme, restructure navigation n8n-style, and polish all content pages.

**Architecture:** Three incremental phases — each phase is committed and deployed independently. Phase 1 changes CSS/config only. Phase 2 moves files and rewrites `mkdocs.yml` nav. Phase 3 edits markdown content in-place.

**Tech Stack:** MkDocs + Material for MkDocs, CSS custom properties, Mermaid diagrams, GitHub Pages auto-deploy.

---

## Phase 1: Theme & Branding

### Task 1.1: Update CSS color variables

**Files:**
- Modify: `docs/assets/stylesheets/extra.css`

**Step 1: Replace light mode color variables**

Replace the `:root` block in `extra.css` with:

```css
:root {
  --md-primary-fg-color: #f15a24;
  --md-primary-fg-color--light: #ff7043;
  --md-primary-fg-color--dark: #d14d1e;
  --md-accent-fg-color: #f15a24;
  --md-typeset-a-color: #f15a24;
}
```

**Step 2: Replace dark mode color variables**

Replace the `[data-md-color-scheme="slate"]` block with:

```css
[data-md-color-scheme="slate"] {
  --md-primary-fg-color: #f15a24;
  --md-primary-fg-color--light: #ff7043;
  --md-primary-fg-color--dark: #d14d1e;
  --md-accent-fg-color: #ff7043;
  --md-typeset-a-color: #ff7043;
  --md-default-bg-color: #111111;
  --md-default-bg-color--light: #1a1a1a;
}
```

**Step 3: Update grid card hover border to orange**

In the `.md-typeset .grid.cards > ul > li:hover` rule, `border-color` already references `--md-accent-fg-color` which now resolves to orange. No change needed — verify visually.

**Step 4: Update announcement bar styling**

Replace the `.md-banner` block with:

```css
.md-banner {
  background-color: #f15a24;
  color: white;
}

.md-banner a {
  color: white;
  text-decoration: underline;
}
```

**Step 5: Add Manrope import and heading overrides**

Add at the TOP of `extra.css`, before `:root`:

```css
@import url('https://fonts.googleapis.com/css2?family=Manrope:wght@400;500;600;700;800&display=swap');
```

Update heading rules:

```css
.md-typeset h1 {
  font-family: 'Manrope', var(--md-text-font-family);
  font-size: 2em;
  font-weight: 800;
  letter-spacing: -0.02em;
}

.md-typeset h2 {
  font-family: 'Manrope', var(--md-text-font-family);
  font-size: 1.5em;
  font-weight: 700;
  letter-spacing: -0.01em;
}

.md-typeset h3 {
  font-family: 'Manrope', var(--md-text-font-family);
  font-size: 1.25em;
  font-weight: 600;
}
```

**Step 6: Verify build**

Run: `mkdocs build`
Expected: Build succeeds with no errors.

### Task 1.2: Update mkdocs.yml theme config

**Files:**
- Modify: `mkdocs.yml`

**Step 1: Change palette to custom**

Replace the `palette:` section (lines 43-56) with:

```yaml
  palette:
    - media: "(prefers-color-scheme: light)"
      scheme: default
      primary: custom
      accent: custom
      toggle:
        icon: material/brightness-7
        name: Switch to dark mode
    - media: "(prefers-color-scheme: dark)"
      scheme: slate
      primary: custom
      accent: custom
      toggle:
        icon: material/brightness-4
        name: Switch to light mode
```

**Step 2: Verify build**

Run: `mkdocs build`
Expected: Build succeeds with no errors.

### Task 1.3: Update logo SVG

**Files:**
- Modify: `docs/assets/images/logo.svg`

**Step 1: Replace logo with orange-branded version**

Replace entire file content with:

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 48 48" fill="none">
  <rect width="48" height="48" rx="8" fill="#f15a24"/>
  <text x="50%" y="54%" dominant-baseline="middle" text-anchor="middle"
        font-family="Manrope, Inter, system-ui, sans-serif" font-weight="800"
        font-size="22" fill="white">C</text>
</svg>
```

### Task 1.4: Commit Phase 1

**Step 1: Stage and commit**

```bash
git add docs/assets/stylesheets/extra.css mkdocs.yml docs/assets/images/logo.svg
git commit -m "feat: rebrand to Digitech Nomads orange theme

- Replace indigo/blue palette with orange (#f15a24) primary
- Add Manrope font for headings
- Update logo SVG to orange
- Set Material theme to custom palette mode
- Update dark mode colors to match brand"
```

---

## Phase 2: Navigation Restructure

### Task 2.1: Create new directory structure

**Step 1: Create directories**

```bash
mkdir -p docs/using/getting-started
mkdir -p docs/using/core-concepts
mkdir -p docs/using/email-automation
mkdir -p docs/using/ai-copilot
mkdir -p docs/using/streamboost
mkdir -p docs/using/calendar
mkdir -p docs/using/tasks
mkdir -p docs/using/digital-audits
mkdir -p docs/using/best-practices
mkdir -p docs/hosting
```

### Task 2.2: Move Getting Started files

**Step 1: Move files**

```bash
cp docs/getting-started/index.md docs/using/getting-started/index.md
cp docs/getting-started/quickstart.md docs/using/getting-started/quickstart.md
cp docs/getting-started/installation.md docs/using/getting-started/installation.md
cp docs/getting-started/configuration.md docs/using/getting-started/configuration.md
```

**Step 2: Fix any relative links in moved files**

In each moved file, internal links like `quickstart.md` remain correct since they're in the same directory. Cross-section links to `../features/` or `../platform/` will need updating in Phase 3.

### Task 2.3: Move Platform → Core Concepts

**Step 1: Move files**

```bash
cp docs/platform/architecture.md docs/using/core-concepts/architecture.md
cp docs/platform/concepts.md docs/using/core-concepts/concepts.md
cp docs/platform/database.md docs/using/core-concepts/database.md
```

### Task 2.4: Move Features → Individual directories

**Step 1: Move each feature file to its own directory as overview.md**

```bash
cp docs/features/email-automation.md docs/using/email-automation/overview.md
cp docs/features/ai-copilot.md docs/using/ai-copilot/overview.md
cp docs/features/streamboost.md docs/using/streamboost/overview.md
cp docs/features/calendar.md docs/using/calendar/overview.md
cp docs/features/tasks.md docs/using/tasks/overview.md
cp docs/features/digital-audits.md docs/using/digital-audits/overview.md
```

### Task 2.5: Move Guides → Hosting & Best Practices

**Step 1: Move deployment guides**

```bash
cp docs/guides/deployment.md docs/hosting/deployment.md
cp docs/guides/self-hosting.md docs/hosting/self-hosting.md
cp docs/guides/best-practices.md docs/using/best-practices/best-practices.md
```

### Task 2.6: Move Changelog → Development

**Step 1: Move changelog**

```bash
cp docs/changelog.md docs/development/changelog.md
```

### Task 2.7: Create new section index pages

**Files:**
- Create: `docs/using/index.md`
- Create: `docs/hosting/index.md`

**Step 1: Create Using Convergio AI index**

Write `docs/using/index.md`:

```markdown
---
title: Using Convergio AI
description: Learn how to use Convergio AI — from first setup to advanced features.
---

# Using Convergio AI

Everything you need to get started and make the most of Convergio AI.

## Learning path

<div class="grid cards" markdown>

-   :material-lightning-bolt:{ .lg .middle } **Getting Started**

    ---

    Install, configure, and launch your first instance.

    [:octicons-arrow-right-24: Quickstart](getting-started/quickstart.md)

-   :material-lightbulb-outline:{ .lg .middle } **Core Concepts**

    ---

    Understand the platform architecture, domain model, and database.

    [:octicons-arrow-right-24: Core concepts](core-concepts/concepts.md)

-   :material-email-fast-outline:{ .lg .middle } **Email Automation**

    ---

    AI-powered email management with auto-replies and smart categorization.

    [:octicons-arrow-right-24: Email automation](email-automation/overview.md)

-   :material-robot-outline:{ .lg .middle } **AI Copilot**

    ---

    Natural language interface for email summaries, lead tracking, and tasks.

    [:octicons-arrow-right-24: AI Copilot](ai-copilot/overview.md)

-   :material-broadcast:{ .lg .middle } **StreamBoost**

    ---

    YouTube live detection with cross-platform announcements.

    [:octicons-arrow-right-24: StreamBoost](streamboost/overview.md)

-   :material-calendar-clock:{ .lg .middle } **Calendar & Scheduling**

    ---

    Full calendar with Cal.com integration and meeting detection.

    [:octicons-arrow-right-24: Calendar](calendar/overview.md)

-   :material-checkbox-marked-outline:{ .lg .middle } **Task Management**

    ---

    Convert emails to tasks with priorities, filters, and tracking.

    [:octicons-arrow-right-24: Tasks](tasks/overview.md)

-   :material-shield-search:{ .lg .middle } **Digital Audits**

    ---

    AI-powered website and security audit workflows.

    [:octicons-arrow-right-24: Digital audits](digital-audits/overview.md)

-   :material-check-decagram:{ .lg .middle } **Best Practices**

    ---

    Production patterns for reliability, security, and performance.

    [:octicons-arrow-right-24: Best practices](best-practices/best-practices.md)

</div>
```

**Step 2: Create Hosting & Deployment index**

Write `docs/hosting/index.md`:

```markdown
---
title: Hosting & Deployment
description: Deploy and host Convergio AI in production environments.
---

# Hosting & Deployment

Guides for deploying Convergio AI to production.

<div class="grid cards" markdown>

-   :material-cloud-upload:{ .lg .middle } **Deployment**

    ---

    Deploy to production with Docker, PM2, or cloud platforms.

    [:octicons-arrow-right-24: Deployment guide](deployment.md)

-   :material-server:{ .lg .middle } **Self-Hosting**

    ---

    Run Convergio AI on your own infrastructure.

    [:octicons-arrow-right-24: Self-hosting guide](self-hosting.md)

</div>
```

### Task 2.8: Update mkdocs.yml navigation

**Files:**
- Modify: `mkdocs.yml`

**Step 1: Replace the entire `nav:` section (lines 211-266) with:**

```yaml
nav:
  - Home:
      - index.md

  - Using Convergio AI:
      - using/index.md
      - Getting Started:
          - using/getting-started/index.md
          - Quickstart: using/getting-started/quickstart.md
          - Installation: using/getting-started/installation.md
          - Configuration: using/getting-started/configuration.md
      - Core Concepts:
          - Architecture: using/core-concepts/architecture.md
          - Concepts: using/core-concepts/concepts.md
          - Database Schema: using/core-concepts/database.md
      - Email Automation: using/email-automation/overview.md
      - AI Copilot: using/ai-copilot/overview.md
      - StreamBoost: using/streamboost/overview.md
      - Calendar & Scheduling: using/calendar/overview.md
      - Task Management: using/tasks/overview.md
      - Digital Audits: using/digital-audits/overview.md
      - Best Practices: using/best-practices/best-practices.md

  - Integrations:
      - integrations/index.md
      - n8n Workflows: integrations/n8n.md
      - Cal.com: integrations/calcom.md
      - Platform Connections: integrations/platforms.md

  - API Reference:
      - api/index.md
      - Authentication: api/authentication.md
      - Emails: api/emails.md
      - Tasks: api/tasks.md
      - AI: api/ai.md
      - Calendar: api/calendar.md
      - Settings: api/settings.md
      - StreamBoost: api/streamboost.md
      - Error Handling: api/errors.md

  - Hosting & Deployment:
      - hosting/index.md
      - Deployment: hosting/deployment.md
      - Self-Hosting: hosting/self-hosting.md

  - Development:
      - development/index.md
      - Contributing: development/contributing.md
      - Design System: development/design-system.md
      - Changelog: development/changelog.md
```

### Task 2.9: Remove old directories

**Step 1: Remove old source directories after verifying build**

Run: `mkdocs build`
Expected: Build succeeds with no errors.

Then remove old directories:

```bash
rm -rf docs/getting-started
rm -rf docs/platform
rm -rf docs/features
rm -rf docs/guides
rm docs/changelog.md
```

**Step 2: Verify build again**

Run: `mkdocs build`
Expected: Build succeeds with no errors.

### Task 2.10: Commit Phase 2

```bash
git add -A
git commit -m "feat: restructure navigation to n8n-style task-oriented layout

- Merge Getting Started, Features, Platform, Guides into 'Using Convergio AI'
- Each feature gets its own subdirectory
- Add 'Hosting & Deployment' as standalone section
- Move Changelog under Development
- Create new section index pages with grid cards
- Reduce from 8 tabs to 6 tabs"
```

---

## Phase 3: Content Polish

### Task 3.1: Update landing page for new structure

**Files:**
- Modify: `docs/index.md`

**Step 1: Update grid cards to point to new paths**

Replace the grid cards section. Update all links:
- `getting-started/quickstart.md` → `using/getting-started/quickstart.md`
- `features/index.md` → `using/index.md`
- `api/index.md` → stays same
- `platform/architecture.md` → `using/core-concepts/architecture.md`
- `integrations/index.md` → stays same
- `development/index.md` → stays same

**Step 2: Add a "Start here" learning path section after the grid cards**

Add after the grid cards `</div>`:

```markdown

## Start here

New to Convergio AI? Follow this path:

1. **[Quickstart](using/getting-started/quickstart.md)** — Get a running instance in 10 minutes
2. **[Core Concepts](using/core-concepts/concepts.md)** — Understand the domain model
3. **[Email Automation](using/email-automation/overview.md)** — Set up your first AI-powered inbox
4. **[Best Practices](using/best-practices/best-practices.md)** — Production-ready patterns
```

**Step 3: Update "Key capabilities" table links**

Each row in the capabilities table should link to the new feature paths.

### Task 3.2: Add admonitions and cross-links to Getting Started pages

**Files:**
- Modify: `docs/using/getting-started/quickstart.md`
- Modify: `docs/using/getting-started/installation.md`
- Modify: `docs/using/getting-started/configuration.md`

**Step 1: Add prerequisite admonition to quickstart.md**

Add after the frontmatter and title:

```markdown
!!! info "Prerequisites"
    Make sure you have Node.js 20+, PostgreSQL 15+, and npm 9+ installed.
    See [Installation](installation.md) for detailed setup instructions.
```

**Step 2: Add "Next steps" to each page**

At the bottom of each Getting Started page, add:

```markdown
## Next steps

- [Core Concepts](../core-concepts/concepts.md) — Understand the domain model
- [Email Automation](../email-automation/overview.md) — Set up AI-powered email
- [Configuration](configuration.md) — Fine-tune environment variables
```

(Adjust links per page — don't link a page to itself.)

### Task 3.3: Add admonitions and cross-links to Core Concepts pages

**Files:**
- Modify: `docs/using/core-concepts/architecture.md`
- Modify: `docs/using/core-concepts/concepts.md`
- Modify: `docs/using/core-concepts/database.md`

**Step 1: Add cross-links at bottom of each page**

Example for `architecture.md`:

```markdown
## Related pages

- [Core Concepts](concepts.md) — Domain model and key abstractions
- [Database Schema](database.md) — PostgreSQL tables and relationships
- [API Reference](../../api/index.md) — REST API endpoints
```

### Task 3.4: Polish feature pages

**Files:**
- Modify: all `docs/using/<feature>/overview.md` files (6 files)

**Step 1: Ensure consistent frontmatter on each feature page**

Each feature page should have:

```yaml
---
title: <Feature Name>
description: <One-line description>
---
```

**Step 2: Add "Related pages" section at bottom of each feature page**

Link to related features, API endpoints, and integrations.

Example for email-automation:

```markdown
## Related pages

- [AI Copilot](../ai-copilot/overview.md) — Chat interface for email summaries
- [Email API](../../api/emails.md) — REST endpoints for email operations
- [n8n Workflows](../../integrations/n8n.md) — Automated email pipelines
- [Configuration](../getting-started/configuration.md) — IMAP/SMTP settings
```

**Step 3: Add tip admonitions where useful**

Example for email-automation:

```markdown
!!! tip "Quick setup"
    The fastest way to get email automation running is to configure your
    IMAP credentials in `.env` and enable auto-reply in the settings panel.
```

### Task 3.5: Update Development section with changelog

**Files:**
- Modify: `docs/development/index.md`

**Step 1: Add changelog card to the grid**

Add a third card to the grid:

```markdown
-   :material-history:{ .lg .middle } **Changelog**

    ---

    Release history and version notes.

    [:octicons-arrow-right-24: Changelog](changelog.md)
```

### Task 3.6: Verify full build and commit Phase 3

**Step 1: Build and check**

Run: `mkdocs build`
Expected: Build succeeds with no errors or broken links.

**Step 2: Commit**

```bash
git add -A
git commit -m "feat: polish content with admonitions, cross-links, and learning path

- Update landing page grid cards for new navigation paths
- Add 'Start here' learning path to homepage
- Add prerequisite admonitions to Getting Started pages
- Add 'Next steps' and 'Related pages' sections across all pages
- Ensure consistent frontmatter on all feature pages
- Add changelog card to Development section"
```

---

## Verification

After all 3 phases:

1. Run `mkdocs serve` and verify:
   - Orange branding visible in header, links, and hover states
   - Manrope headings render correctly
   - Dark mode toggle works with correct dark colors
   - All 6 navigation tabs appear and link correctly
   - All grid cards on index pages link to correct pages
   - No broken internal links
   - Admonitions render with correct styling

2. Push to main and verify GitHub Actions deploys successfully to docs.instinctbits.com
