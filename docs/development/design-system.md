---
title: Design System
description: Convergio AI design system — colors, typography, components, and theming.
---

# Design System

Convergio AI uses a Tabler-inspired design system with comprehensive dark/light mode support.

## Color palette

=== "Dark Mode"

    | Token | Value | Usage |
    | ----- | ----- | ----- |
    | Background | `#182433` | Page background |
    | Cards | `#1d2838` | Elevated surfaces |
    | Primary | `#f15b22` | Orange accent |
    | Success | `#2fb344` | Green indicators |
    | Warning | `#f59e0b` | Amber alerts |
    | Error | `#ef4444` | Red errors |

=== "Light Mode"

    | Token | Value | Usage |
    | ----- | ----- | ----- |
    | Background | `#ffffff` | Page background |
    | Cards | `#f8fafc` | Elevated surfaces |
    | Primary | `#ea580c` | Orange accent |
    | Success | `#16a34a` | Green indicators |

## Typography

| Property | Value |
| -------- | ----- |
| Font family | Inter (system fonts fallback) |
| Scale | 32px → 12px (6 levels) |
| Line height | 1.428 |
| Weights | 400, 500, 600, 700 |

## Component library

- **Stat Cards** — Metrics with sparklines and trend indicators
- **Icon Badges** — Status indicators with color coding
- **Data Tables** — Sortable, filterable tables
- **Modal Overlays** — Detail views and forms
- **Activity Feeds** — Timeline-style event lists
- **Tag System** — Color-coded email categorization

## Customization

All design tokens are defined as CSS custom properties in `src/styles/variables.css`. Override them for custom themes.
