---
title: Tasks API
description: API endpoints for task management.
---

# Tasks API

## List tasks

```
GET /api/tasks
```

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| `status` | string | Filter: `todo`, `in_progress`, `done` |
| `priority` | string | Filter: `low`, `medium`, `high`, `urgent` |
| `tag` | string | Filter by email-derived tag |

## Create task

```
POST /api/tasks
```

```json
{
  "title": "Follow up with client",
  "description": "Regarding partnership proposal",
  "priority": "high",
  "email_id": 42
}
```

## Get task

```
GET /api/tasks/{id}
```

## Update task

```
PATCH /api/tasks/{id}
```

```json
{
  "status": "in_progress",
  "priority": "urgent"
}
```

## Dashboard statistics

```
GET /api/stats
```

Returns aggregate stats:

```json
{
  "totalEmails": 150,
  "tasksByStatus": {
    "todo": 23,
    "in_progress": 8,
    "done": 45
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
