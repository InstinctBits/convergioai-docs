---
title: StreamBoost API
description: API endpoints for YouTube live stream automation, captions, cross-platform posting, milestones, and card generation.
---

# StreamBoost API

## Stream status

| Method | Endpoint | Description |
| ------ | -------- | ----------- |
| `GET` | `/api/streamboost/status` | Current stream state (live/ended, viewers, peak) |
| `GET` | `/api/streamboost/health` | StreamBoost health check |
| `POST` | `/api/streamboost/heartbeat` | Health heartbeat |
| `GET` | `/api/streamboost/sessions` | Active stream sessions |
| `GET` | `/api/streamboost/stats` | Stream statistics |

## Captions

| Method | Endpoint | Description |
| ------ | -------- | ----------- |
| `POST` | `/api/streamboost/captions/generate` | Generate AI captions for all platforms |
| `GET` | `/api/streamboost/captions/pending` | List pending captions awaiting approval |

### Generate captions

```
POST /api/streamboost/captions/generate
```

Generates platform-specific captions using the AI model and channel voice settings. Returns one caption per connected platform.

### Post captions

| Method | Endpoint | Description |
| ------ | -------- | ----------- |
| `POST` | `/api/streamboost/post/all` | Dispatch all approved captions to platforms |
| `POST` | `/api/streamboost/post/:captionId` | Post a specific caption to its platform |

## Platform credentials

| Method | Endpoint | Description |
| ------ | -------- | ----------- |
| `GET` | `/api/streamboost/credentials` | List platform connection status |
| `PUT` | `/api/streamboost/credentials/:platform` | Update credentials for a platform |
| `POST` | `/api/streamboost/credentials/:platform/test` | Test platform connectivity |

Supported platforms: `youtube`, `discord`, `x`, `instagram`, `facebook`

=== "Update credentials"

    ```bash
    curl -X PUT http://localhost:3001/api/streamboost/credentials/discord \
      -H "Content-Type: application/json" \
      -b cookies.txt \
      -d '{"credential_value": "https://discord.com/api/webhooks/..."}'
    ```

=== "Test connectivity"

    ```bash
    curl -X POST http://localhost:3001/api/streamboost/credentials/discord/test \
      -b cookies.txt
    ```

## Channel voice

| Method | Endpoint | Description |
| ------ | -------- | ----------- |
| `GET` | `/api/streamboost/channels` | Get per-platform voice settings |
| `PUT` | `/api/streamboost/channels/:platform` | Update tone, prompts, hashtags |

```json
{
  "tone_preset": "hype",
  "core_hashtags": ["#live", "#streaming", "#digitechnomads"],
  "cta_text": "Subscribe and turn on notifications!"
}
```

## Announcements

| Method | Endpoint | Description |
| ------ | -------- | ----------- |
| `GET` | `/api/streamboost/announcements` | Announcement history |
| `POST` | `/api/streamboost/announcements` | Create announcement |
| `POST` | `/api/streamboost/announcements/:id/retry` | Retry failed announcement |

Announcement types: `go_live`, `end_stream`, `milestone`

## Milestones

| Method | Endpoint | Description |
| ------ | -------- | ----------- |
| `GET` | `/api/streamboost/milestones` | List milestone thresholds |
| `POST` | `/api/streamboost/milestones` | Create custom milestone threshold |
| `POST` | `/api/streamboost/milestones/check` | Check if any milestones have been reached |
| `POST` | `/api/streamboost/milestones/trigger` | Manually trigger a milestone celebration |
| `DELETE` | `/api/streamboost/milestones/:id` | Delete a milestone threshold |

## Card generation

| Method | Endpoint | Description |
| ------ | -------- | ----------- |
| `POST` | `/api/streamboost/story-card` | Generate Instagram Stories card |
| `POST` | `/api/streamboost/milestone-card` | Generate milestone celebration card |

These endpoints generate shareable graphics that can be uploaded alongside captions.
