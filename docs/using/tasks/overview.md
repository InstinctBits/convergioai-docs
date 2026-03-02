---
title: WorkBoost — Task Management
description: Kanban task management with source tracking, priorities, and email-to-task conversion.
---

# WorkBoost — Task Management

WorkBoost automatically converts every incoming email into an actionable task and provides a full Kanban board for managing work across all Boost modules.

## Kanban board

WorkBoost organizes tasks in a drag-and-drop Kanban board with three columns:

```
┌──────────────┐  ┌──────────────┐  ┌──────────────┐
│   Pending    │  │ In Progress  │  │  Completed   │
│              │  │              │  │              │
│  ┌────────┐  │  │  ┌────────┐  │  │  ┌────────┐  │
│  │ Task 1 │  │  │  │ Task 3 │  │  │  │ Task 5 │  │
│  └────────┘  │  │  └────────┘  │  │  └────────┘  │
│  ┌────────┐  │  │  ┌────────┐  │  │  ┌────────┐  │
│  │ Task 2 │  │  │  │ Task 4 │  │  │  │ Task 6 │  │
│  └────────┘  │  │  └────────┘  │  │  └────────┘  │
└──────────────┘  └──────────────┘  └──────────────┘
```

Drag tasks between columns to update their status. Tasks are color-coded by their source module for quick identification.

## Source tracking

Tasks are color-coded by the module that created them:

| Source | Color | Description |
| ------ | ----- | ----------- |
| **CommBoost** | Blue | Created from incoming emails |
| **StreamBoost** | Purple | Stream-related tasks |
| **ContentBoost** | Teal | Content creation tasks |
| **IdeaBoost** | Yellow | Idea-derived tasks |
| **CampaignBoost** | Green | Campaign-related tasks |
| **Manual** | Gray | Manually created tasks |

## Auto-task creation

When an email is saved to the database (via IMAP sync or the auto-responder), a task is automatically created:

- **Title** — Derived from the email subject
- **Description** — Links back to the source email
- **Status** — Set to `pending` by default
- **Priority** — Default `medium`, adjustable
- **Source** — Set to `CommBoost`

## Views

### Kanban view

The default view shows a drag-and-drop board with tasks organized by status. Each task card displays:

- Task title and priority badge
- Source module color indicator
- Creation date
- Quick-action buttons for status changes

### List view

A detailed table view with full task information and advanced filters:

| Filter | Options |
| ------ | ------- |
| Status | `pending`, `in_progress`, `completed` |
| Priority | `low`, `medium`, `high` |
| Source | CommBoost, StreamBoost, Manual, etc. |
| Tag | Email-derived tag (Hello, Partners, etc.) |

### Analytics tab

Visual charts and metrics including:

- Task completion rates over time
- Source breakdown (pie chart by module)
- Priority distribution
- Average time to completion

## Task lifecycle

```
pending → in_progress → completed
```

Tasks can be updated at any time by dragging on the Kanban board or using the API.

## API

| Method | Endpoint | Description |
| ------ | -------- | ----------- |
| `GET` | `/api/tasks` | List tasks with filters |
| `POST` | `/api/tasks` | Create a new task |
| `PATCH` | `/api/tasks/:id` | Update status or priority |
| `GET` | `/api/stats` | Dashboard statistics including task counts |

## Related pages

- [Tasks API](../../api/tasks.md) — Task endpoint reference
- [CommBoost](../email-automation/overview.md) — Auto-create tasks from emails
- [AI Copilot](../ai-copilot/overview.md) — Manage tasks via natural language
