---
title: Installation
description: Detailed installation guide for Convergio AI with Node.js, Docker, and n8n setup.
---

# Installation

## System requirements

| Component   | Requirement      |
| ----------- | ---------------- |
| Node.js     | 20.0 or higher   |
| PostgreSQL  | 15 or higher     |
| npm         | 9.0 or higher    |
| OS          | macOS, Linux, Windows |

## Method 1: Local development

### Install Node.js dependencies

```bash
git clone https://github.com/InstinctBits/convergioai.git
cd convergioai
npm install
```

### Set up PostgreSQL

Create the database:

```bash
createdb convergioai
```

Initialize all schemas:

```bash
npm run db:init
```

This executes four schema files in order:

1. `schema.sql` — Core tables (emails, tasks, auto-replies, app settings)
2. `schema-settings.sql` — Users, auth, billing, API keys, token management
3. `schema-calendar.sql` — Calendar events, Cal.com settings
4. `schema-streamboost.sql` — Stream state, announcements, platform credentials, captions

### Start the servers

```bash
# Start both frontend and backend concurrently
npm run dev:all

# Or start them separately
npm run dev      # Frontend (Vite) — port 5173
npm run server   # Backend (Express) — port 3001
```

## Method 2: Docker

```bash
# Build and start all services
docker-compose up -d

# Access the application
# Frontend: http://localhost:5173
# Backend:  http://localhost:3001
```

## Method 3: Production with PM2

The repository includes a PM2 ecosystem config:

```bash
# Install PM2 globally
npm install -g pm2

# Build the frontend
npm run build

# Start with PM2
pm2 start pm2.ecosystem.config.cjs
```

## n8n workflow setup (optional)

n8n powers the automated email processing pipeline. To set it up:

1. Install n8n ([self-hosted](https://docs.n8n.io/hosting/) or [cloud](https://n8n.io/cloud/))
2. Import the workflow files from `n8n-workflows/`:
   - `email-agent-workflow.json` — IMAP → AI → SMTP pipeline
   - `calcom-calendar-sync.json` — Cal.com booking sync
   - `digital-audit-workflow.json` — Security audit automation
   - `01_YouTube_Live_Detector.json` — StreamBoost live detection
   - `02_Cross_Posting_AI.json` — Multi-platform announcements
3. Configure credentials in n8n for your email, Claude API, and database
4. Activate the workflows

## Verify installation

```bash
# Check the API health
curl http://localhost:3001/api/health
```

Expected response:

```json
{
  "status": "ok",
  "version": "3.0.0"
}
```

## Next steps

- [Configuration](configuration.md) — Environment variables and API key setup
- [Features](../features/index.md) — Explore platform capabilities
