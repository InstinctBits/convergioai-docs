---
title: Self-Hosting
description: Host Convergio AI on your own infrastructure.
---

# Self-Hosting

Convergio AI is fully open-source and designed to run on your own infrastructure.

## Minimum requirements

| Resource | Recommendation |
| -------- | -------------- |
| CPU | 2 vCPU |
| RAM | 2 GB |
| Storage | 20 GB SSD |
| OS | Ubuntu 22.04+ |

## Setup checklist

1. Install Node.js 20+, PostgreSQL 15+
2. Clone the repository
3. Configure `.env` with your credentials
4. Run `npm run db:init` to create tables
5. Build frontend: `npm run build`
6. Start with PM2: `pm2 start pm2.ecosystem.config.cjs`
7. Set up reverse proxy (nginx) with SSL
8. Install and configure n8n for workflow automation
9. Configure DNS and firewall rules

## n8n self-hosting

n8n can run alongside the API on the same VPS:

```bash
npm install -g n8n
n8n start
```

Or use Docker: `docker run -d --name n8n n8nio/n8n`

Import the workflow JSON files from `n8n-workflows/` and configure credentials.
