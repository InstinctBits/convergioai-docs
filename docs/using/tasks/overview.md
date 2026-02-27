---
title: Task Management
description: Automatic task creation from emails with priorities, assignments, and status tracking.
---

# Task Management (WorkBoost)

WorkBoost automatically converts every incoming email into an actionable task, ensuring nothing falls through the cracks.

## Auto-task creation

When an email is saved to the database (via the n8n webhook or IMAP sync), a task is automatically created:

- **Title** — Derived from the email subject
- **Description** — Links back to the source email
- **Status** — Set to `todo` by default
- **Priority** — Default `medium`, adjustable

## Task lifecycle

```
todo → in_progress → done
```

## Filtering and views

| Filter | Options |
| ------ | ------- |
| Status | `todo`, `in_progress`, `done` |
| Priority | `low`, `medium`, `high`, `urgent` |
| Tag | Email-derived tag (Hello, Partners, etc.) |

## API

| Method | Endpoint | Description |
| ------ | -------- | ----------- |
| `GET` | `/api/tasks` | List tasks with filters |
| `POST` | `/api/tasks` | Create a new task |
| `GET` | `/api/tasks/{id}` | Get task details |
| `PATCH` | `/api/tasks/{id}` | Update status or priority |

## Related pages

- [Tasks API](../../api/tasks.md) — Task endpoint reference
- [Email Automation](../email-automation/overview.md) — Auto-create tasks from emails
- [AI Copilot](../ai-copilot/overview.md) — Manage tasks via natural language
