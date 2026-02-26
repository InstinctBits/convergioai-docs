---
title: API Reference
description: Complete REST API reference for Convergio AI — 80+ endpoints across emails, AI, tasks, calendar, streaming, and settings.
---

# API Reference

The Convergio AI API is a REST API built on Express 5. It accepts JSON request bodies and returns JSON responses. Full OpenAPI 3.0.3 documentation is available at `/api-docs` when the server is running.

**Base URL:**

```
http://localhost:3001/api
```

**Production (via Netlify proxy):**

```
https://convergioai.netlify.app/api
```

## Authentication

Most endpoints use JWT Bearer authentication. See [Authentication](authentication.md) for details.

```
Authorization: Bearer <jwt_token>
```

## Endpoint groups

| Section | Endpoints | Auth | Description |
| ------- | --------- | ---- | ----------- |
| [Authentication](authentication.md) | 5 | Mixed | Register, login, refresh, logout, profile |
| [Emails](emails.md) | 4 | No | Email CRUD, AI analysis |
| [Tasks](tasks.md) | 4 | No | Task management |
| [AI](ai.md) | 6 | No | Model selection, content generation, chat, intelligence |
| [Calendar](calendar.md) | 12 | No | Events, Cal.com sync, meeting detection |
| [Settings](settings.md) | 25+ | JWT | Profile, security, billing, tokens |
| [StreamBoost](streamboost.md) | 10+ | No | Stream state, captions, credentials, milestones |
| [Error Handling](errors.md) | — | — | Status codes and error format |

## Quick reference

```bash
# Health check
curl http://localhost:3001/api/health

# Login
curl -X POST http://localhost:3001/api/auth/login \
  -H "Content-Type: application/json" \
  -d '{"email": "demo@digitechnomads.com", "password": "demo123"}'

# List emails
curl http://localhost:3001/api/emails?tag=Hello&limit=10

# Dashboard stats
curl http://localhost:3001/api/stats
```
