---
title: Quickstart
description: Get Convergio AI running locally in under 10 minutes.
---

# Quickstart

Get a fully functional Convergio AI instance running on your machine.

!!! info "Prerequisites"
    Make sure you have Node.js 20+, PostgreSQL 15+, and npm 9+ installed.
    See [Installation](installation.md) for detailed setup instructions.

## 1. Clone the repository

```bash
git clone https://github.com/InstinctBits/convergioai.git
cd convergioai
```

## 2. Install dependencies

```bash
npm install
```

## 3. Configure environment

```bash
cp .env.example .env
```

Edit `.env` with your credentials:

```bash
# Database
DATABASE_URL=postgresql://user:password@localhost:5432/convergioai

# AI
ANTHROPIC_API_KEY=sk-ant-...

# Email (IMAP/SMTP)
IMAP_HOST=imap.gmail.com
IMAP_PORT=993
SMTP_HOST=smtp.gmail.com
SMTP_PORT=587
EMAIL_USER=your@email.com
EMAIL_PASS=your-app-password

# JWT
JWT_SECRET=your-secret-key
```

## 4. Initialize the database

```bash
npm run db:init
```

This runs the SQL schemas (`schema.sql`, `schema-settings.sql`, `schema-calendar.sql`, `schema-streamboost.sql`) to create all required tables.

## 5. Start the development servers

```bash
npm run dev:all
```

This starts both servers concurrently:

| Service  | URL                     | Description       |
| -------- | ----------------------- | ----------------- |
| Frontend | `http://localhost:5173` | React dashboard   |
| Backend  | `http://localhost:3001` | Express API server |

## 6. Access the dashboard

Open [http://localhost:5173](http://localhost:5173) in your browser. You'll see the login page.

A demo account is seeded automatically:

| Field    | Value                        |
| -------- | ---------------------------- |
| Email    | `demo@digitechnomads.com`    |
| Password | `demo123`                    |

## What's next?

- [Installation](installation.md) — Detailed setup including Docker and n8n
- [Configuration](configuration.md) — All environment variables and options
- [Features](../index.md) — Explore what Convergio AI can do

## Next steps

- [Core Concepts](../core-concepts/concepts.md) — Understand the domain model
- [Email Automation](../email-automation/overview.md) — Set up AI-powered email
- [Configuration](configuration.md) — Fine-tune environment variables
