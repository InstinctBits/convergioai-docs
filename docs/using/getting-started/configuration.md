---
title: Configuration
description: Environment variables, API keys, and configuration options for Convergio AI.
---

# Configuration

All configuration is managed through environment variables. Copy `.env.example` to `.env` and fill in the values.

## Required variables

### Database

| Variable       | Description                      | Example                                            |
| -------------- | -------------------------------- | -------------------------------------------------- |
| `DATABASE_URL` | PostgreSQL connection string     | `postgresql://user:pass@localhost:5432/convergioai` |

### Authentication (Better Auth)

| Variable             | Description                          | Example                     |
| -------------------- | ------------------------------------ | --------------------------- |
| `BETTER_AUTH_SECRET` | Secret key for session signing       | A random 64-char string     |
| `BETTER_AUTH_URL`    | Backend URL for Better Auth          | `http://localhost:3001`     |

### Server

| Variable        | Description         | Example                    |
| --------------- | ------------------- | -------------------------- |
| `PORT`          | Backend API port    | `3001`                     |
| `FRONTEND_URL`  | Frontend URL        | `http://localhost:5173`    |
| `API_BASE_URL`  | Backend URL         | `http://localhost:3001`    |
| `DASHBOARD_URL` | Dashboard URL       | `http://localhost:5173`    |

### AI

| Variable            | Description              | Example            |
| ------------------- | ------------------------ | ------------------ |
| `ANTHROPIC_API_KEY` | Anthropic Claude API key | `sk-ant-api03-...` |

### Email (per-inbox IMAP/SMTP)

Each of the five inboxes requires its own credentials:

=== "Hello Inbox"

    | Variable | Example |
    | -------- | ------- |
    | `HELLO_EMAIL_USER` | `hello@digitechnomads.com` |
    | `HELLO_EMAIL_PASSWORD` | `your-password` |
    | `HELLO_IMAP_HOST` | `imap.hostinger.com` |
    | `HELLO_IMAP_PORT` | `993` |

=== "Partners Inbox"

    | Variable | Example |
    | -------- | ------- |
    | `PARTNERS_EMAIL_USER` | `partners@digitechnomads.com` |
    | `PARTNERS_EMAIL_PASSWORD` | `your-password` |
    | `PARTNERS_IMAP_HOST` | `imap.hostinger.com` |
    | `PARTNERS_IMAP_PORT` | `993` |

=== "Info / Support / Neo"

    Same pattern: `INFO_EMAIL_USER`, `SUPPORT_EMAIL_USER`, `NEO_EMAIL_USER`, etc.

**SMTP (shared):**

| Variable    | Description          | Example                        |
| ----------- | -------------------- | ------------------------------ |
| `SMTP_USER` | SMTP sender account  | `hello@digitechnomads.com`     |
| `SMTP_PASS` | SMTP password        | `your-password`                |

## Optional variables

### n8n Integration

| Variable                       | Description                      | Example                                                               |
| ------------------------------ | -------------------------------- | --------------------------------------------------------------------- |
| `N8N_DISPATCHER_WEBHOOK_URL`   | n8n webhook for StreamBoost      | `https://loop.digitechnomads.com/webhook/streamboost/post-dispatcher` |

### Cal.com Integration

| Variable         | Description       | Example        |
| ---------------- | ----------------- | -------------- |
| `CALCOM_API_KEY` | Cal.com API key   | `cal_live_...` |

## Subscription plans

The database is seeded with three default plans:

| Plan       | Monthly (INR) | Token limit | Features                                |
| ---------- | ------------- | ----------- | --------------------------------------- |
| Free       | 0             | 1,000       | 100 emails/month, 50 AI responses      |
| Pro        | 1,999         | 50,000      | 5,000 emails, 2,500 AI responses       |
| Enterprise | 9,999         | 500,000     | Unlimited emails/AI, dedicated support  |

!!! warning "Security"
    Never commit `.env` files to version control. The `.gitignore` already excludes them.

## Next steps

- [CommBoost](../email-automation/overview.md) — Set up AI-powered email management
- [Deployment](../../hosting/deployment.md) — Deploy to production
- [Best Practices](../best-practices/best-practices.md) — Production patterns
