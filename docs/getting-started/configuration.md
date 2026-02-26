---
title: Configuration
description: Configure authentication, environment variables, and runtime options for Convergio AI.
---

# Configuration

## Authentication

All API requests require a valid API key. Set it as an environment variable:

```bash
export CONVERGIOAI_API_KEY="your-api-key-here"
```

Or pass it directly in your code:

```python
from convergioai import Client

client = Client(api_key="your-api-key-here")
```

!!! warning "Keep your API key secure"
    Never commit API keys to version control. Use environment variables or a secrets manager in production.

## Environment variables

| Variable              | Description                    | Default                          |
| --------------------- | ------------------------------ | -------------------------------- |
| `CONVERGIOAI_API_KEY` | Your API authentication key    | —                                |
| `CONVERGIOAI_BASE_URL`| API base URL                   | `https://api.convergioai.com/v1` |
| `CONVERGIOAI_TIMEOUT` | Request timeout in seconds     | `30`                             |

## Next steps

- [API Reference](../api/index.md) — Explore available endpoints
- [Best Practices](../guides/best-practices.md) — Production configuration tips
