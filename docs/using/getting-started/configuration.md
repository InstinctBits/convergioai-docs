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

### Authentication

| Variable     | Description                   | Example                |
| ------------ | ----------------------------- | ---------------------- |
| `JWT_SECRET` | Secret key for JWT signing    | A random 64-char string |

### AI

| Variable          | Description              | Example          |
| ----------------- | ------------------------ | ---------------- |
| `ANTHROPIC_API_KEY` | Anthropic Claude API key | `sk-ant-api03-...` |

### Email (IMAP/SMTP)

| Variable      | Description          | Example             |
| ------------- | -------------------- | ------------------- |
| `IMAP_HOST`   | IMAP server hostname | `imap.gmail.com`    |
| `IMAP_PORT`   | IMAP server port     | `993`               |
| `SMTP_HOST`   | SMTP server hostname | `smtp.gmail.com`    |
| `SMTP_PORT`   | SMTP server port     | `587`               |
| `EMAIL_USER`  | Email account        | `you@example.com`   |
| `EMAIL_PASS`  | Email password/app password | `your-app-password` |

## Optional variables

### n8n Integration

| Variable       | Description           | Example                      |
| -------------- | --------------------- | ---------------------------- |
| `N8N_BASE_URL` | n8n instance base URL | `http://localhost:5678`      |

### Cal.com Integration

| Variable         | Description       | Example           |
| ---------------- | ----------------- | ----------------- |
| `CALCOM_API_KEY` | Cal.com API key   | `cal_live_...`    |

### Server

| Variable | Description        | Default |
| -------- | ------------------ | ------- |
| `PORT`   | Backend API port   | `3001`  |
| `NODE_ENV` | Runtime environment | `development` |

## Subscription plans

The database is seeded with three default plans:

| Plan       | Monthly (INR) | Token limit | Features                                |
| ---------- | ------------- | ----------- | --------------------------------------- |
| Free       | 0             | 1,000       | 100 emails/month, 50 AI responses      |
| Pro        | 1,999         | 50,000      | 5,000 emails, 2,500 AI responses       |
| Enterprise | 9,999         | 500,000     | Unlimited emails/AI, dedicated support  |

## Token packages

| Package    | Tokens  | Price (INR) | Bonus tokens |
| ---------- | ------- | ----------- | ------------ |
| Starter    | 5,000   | 499         | 0            |
| Growth     | 25,000  | 1,999       | 2,500        |
| Business   | 100,000 | 6,999       | 15,000       |
| Enterprise | 500,000 | 29,999      | 100,000      |

!!! warning "Security"
    Never commit `.env` files to version control. The `.gitignore` already excludes them.

## Next steps

- [Architecture](../core-concepts/architecture.md) — Understand the system design
- [API Reference](../../api/index.md) — Explore all endpoints
