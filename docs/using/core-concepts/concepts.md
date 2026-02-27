---
title: Core Concepts
description: Key abstractions and terminology used across the Convergio AI platform.
---

# Core Concepts

## Boost Suite

Convergio AI organizes its features into a "Boost Suite" — a collection of focused tools that each enhance a specific aspect of business operations:

| Boost | Page | Description |
| ----- | ---- | ----------- |
| **CommBoost** | `/dashboard/commboost` | Multi-inbox email management with AI auto-replies |
| **WorkBoost** | `/dashboard/workboost` | Task management with priorities and assignments |
| **StreamBoost** | `/dashboard/streamboost` | YouTube live stream automation and cross-platform posting |
| **ContentBoost** | `/dashboard/contentboost` | AI-powered content creation tools |
| **IdeaBoost** | `/dashboard/ideaboost` | Brainstorming and ideation |
| **CampaignBoost** | `/dashboard/campaignboost` | Campaign management |

## Inboxes and tags

Convergio AI supports multiple email inboxes, each mapped to a **tag** derived from the recipient address. Tags determine:

- Which section of the dashboard displays the email
- Which AI system prompt and knowledge base is used for auto-replies
- How tasks are categorized

## AI tokens

AI usage is tracked through a token system:

- **Token balance** — Current available tokens for the user
- **Token usage** — Per-request tracking with model attribution
- **Token packages** — Purchasable bundles (Starter, Growth, Business, Enterprise)
- **Usage alerts** — Configurable threshold notifications

## Captions and approval flow

In StreamBoost, when a live stream is detected:

1. AI generates platform-specific **captions** (one per target platform)
2. Captions enter a **pending** state in the dashboard
3. User can **approve**, **edit**, or **skip** each caption
4. Approved captions are **dispatched** to the target platform (Discord, X, Instagram, Facebook)

## Workflows

n8n workflows automate background processes:

- **Email Agent** — IMAP fetch → AI analysis → Auto-reply generation → SMTP send → Database storage
- **YouTube Live Detector** — Polls YouTube API → Detects live streams → Triggers caption generation
- **Cross-Platform Poster** — Takes approved captions → Posts to Discord/X/Meta
- **Calendar Sync** — Syncs Cal.com bookings → Creates calendar events
- **Digital Audit** — Runs website analysis → Generates audit report

## Sessions and security

- **Sessions** are stored in the database with device info, IP, and expiry
- **2FA** uses TOTP with backup codes
- **API keys** use a `cai_` prefix with hashed storage
- **Login history** tracks all authentication attempts

## Related pages

- [Architecture](architecture.md) — System design and data flow
- [Database Schema](database.md) — PostgreSQL tables and relationships
- [Getting Started](../getting-started/quickstart.md) — Quick setup guide
