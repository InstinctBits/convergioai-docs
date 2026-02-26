---
title: SDKs
description: Official SDKs and client libraries for Convergio AI.
---

# SDKs

Official client libraries for integrating Convergio AI into your applications.

| Language   | Package         | Status       |
| ---------- | --------------- | ------------ |
| Python     | `convergioai`   | :material-check-circle:{ .green } Available |
| JavaScript | `convergioai`   | :material-clock-outline: Coming soon |
| Go         | `convergioai-go` | :material-clock-outline: Coming soon |

## Python SDK

```bash
pip install convergioai
```

```python
from convergioai import Client

client = Client()
response = client.predict(input="Hello, Convergio!")
print(response)
```

For detailed SDK documentation, see the [Quickstart](../getting-started/quickstart.md).

!!! info "This page will be expanded"
    Full SDK reference with all methods, types, and configuration options is coming soon.
