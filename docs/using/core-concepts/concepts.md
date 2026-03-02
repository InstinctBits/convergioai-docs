---
title: Core Concepts
description: Key abstractions and terminology used across the Convergio AI platform.
---

# Core Concepts

## Boost Suite

Convergio AI organizes its features into a **Boost Suite** — a collection of focused tools that each enhance a specific aspect of business operations:

| Boost | Route | Description | Status |
| ----- | ----- | ----------- | ------ |
| **CommBoost** | `/dashboard/commboost` | Multi-inbox email management with AI auto-replies | Active |
| **WorkBoost** | `/dashboard/workboost` | Kanban task management with source tracking | Active |
| **StreamBoost** | `/dashboard/streamboost` | YouTube live stream automation and cross-platform posting | Active |
| **Free Tools** | `/dashboard/free-tools` | AI Prompt Generator and utilities | Active |
| **ContentBoost** | `/dashboard/contentboost` | AI-powered content creation and publishing | Coming Soon |
| **IdeaBoost** | `/dashboard/ideaboost` | Idea capture, suggestions, and management | Coming Soon |
| **CampaignBoost** | `/dashboard/campaignboost` | Email campaigns and contact management | Coming Soon |

## Inboxes and tags

Convergio AI supports five email inboxes, each mapped to a **tag** derived from the recipient address. Tags determine:

- Which section of the dashboard displays the email
- Which AI knowledge base is used for auto-replies
- How tasks are categorized
- The color coding in the UI

| Inbox | Email | Color | Purpose |
| ----- | ----- | ----- | ------- |
| Hello | hello@digitechnomads.com | Blue | Sales inquiries |
| Partners | partners@digitechnomads.com | Purple | Partnership requests |
| Info | info@digitechnomads.com | Cyan | Press and media |
| Support | support@digitechnomads.com | Orange | Client support |
| Neo | neo@digitechnomads.com | Green | Special projects |

Each inbox has its own **knowledge base** — a set of markdown files that provide context to the AI when generating auto-replies. This ensures responses are accurate and inbox-appropriate.

## Email threading

CommBoost maintains proper email threading using RFC 2822 headers:

- **Message-ID** — Unique identifier for each email
- **In-Reply-To** — References the parent email
- **References** — Full chain of related message IDs

This enables the **conversation view** in the dashboard, where related emails are grouped into threads.

## Built-in auto-responder

The auto-responder is a cron service built directly into the server that runs every 3 minutes:

1. Fetches emails without replies from the database
2. Loads the inbox-specific knowledge base
3. Generates a contextual response using Claude AI
4. Sends the reply via SMTP with proper threading headers
5. Records the auto-reply in the database

Each inbox can be toggled independently — enable auto-responses for Support while keeping Hello manual.

!!! tip "No external dependencies"
    The auto-responder runs entirely within the Express server. No n8n, no external services — just your server, your database, and the AI API.

## AI models

Convergio AI supports multiple AI providers with runtime switching:

| Model | Provider | Best for |
| ----- | -------- | -------- |
| Claude | Anthropic | High-quality email replies, complex analysis |
| Gemini | Google | Fast responses, general-purpose tasks |
| Qwen | OpenRouter/Bytez | Cost-effective alternative |

Switch the active model at any time from the dashboard or via `POST /api/ai-model` — no restart required.

## Captions and approval flow

In StreamBoost, when a live stream is detected:

1. AI generates platform-specific **captions** (one per target platform)
2. Captions enter a **pending** state in the dashboard
3. User can **approve**, **edit**, or **skip** each caption
4. Approved captions are **dispatched** to the target platform (Discord, X, Instagram, Facebook)

Each platform has its own **channel voice** — a configurable tone, style, and hashtag template that shapes how captions are written.

## Milestones

StreamBoost tracks subscriber milestones with configurable thresholds (100, 500, 1K, 5K, 10K, 50K). When a milestone is reached:

- Automatic detection triggers a celebration
- **Story cards** and **milestone cards** can be generated as shareable graphics
- Announcement posts are dispatched to connected platforms

## Calendar events

Calendar events can originate from three sources:

| Source | How it works |
| ------ | ------------ |
| **Manual** | Created directly in the calendar UI |
| **Cal.com** | Synced from Cal.com bookings |
| **Email-detected** | AI detects meeting mentions in emails and suggests events |

Each event tracks status (confirmed, tentative, cancelled), attendees, meeting URL, and timezone.

## Digital audits

The audit system analyzes websites across multiple dimensions:

- **SEO score** — Search engine optimization quality
- **Performance** — Page load and Core Web Vitals
- **Social media presence** — Cross-platform activity
- **Brand consistency** — Visual and messaging coherence
- **Security posture** — SSL, headers, vulnerability indicators

Audit results include an executive summary and prioritized recommendations with impact/effort ratings.

## Authentication

Convergio AI uses **Better Auth** for session-based authentication:

- **Email/password** — Standard signup and login
- **Google OAuth** — Single sign-on via Google
- **Cookie-based sessions** — Secure, HTTP-only cookies (no JWT tokens)
- **Organizations** — Auto-created on signup, with member invitations and roles

!!! warning "v3.0 change"
    Previous versions used JWT tokens. v3.0 uses cookie-based sessions exclusively. All API requests must include the session cookie.

## Organizations

When a user signs up, an organization is automatically created with the user as owner. Organizations support:

- **Members** — Invite team members by email
- **Roles** — Owner, admin, and member permission levels
- **Data scoping** — All data is scoped to the user's organization

## API keys

Developers can generate API keys from the Settings page for programmatic access. Keys use a `cai_` prefix and are stored as hashes in the database.

## Related pages

- [Architecture](architecture.md) — System design and data flow
- [Database Schema](database.md) — PostgreSQL tables and relationships
- [Getting Started](../getting-started/quickstart.md) — Quick setup guide
