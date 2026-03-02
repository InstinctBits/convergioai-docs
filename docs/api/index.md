---
title: API Reference
description: Complete REST API reference for Convergio AI — 67+ endpoints across emails, AI, tasks, calendar, streaming, and settings.
---

# API Reference

The Convergio AI API is a REST API built on Express 5. It accepts JSON request bodies and returns JSON responses. Full OpenAPI 3.0.3 documentation is available at `/api-docs` when the server is running.

**Base URL:**

```
http://localhost:3001/api
```

## Authentication

All API routes are protected by cookie-based session authentication powered by Better Auth. See [Authentication](authentication.md) for details.

```javascript
// All requests must include credentials (session cookie)
fetch("http://localhost:3001/api/emails", {
  credentials: "include",
});
```

## Endpoint groups

| Section | Endpoints | Description |
| ------- | --------- | ----------- |
| [Authentication](authentication.md) | 4 | Sign up, sign in, session, sign out, Google OAuth |
| [Emails](emails.md) | 10+ | Email CRUD, threading, sync, auto-responder |
| [Tasks](tasks.md) | 4 | Task management and dashboard stats |
| [AI](ai.md) | 8+ | Model selection, generation, chat, email intelligence |
| [Calendar](calendar.md) | 12 | Events, Cal.com sync, meeting detection |
| [Settings](settings.md) | 25+ | Profile, security, billing, API keys, tokens |
| [StreamBoost](streamboost.md) | 25+ | Stream state, captions, credentials, milestones, cards |
| [Error Handling](errors.md) | — | Status codes and error format |

## Quick reference

```bash
# Health check
curl http://localhost:3001/

# Sign in (saves session cookie)
curl -X POST http://localhost:3001/api/auth/sign-in/email \
  -H "Content-Type: application/json" \
  -c cookies.txt \
  -d '{"email": "user@example.com", "password": "securepassword"}'

# List emails (using session cookie)
curl http://localhost:3001/api/emails?tag=Hello&limit=10 -b cookies.txt

# Dashboard stats
curl http://localhost:3001/api/stats -b cookies.txt
```
