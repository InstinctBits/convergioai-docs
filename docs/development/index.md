---
title: Development
description: Contributing to Convergio AI — setup, guidelines, and design system.
---

# Development

<div class="grid cards" markdown>

-   :material-source-pull:{ .lg .middle } **Contributing**

    ---

    Development workflow, coding standards, and PR guidelines.

    [:octicons-arrow-right-24: Contributing](contributing.md)

-   :material-palette-outline:{ .lg .middle } **Design System**

    ---

    Color palette, typography, components, and theming.

    [:octicons-arrow-right-24: Design system](design-system.md)

</div>

## Available scripts

```bash
npm run dev          # Frontend dev server (Vite, port 5173)
npm run server       # Backend API (Express, port 3001)
npm run dev:all      # Both concurrently
npm run build        # Production build
npm run preview      # Preview production build
npm run lint         # ESLint
npm run db:init      # Initialize database schemas
npm run db:migrate   # Run migrations
npm run db:seed      # Seed sample data
```
