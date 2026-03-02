---
title: Tasks API
description: API endpoints for WorkBoost task management and dashboard statistics.
---

# Tasks API

## List tasks

```
GET /api/tasks
```

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| `status` | string | Filter: `pending`, `in_progress`, `completed` |
| `priority` | string | Filter: `low`, `medium`, `high` |
| `tag` | string | Filter by email-derived tag |
| `source` | string | Filter by source module (CommBoost, StreamBoost, Manual, etc.) |

## Create task

```
POST /api/tasks
```

```json
{
  "title": "Follow up with client",
  "description": "Regarding partnership proposal",
  "priority": "high",
  "source": "Manual",
  "email_id": 42
}
```

## Update task

```
PATCH /api/tasks/:id
```

```json
{
  "status": "in_progress",
  "priority": "high"
}
```

## Dashboard statistics

```
GET /api/stats
```

Returns aggregate stats for the dashboard:

```json
{
  "totalEmails": 150,
  "tasksByStatus": {
    "pending": 23,
    "in_progress": 8,
    "completed": 45
  },
  "emailsByTag": {
    "Hello": 40,
    "Partners": 25,
    "Support": 50,
    "Info": 20,
    "Neo": 15
  }
}
```
