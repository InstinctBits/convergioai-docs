---
title: Calendar API
description: API endpoints for calendar events, Cal.com integration, and AI meeting detection.
---

# Calendar API

## Events

| Method | Endpoint | Description |
| ------ | -------- | ----------- |
| `GET` | `/api/calendar/events` | List events (filterable by start, end, status, source) |
| `POST` | `/api/calendar/events` | Create event (supports Cal.com booking upsert) |
| `GET` | `/api/calendar/events/{id}` | Get event details |
| `PATCH` | `/api/calendar/events/{id}` | Update event |
| `DELETE` | `/api/calendar/events/{id}` | Delete event |
| `PATCH` | `/api/calendar/events/by-calcom/{bookingId}` | Update by Cal.com booking ID |
| `GET` | `/api/calendar/upcoming` | List upcoming events |
| `GET` | `/api/calendar/stats` | Calendar statistics |

## AI meeting detection

| Method | Endpoint | Description |
| ------ | -------- | ----------- |
| `POST` | `/api/calendar/detect` | Detect meeting signals in text |
| `POST` | `/api/calendar/events/from-email` | Create event from detected meeting |

## Cal.com

| Method | Endpoint | Description |
| ------ | -------- | ----------- |
| `GET` | `/api/calcom/settings` | Get Cal.com config status |
| `POST` | `/api/calcom/settings` | Save Cal.com API key |
| `POST` | `/api/calcom/sync` | Trigger booking sync |
| `GET` | `/api/calcom/event-types` | List Cal.com event types |
