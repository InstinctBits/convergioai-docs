---
title: Installation
description: Detailed installation guide for Convergio AI with Node.js, Docker, and PM2 setup.
---

# Installation

## System requirements

| Component   | Requirement      |
| ----------- | ---------------- |
| Node.js     | 22.0 or higher   |
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
node run-schema.js
```

This executes six schema files:

1. `schema.sql` — Core tables (emails, tasks, auto-replies, app settings)
2. `schema-better-auth.sql` — Better Auth tables (users, sessions, accounts, organizations)
3. `schema-settings.sql` — User settings, API keys, email signatures
4. `schema-calendar.sql` — Calendar events
5. `schema-streamboost.sql` — Stream state, announcements, platform credentials, milestones
6. `schema-threading.sql` — Email threading (Message-ID, In-Reply-To, References)

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

```bash
# Install PM2 globally
npm install -g pm2

# Build the frontend
npm run build

# Start with PM2
pm2 start pm2.ecosystem.config.cjs
```

## n8n workflow setup (optional)

!!! info "n8n is optional in v3.0"
    Core email automation now runs as a built-in service. n8n is only needed for advanced workflows like StreamBoost post dispatching and custom automations.

To set up n8n:

1. Install n8n ([self-hosted](https://docs.n8n.io/hosting/) or [cloud](https://n8n.io/cloud/))
2. Import workflow files from `n8n-workflows/`
3. Configure credentials in n8n
4. Activate the workflows

## Verify installation

```bash
# Check the API health
curl http://localhost:3001/
```

## Next steps

- [Quickstart](quickstart.md) — Get running in 10 minutes
- [Configuration](configuration.md) — Environment variables and API keys
- [Architecture](../core-concepts/architecture.md) — Understand the system design
