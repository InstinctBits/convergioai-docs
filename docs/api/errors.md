---
title: Error Handling
description: Convergio AI API error codes, response formats, and retry strategies.
---

# Error Handling

The API uses standard HTTP status codes and returns JSON error responses.

## HTTP status codes

| Code | Meaning | Description |
| ---- | ------- | ----------- |
| `200` | OK | Request succeeded |
| `201` | Created | Resource created |
| `400` | Bad Request | Invalid parameters |
| `401` | Unauthorized | Missing or invalid session cookie |
| `403` | Forbidden | Insufficient permissions |
| `404` | Not Found | Resource not found |
| `409` | Conflict | Duplicate (e.g., email already exists) |
| `500` | Internal Server Error | Unexpected error |

## Error response format

```json
{
  "error": "Not authenticated"
}
```

## Common error scenarios

| Scenario | Code | Resolution |
| -------- | ---- | ---------- |
| No session cookie | `401` | Sign in first, include `credentials: "include"` in fetch |
| Session expired | `401` | Re-authenticate via `/api/auth/sign-in/email` |
| Invalid request body | `400` | Check required fields and data types |
| Duplicate email | `409` | Email already exists (deduplication by `message_id`) |
| IMAP sync failure | `500` | Check IMAP credentials and server connectivity |

## Retry strategy

For `5xx` errors, implement exponential backoff:

```python
import time, requests

session = requests.Session()
session.post("http://localhost:3001/api/auth/sign-in/email", json={
    "email": "user@example.com", "password": "securepassword"
})

for attempt in range(3):
    response = session.get("http://localhost:3001/api/emails")
    if response.status_code >= 500:
        time.sleep(2 ** attempt)
        continue
    break
```
