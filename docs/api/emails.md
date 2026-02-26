---
title: Emails API
description: API endpoints for email management, auto-replies, and email intelligence.
---

# Emails API

## List emails

```
GET /api/emails
```

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| `tag` | string | Filter by tag (Hello, Partners, Info, Support, Neo) |
| `status` | string | Filter by status |
| `limit` | number | Results per page (default: 50) |
| `offset` | number | Pagination offset |

=== "Request"

    ```bash
    curl "http://localhost:3001/api/emails?tag=Hello&limit=10"
    ```

=== "Response (200)"

    ```json
    [
      {
        "id": 1,
        "message_id": "<abc@mail.com>",
        "from_address": "lead@company.com",
        "from_name": "Jane Smith",
        "to_address": "hello@digitechnomads.com",
        "subject": "Partnership inquiry",
        "body_text": "...",
        "tag": "Hello",
        "direction": "inbound",
        "received_at": "2026-02-25T10:30:00Z"
      }
    ]
    ```

## Create email (webhook)

```
POST /api/emails
```

Used by n8n to push new emails. Auto-derives tag, creates task, and saves auto-reply.

## Get email with replies

```
GET /api/emails/{id}
```

Returns the email with associated auto-replies.

## AI email analysis

```
GET /api/emails/{id}/ai-analysis
```

Returns AI-generated analysis of the email content including urgency, action items, and insights.

## Auto-replies

| Method | Endpoint | Description |
| ------ | -------- | ----------- |
| `GET` | `/api/auto-replies` | List all auto-replies |
| `POST` | `/api/auto-replies` | Save AI-generated reply |

## Send email

```
POST /api/send-email
```

Send an email via SMTP from a selected inbox.

## IMAP sync

| Method | Endpoint | Description |
| ------ | -------- | ----------- |
| `POST` | `/api/sync` | Trigger IMAP sync across all inboxes |
| `GET` | `/api/sync/status` | Get last sync timestamp |
