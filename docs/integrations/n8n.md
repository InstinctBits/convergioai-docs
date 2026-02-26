---
title: n8n Workflows
description: Automated workflow pipelines for email processing, stream detection, and digital audits.
---

# n8n Workflows

Convergio AI uses [n8n](https://n8n.io) as its workflow automation engine. Pre-built workflow JSON files are included in the `n8n-workflows/` directory.

## Available workflows

| Workflow | File | Description |
| -------- | ---- | ----------- |
| **Email Agent** | `email-agent-workflow.json` | IMAP fetch → AI analysis → Auto-reply → SMTP send → API webhook |
| **YouTube Live Detector** | `01_YouTube_Live_Detector.json` | Polls YouTube Data API every 3 minutes for live streams |
| **Cross-Platform Poster** | `02_Cross_Posting_AI.json` | Posts approved captions to Discord, X, Instagram, Facebook |
| **Shorts Generator** | `03_Shorts_Generator.json` | Content repurposing workflow |
| **Discord XP System** | `04_Discord_XP_System.json` | Community engagement tracking |
| **Calendar Sync** | `calcom-calendar-sync.json` | Syncs Cal.com bookings to calendar events |
| **Digital Audit** | `digital-audit-workflow.json` | AI-powered website audit pipeline |

## Setup

1. Install n8n ([self-hosted](https://docs.n8n.io/hosting/) or [n8n Cloud](https://n8n.io/cloud/))
2. Import workflow JSON files via n8n UI (Settings → Import)
3. Configure credentials:
    - IMAP/SMTP for email
    - Anthropic Claude API key
    - HTTP endpoint pointing to your Express API
    - YouTube Data API key (for StreamBoost)
4. Activate workflows

## Webhook endpoints

n8n communicates with the API through these webhook endpoints:

| Endpoint | Used by | Direction |
| -------- | ------- | --------- |
| `POST /api/emails` | Email Agent | n8n → API |
| `POST /api/auto-replies` | Email Agent | n8n → API |
| `POST /api/n8n/email-response` | Email Agent | API → n8n (AI) |
| `POST /api/n8n/digital-audit` | Digital Audit | API → n8n (AI) |
| `POST /api/audits/{id}/complete` | Digital Audit | n8n → API |
| `GET /api/n8n/model-info` | All | n8n → API |
