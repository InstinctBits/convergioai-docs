---
title: Convergio AI Documentation
description: Official documentation for Convergio AI — a unified omnichannel CRM platform with AI-powered email automation, stream management, and intelligent workflows.
---

# Convergio AI

**Unified Omnichannel CRM with AI-Powered Automation**

Convergio AI is a modern, open-source platform that brings together email management, AI-powered automation, stream broadcasting, calendar scheduling, free tools, and workflow orchestration — all in one intelligent dashboard. Built with React 19, Express 5, and PostgreSQL, powered by Claude AI with built-in automation.

<div class="grid cards" markdown>

-   :material-rocket-launch-outline:{ .lg .middle } **Getting Started**

    ---

    Install, configure, and run your first instance in minutes.

    [:octicons-arrow-right-24: Quickstart](using/getting-started/quickstart.md)

-   :material-robot-outline:{ .lg .middle } **Boost Suite**

    ---

    CommBoost, WorkBoost, StreamBoost, Free Tools, Calendar, Digital Audits, and more.

    [:octicons-arrow-right-24: Explore features](using/index.md)

-   :material-api:{ .lg .middle } **API Reference**

    ---

    Complete REST API reference with 67+ endpoints for emails, AI, tasks, and streams.

    [:octicons-arrow-right-24: API docs](api/index.md)

-   :material-sitemap-outline:{ .lg .middle } **Architecture**

    ---

    System design, database schema, and technology stack overview.

    [:octicons-arrow-right-24: Platform overview](using/core-concepts/architecture.md)

-   :material-connection:{ .lg .middle } **Integrations**

    ---

    Cal.com scheduling, n8n advanced workflows, and multi-platform posting.

    [:octicons-arrow-right-24: View integrations](integrations/index.md)

-   :material-code-braces:{ .lg .middle } **Development**

    ---

    Contributing guide, design system, and development setup.

    [:octicons-arrow-right-24: Start contributing](development/index.md)

</div>

## Start here

New to Convergio AI? Follow this path:

1. **[Quickstart](using/getting-started/quickstart.md)** — Get a running instance in 10 minutes
2. **[Core Concepts](using/core-concepts/concepts.md)** — Understand the Boost Suite and domain model
3. **[CommBoost](using/email-automation/overview.md)** — Set up your first AI-powered inbox
4. **[Free Tools](using/free-tools/overview.md)** — Try the AI Prompt Generator
5. **[Best Practices](using/best-practices/best-practices.md)** — Production-ready patterns

## Key capabilities

| Capability | Description |
| ---------- | ----------- |
| **[CommBoost — Email](using/email-automation/overview.md)** | Multi-inbox AI email management with built-in auto-replies, threading, and smart categorization |
| **[WorkBoost — Tasks](using/tasks/overview.md)** | Kanban board with source tracking, priorities, and email-to-task conversion |
| **[StreamBoost](using/streamboost/overview.md)** | YouTube live detection with milestones, story cards, and cross-platform announcements |
| **[AI Copilot](using/ai-copilot/overview.md)** | Multi-model chat interface (Claude, Gemini, Qwen) for email summaries and operational insights |
| **[Calendar](using/calendar/overview.md)** | Multi-view calendar with Cal.com integration and AI meeting detection |
| **[Digital Audits](using/digital-audits/overview.md)** | AI-powered website security and performance audits |
| **[Free Tools](using/free-tools/overview.md)** | AI Prompt Generator with multiple framework templates |

## Tech stack

=== "Frontend"

    - **React 19.2** with TypeScript 5.9
    - **Vite 7.2** build tooling
    - **Tabler Design System** with dark/light mode
    - **Recharts 3.7** for analytics visualization
    - **TipTap 3.20** rich text editor

=== "Backend"

    - **Express 5.2** (Node.js 22+)
    - **PostgreSQL 15+** with `pg` driver
    - **Better Auth 1.5** — cookie-based session authentication
    - **Swagger/OpenAPI** documentation
    - **Sharp** for image processing

=== "AI & Automation"

    - **Anthropic Claude** for AI responses
    - **Google Gemini** and **Qwen** as alternative models
    - **Built-in email auto-responder** (cron-based, no external dependencies)
    - **n8n** for advanced workflows (StreamBoost dispatching)
    - **IMAPFlow** for email synchronization
    - **Cal.com** for scheduling

---

<div style="text-align: center; margin-top: 2rem; color: var(--md-default-fg-color--lighter); font-size: 0.8rem;" markdown>
Ignited at [Instinct Bits Lab](https://instinctbits.com){ target="_blank" } | Supercharged by [Digitech Nomads](https://digitechnomads.com){ target="_blank" }
</div>
