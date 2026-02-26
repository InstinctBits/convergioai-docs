---
title: Error Handling
description: Convergio AI API error codes, response formats, and retry strategies.
---

# Error Handling

The API uses standard HTTP status codes and returns structured JSON error responses.

## Error response format

```json
{
  "error": {
    "code": "invalid_api_key",
    "message": "The API key provided is invalid.",
    "status": 401
  }
}
```

## HTTP status codes

| Code  | Meaning               | Description                              |
| ----- | --------------------- | ---------------------------------------- |
| `200` | OK                    | Request succeeded.                       |
| `400` | Bad Request           | Invalid request body or parameters.      |
| `401` | Unauthorized          | Missing or invalid API key.              |
| `403` | Forbidden             | Insufficient permissions.                |
| `404` | Not Found             | Resource does not exist.                 |
| `429` | Too Many Requests     | Rate limit exceeded.                     |
| `500` | Internal Server Error | Unexpected server-side error.            |

## Retry strategy

For `429` and `5xx` errors, implement exponential backoff:

```python
import time
import requests

def request_with_retry(url, headers, json, max_retries=3):
    for attempt in range(max_retries):
        response = requests.post(url, headers=headers, json=json)
        if response.status_code in (429, 500, 502, 503):
            time.sleep(2 ** attempt)
            continue
        return response
    return response
```

!!! info "This page will be expanded"
    Detailed error codes per endpoint are coming soon.
