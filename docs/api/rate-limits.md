---
title: Rate Limits
description: Convergio AI API rate limits, response headers, and best practices.
---

# Rate Limits

The API enforces rate limits to ensure fair usage and platform stability.

## Response headers

Every API response includes rate limit information:

| Header                  | Description                        |
| ----------------------- | ---------------------------------- |
| `X-RateLimit-Limit`     | Maximum requests per window.       |
| `X-RateLimit-Remaining` | Requests remaining in the window.  |
| `X-RateLimit-Reset`     | Unix timestamp when the window resets. |

## Handling rate limits

When you receive a `429 Too Many Requests` response, wait until `X-RateLimit-Reset` before retrying. See [Error Handling](errors.md) for a retry implementation example.

!!! info "This page will be expanded"
    Tier-specific rate limits and upgrade paths are coming soon.
