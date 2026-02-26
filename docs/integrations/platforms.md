---
title: Platform Connections
description: Configure YouTube, Discord, X, Instagram, and Facebook for StreamBoost cross-platform posting.
---

# Platform Connections

StreamBoost posts announcements to multiple platforms. Each requires its own credentials.

## Supported platforms

| Platform | Credential type | Used for |
| -------- | --------------- | -------- |
| **YouTube** | API key | Live stream detection via Data API v3 |
| **Discord** | Webhook URL | Rich embed or plain text announcements |
| **X (Twitter)** | OAuth2 | Tweet posting |
| **Meta (Instagram/Facebook)** | System user token | Page/profile posting via Graph API |

## Configuration

Manage credentials via the StreamBoost settings page or the API:

```bash
# Check connection status
curl http://localhost:3001/api/streamboost/credentials

# Add credentials
curl -X POST http://localhost:3001/api/streamboost/credentials \
  -H "Content-Type: application/json" \
  -d '{"platform": "discord", "credential_value": "https://discord.com/api/webhooks/..."}'
```

## Per-platform voice settings

Customize the AI tone for each platform:

| Platform | Default tone | Format |
| -------- | ------------ | ------ |
| Discord | Friendly | Embed |
| X | Mixed | Tweet with hashtags |
| Instagram | Hype | Post with image |
| Facebook | Professional | Page post |
