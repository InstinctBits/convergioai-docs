---
title: Deployment
description: Deploy Convergio AI to production with Netlify, VPS, and Docker.
---

# Deployment

## Recommended stack

| Component | Platform | Description |
| --------- | -------- | ----------- |
| Frontend | Netlify / Vercel | Static build with API proxy |
| Backend | VPS with PM2 | Express API server |
| Database | PostgreSQL | Remote or managed |
| Workflows | Self-hosted n8n | Automation engine |

## Frontend (Netlify)

The `netlify.toml` is pre-configured:

```bash
npm run build
# Deploy dist/ to Netlify
```

Key settings:
- Build command: `npm run build`
- Publish directory: `dist`
- API proxy: `/api/*` redirects to your VPS

## Backend (PM2 on VPS)

```bash
# Install PM2
npm install -g pm2

# Start the API server
pm2 start pm2.ecosystem.config.cjs

# Save and enable startup
pm2 save
pm2 startup
```

## Docker

```bash
docker-compose -f docker-compose.prod.yml up -d
```

## Environment

Set all [configuration variables](../getting-started/configuration.md) in your production environment. Use a secrets manager for API keys.
