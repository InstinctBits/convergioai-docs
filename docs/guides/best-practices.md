---
title: Best Practices
description: Production patterns for reliability, security, and performance with Convergio AI.
---

# Best Practices

Recommendations for building robust applications with Convergio AI.

## Security

- **Never hardcode API keys.** Use environment variables or a secrets manager.
- **Rotate keys regularly.** Generate new keys and deprecate old ones on a schedule.
- **Use HTTPS exclusively.** All API communication must use TLS.

## Reliability

- **Implement retries with backoff.** Handle transient `429` and `5xx` errors gracefully. See [Error Handling](../api/errors.md).
- **Set timeouts.** Configure reasonable request timeouts to prevent hanging connections.
- **Monitor rate limit headers.** Track usage against limits proactively.

## Performance

- **Use connection pooling.** Reuse HTTP connections to reduce latency.
- **Batch requests when possible.** Minimize round trips for bulk operations.
- **Cache responses.** Cache deterministic responses to reduce API calls.

!!! info "This page will be expanded"
    Detailed patterns with code examples for each recommendation are coming soon.
