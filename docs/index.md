---
title: Convergio AI Documentation
description: Official documentation for Convergio AI — a unified omnichannel CRM platform with AI-powered email automation, stream management, and intelligent workflows.
---

# Convergio AI

**Unified Omnichannel CRM with AI-Powered Automation**

Convergio AI is a modern, open-source platform that brings together email management, AI-powered automation, stream broadcasting, calendar scheduling, and workflow orchestration — all in one intelligent dashboard. Built with React, Express, and PostgreSQL, powered by Claude AI and n8n workflows.

<div class="grid cards" markdown>

-   :material-rocket-launch-outline:{ .lg .middle } **Getting Started**

    ---

    Install, configure, and run your first instance in minutes.

    [:octicons-arrow-right-24: Quickstart](using/getting-started/quickstart.md)

-   :material-robot-outline:{ .lg .middle } **Features**

    ---

    AI email automation, StreamBoost, calendar, task management, and more.

    [:octicons-arrow-right-24: Explore features](using/index.md)

-   :material-api:{ .lg .middle } **API Reference**

    ---

    Complete REST API reference with 80+ endpoints for emails, AI, tasks, and streams.

    [:octicons-arrow-right-24: API docs](api/index.md)

-   :material-sitemap-outline:{ .lg .middle } **Architecture**

    ---

    System design, database schema, and technology stack overview.

    [:octicons-arrow-right-24: Platform overview](using/core-concepts/architecture.md)

-   :material-connection:{ .lg .middle } **Integrations**

    ---

    n8n workflows, Cal.com scheduling, and multi-platform posting.

    [:octicons-arrow-right-24: View integrations](integrations/index.md)

-   :material-code-braces:{ .lg .middle } **Development**

    ---

    Contributing guide, design system, and development setup.

    [:octicons-arrow-right-24: Start contributing](development/index.md)

</div>

## Key capabilities

| Capability | Description |
| ---------- | ----------- |
| **AI Email Automation** | Claude AI-powered auto-replies, email intelligence, and smart categorization |
| **StreamBoost** | YouTube live stream detection with cross-platform announcements to Discord, X, Instagram, Facebook |
| **AI Operations Copilot** | Natural language chat interface for email summaries, lead tracking, and task management |
| **Calendar & Scheduling** | Full calendar with Cal.com integration, meeting detection from emails |
| **Task Management** | Convert emails to tasks with priorities, assignments, and due dates |
| **Digital Audits** | AI-powered security and digital audit workflows |
| **n8n Workflows** | Automated IMAP → AI → SMTP → Database pipelines with visual workflow builder |

## Tech stack

=== "Frontend"

    - **React 19** with TypeScript
    - **Vite 6** build tooling
    - **Tabler Design System** with dark/light mode
    - **Recharts** for analytics visualization
    - **TipTap** rich text editor

=== "Backend"

    - **Express 5** (Node.js 20+)
    - **PostgreSQL** with `pg` driver
    - **JWT** authentication with bcrypt
    - **Swagger/OpenAPI** documentation
    - **Sharp** for image processing

=== "AI & Automation"

    - **Anthropic Claude** for AI responses
    - **n8n** for workflow automation
    - **IMAPFlow** for email synchronization
    - **Cal.com** for scheduling

---

<div style="text-align: center; margin-top: 2rem; color: var(--md-default-fg-color--lighter); font-size: 0.8rem;" markdown>
A [Digitech Nomads](https://digitechnomads.com){ target="_blank" } project. Produced by [Instinct Bits Lab](https://instinctbits.com){ target="_blank" }.
</div>
