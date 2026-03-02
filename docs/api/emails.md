---
title: Emails API
description: API endpoints for email management, threading, auto-responder, and IMAP sync.
---

# Emails API

## List emails

```
GET /api/emails
```

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| `tag` | string | Filter by tag (Hello, Partners, Info, Support, Neo) |
| `direction` | string | Filter by direction (`inbound`, `outbound`) |
| `search` | string | Search in subject and body |
| `limit` | number | Results per page (default: 50) |
| `offset` | number | Pagination offset |

=== "cURL"

    ```bash
    curl "http://localhost:3001/api/emails?tag=Hello&limit=10" -b cookies.txt
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
        "thread_count": 3,
        "received_at": "2026-02-25T10:30:00Z"
      }
    ]
    ```

## Get email details

```
GET /api/emails/:id
```

Returns the email with full body content and associated auto-replies.

## Get email thread

```
GET /api/emails/:id/thread
```

Returns the complete conversation thread for an email, ordered chronologically. Uses RFC 2822 Message-ID, In-Reply-To, and References headers to build the thread.

## Create / save email

```
POST /api/emails
```

Save an email to the database. Auto-derives tag from `to_address`, creates a task, and handles deduplication via `message_id`.

## Send email

```
POST /api/send-email
```

Send an email via SMTP from a configured inbox. Includes proper threading headers for replies.

```json
{
  "to": "recipient@example.com",
  "subject": "Re: Your inquiry",
  "body": "<p>Thank you for reaching out...</p>",
  "inbox": "hello",
  "in_reply_to": "<original-message-id@mail.com>"
}
```

## Upload attachment

```
POST /api/upload-attachment
```

Upload a file attachment for use in email composition. Returns the attachment metadata.

## IMAP sync

| Method | Endpoint | Description |
| ------ | -------- | ----------- |
| `POST` | `/api/sync` | Trigger IMAP sync across all configured inboxes |
| `GET` | `/api/sync/status` | Get last sync results and timestamps |
| `GET` | `/api/sync/config` | View configured inbox list |

## Auto-responder

| Method | Endpoint | Description |
| ------ | -------- | ----------- |
| `GET` | `/api/auto-responder/status` | Get auto-responder status per inbox |
| `POST` | `/api/auto-responder/toggle` | Enable/disable auto-responder for an inbox |

=== "Toggle request"

    ```json
    {
      "inbox": "hello",
      "enabled": true
    }
    ```

=== "Status response"

    ```json
    {
      "hello": { "enabled": true, "lastRun": "2026-03-02T10:00:00Z" },
      "partners": { "enabled": false, "lastRun": null },
      "info": { "enabled": true, "lastRun": "2026-03-02T10:00:00Z" },
      "support": { "enabled": true, "lastRun": "2026-03-02T09:57:00Z" },
      "neo": { "enabled": false, "lastRun": null }
    }
    ```

## SMTP inboxes

```
GET /api/smtp-inboxes
```

Returns the list of configured SMTP inboxes with their connection details (host, port, security).
