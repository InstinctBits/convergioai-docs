---
title: Installation
description: Install the Convergio AI SDK and set up your development environment.
---

# Installation

## Requirements

| Dependency | Minimum version |
| ---------- | --------------- |
| Python     | 3.10+           |
| pip        | 22.0+           |

## Install the SDK

=== "pip"

    ```bash
    pip install convergioai
    ```

=== "Poetry"

    ```bash
    poetry add convergioai
    ```

=== "uv"

    ```bash
    uv add convergioai
    ```

## Verify installation

```bash
python -c "import convergioai; print(convergioai.__version__)"
```

## Next steps

- [Quickstart](quickstart.md) — Make your first API call
- [Configuration](configuration.md) — Set up authentication and options
