---
title: Emails API
description: API endpoints for email management, threading, read/unread tracking, inbox configuration, auto-responder, and IMAP sync.
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
| `is_read` | string | Filter by read status (`true`, `false`) |
| `limit` | number | Results per page (default: 50) |
| `offset` | number | Pagination offset |

=== "cURL"

    ```bash
    curl "http://localhost:3002/api/emails?tag=Hello&is_read=false&limit=10" -b cookies.txt
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
        "is_read": false,
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

=== "Response (200)"

    ```json
    {
      "thread_id": "<abc@mail.com>",
      "messages": [
        {
          "id": 1,
          "message_id": "<abc@mail.com>",
          "from_name": "Jane Smith",
          "from_address": "lead@company.com",
          "to_address": "hello@digitechnomads.com",
          "subject": "Partnership inquiry",
          "body_text": "...",
          "body_html": "...",
          "direction": "inbound",
          "in_reply_to_message_id": null,
          "received_at": "2026-02-25T10:30:00Z"
        },
        {
          "id": 5,
          "message_id": "<def@digitechnomads.com>",
          "direction": "outbound",
          "in_reply_to_message_id": "<abc@mail.com>",
          "received_at": "2026-02-25T11:00:00Z"
        }
      ]
    }
    ```

## Mark read/unread

```
PATCH /api/emails/read
```

Bulk mark emails (and all emails in their threads) as read or unread.

=== "Request"

    ```json
    {
      "ids": [1, 5, 12],
      "is_read": true
    }
    ```

=== "Response (200)"

    ```json
    {
      "updated": 5,
      "message": "Marked 5 email(s) as read"
    }
    ```

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

=== "Request"

    ```json
    {
      "to": "recipient@example.com",
      "subject": "Re: Your inquiry",
      "body": "<p>Thank you for reaching out...</p>",
      "from_inbox": "hello",
      "parent_message_id": "<original-message-id@mail.com>",
      "references_chain": "<original-message-id@mail.com>"
    }
    ```

=== "Response (200)"

    ```json
    {
      "success": true,
      "messageId": "<new-message-id@digitechnomads.com>",
      "emailId": 42,
      "message": "Email sent successfully"
    }
    ```

| Field | Description |
| ----- | ----------- |
| `from_inbox` | Inbox tag (case-insensitive) — matches against `email_inboxes.tag` |
| `parent_message_id` | The `message_id` of the email being replied to — used for threading |
| `references_chain` | RFC 2822 References header for deep threading |
| `cc`, `bcc` | Optional CC/BCC recipients |
| `attachments` | Array of storage keys from `/api/upload-attachment` |

## Upload attachment

```
POST /api/upload-attachment
```

Upload a file attachment for use in email composition. Returns the attachment metadata.

---

## Inbox management

Inboxes are managed via the API with credentials encrypted at rest (AES-256-GCM).

### List inboxes

```
GET /api/inboxes
```

Returns all configured inboxes with connection details. Passwords are never included in the response.

### Add inbox

```
POST /api/inboxes
```

=== "Request"

    ```json
    {
      "name": "Hello",
      "email_address": "hello@digitechnomads.com",
      "tag": "Hello",
      "imap_host": "mail.example.com",
      "imap_port": 993,
      "imap_user": "hello@digitechnomads.com",
      "imap_password": "secret",
      "imap_tls": true,
      "smtp_host": "mail.example.com",
      "smtp_port": 465,
      "smtp_user": "hello@digitechnomads.com",
      "smtp_password": "secret",
      "smtp_tls": true,
      "is_active": true,
      "auto_reply_enabled": false
    }
    ```

=== "Response (201)"

    ```json
    {
      "id": 1,
      "message": "Inbox created"
    }
    ```

### Update inbox

```
PATCH /api/inboxes/:id
```

Partial update — only send the fields you want to change. Passwords are re-encrypted on update.

### Delete inbox

```
DELETE /api/inboxes/:id
```

Deletes an inbox. The last active inbox cannot be deleted.

### Test connection

```
POST /api/inboxes/:id/test
```

Tests both IMAP and SMTP connectivity for a saved inbox. Returns independent results for each protocol.

=== "Response (200)"

    ```json
    {
      "imap": { "success": true, "error": "" },
      "smtp": { "success": true, "error": "" }
    }
    ```

---

## IMAP sync

| Method | Endpoint | Description |
| ------ | -------- | ----------- |
| `POST` | `/api/sync` | Trigger IMAP sync across all configured inboxes |
| `GET` | `/api/sync/status` | Get last sync results and timestamps |

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

Returns the list of active SMTP inboxes with their tag and email address (for compose UI dropdowns).
