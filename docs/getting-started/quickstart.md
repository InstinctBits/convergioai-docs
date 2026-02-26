---
title: Quickstart
description: Make your first Convergio AI API call in under five minutes.
---

# Quickstart

Get up and running with Convergio AI in minutes.

## Prerequisites

- Python 3.10+ or Node.js 18+
- A Convergio AI API key ([get one here](#))

## Make your first request

=== "Python"

    ```python
    import requests

    response = requests.post(
        "https://api.convergioai.com/v1/predict",
        headers={"Authorization": "Bearer YOUR_API_KEY"},
        json={"input": "Hello, Convergio!"},
    )

    print(response.json())
    ```

=== "cURL"

    ```bash
    curl -X POST https://api.convergioai.com/v1/predict \
      -H "Authorization: Bearer YOUR_API_KEY" \
      -H "Content-Type: application/json" \
      -d '{"input": "Hello, Convergio!"}'
    ```

=== "JavaScript"

    ```javascript
    const response = await fetch("https://api.convergioai.com/v1/predict", {
      method: "POST",
      headers: {
        Authorization: "Bearer YOUR_API_KEY",
        "Content-Type": "application/json",
      },
      body: JSON.stringify({ input: "Hello, Convergio!" }),
    });

    const data = await response.json();
    console.log(data);
    ```

## Next steps

- [Installation](installation.md) — Set up your local development environment
- [Configuration](configuration.md) — Customize your setup
- [API Reference](../api/index.md) — Explore all available endpoints
