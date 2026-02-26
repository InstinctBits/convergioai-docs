---
title: Endpoints
description: Complete list of Convergio AI API endpoints with request and response schemas.
---

# Endpoints

All endpoints are versioned under `/v1` and require [authentication](authentication.md).

## Health check

```
GET /v1/health
```

Returns the current status of the API.

=== "Request"

    ```bash
    curl https://api.convergioai.com/v1/health
    ```

=== "Response"

    ```json
    {
      "status": "ok",
      "version": "1.0.0"
    }
    ```

!!! info "This page will be expanded"
    Full endpoint documentation with request/response schemas, parameters, and examples is coming soon.
