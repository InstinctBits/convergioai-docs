---
title: Cal.com Integration
description: Connect Cal.com for booking sync and scheduling management.
---

# Cal.com Integration

Sync your Cal.com bookings directly into the Convergio AI calendar.

## Setup

1. Get your Cal.com API key from [cal.com/settings/developer](https://cal.com/settings/developer)
2. In Convergio AI, go to **Settings** or use the API:

```bash
curl -X POST http://localhost:3001/api/calcom/settings \
  -H "Content-Type: application/json" \
  -d '{"apiKey": "cal_live_..."}'
```

3. Trigger a sync: `POST /api/calcom/sync`
4. Bookings appear as calendar events with `source: calcom`

## API endpoints

| Method | Endpoint | Description |
| ------ | -------- | ----------- |
| `GET` | `/api/calcom/settings` | Check connection status |
| `POST` | `/api/calcom/settings` | Save API key |
| `POST` | `/api/calcom/sync` | Trigger booking sync |
| `GET` | `/api/calcom/event-types` | List your Cal.com event types |

## Automated sync

Use the `calcom-calendar-sync.json` n8n workflow for periodic automatic syncing.
