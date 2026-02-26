---
title: StreamBoost API
description: API endpoints for YouTube live stream automation, captions, and cross-platform posting.
---

# StreamBoost API

## Stream status

```
GET /api/streamboost/status
```

Returns the current stream state (live/ended, viewer count, peak viewers).

## Captions

| Method | Endpoint | Description |
| ------ | -------- | ----------- |
| `POST` | `/api/streamboost/captions/generate` | Generate AI captions for all platforms |
| `GET` | `/api/streamboost/captions/pending` | List pending captions awaiting approval |
| `PATCH` | `/api/streamboost/captions/pending` | Bulk update caption status |
| `POST` | `/api/streamboost/captions/approve` | Approve or skip a caption |
| `POST` | `/api/streamboost/captions/dispatch` | Post approved captions to platforms |

## Platform credentials

| Method | Endpoint | Description |
| ------ | -------- | ----------- |
| `GET` | `/api/streamboost/credentials` | List platform connection status |
| `POST` | `/api/streamboost/credentials` | Add platform credentials |
| `PATCH` | `/api/streamboost/credentials` | Update credentials |

## Channel voice

| Method | Endpoint | Description |
| ------ | -------- | ----------- |
| `GET` | `/api/streamboost/voice` | Get per-platform voice settings |
| `PATCH` | `/api/streamboost/voice` | Update tone, prompts, hashtags |

## Milestones

| Method | Endpoint | Description |
| ------ | -------- | ----------- |
| `GET` | `/api/streamboost/milestones` | List milestone thresholds |
| `POST` | `/api/streamboost/milestones` | Add custom threshold |
| `PATCH` | `/api/streamboost/milestones` | Update threshold |
