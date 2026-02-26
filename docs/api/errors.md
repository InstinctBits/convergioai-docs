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
| `401` | Unauthorized | Missing or invalid JWT |
| `403` | Forbidden | Insufficient permissions |
| `404` | Not Found | Resource not found |
| `409` | Conflict | Duplicate (e.g., email already exists) |
| `500` | Internal Server Error | Unexpected error |

## Retry strategy

For `5xx` errors, implement exponential backoff:

```python
import time, requests

for attempt in range(3):
    response = requests.get(url, headers=headers)
    if response.status_code >= 500:
        time.sleep(2 ** attempt)
        continue
    break
```
