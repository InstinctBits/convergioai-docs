---
title: Deployment
description: Deploy Convergio AI in production with Docker, Kubernetes, and cloud platforms.
---

# Deployment

This guide covers deploying Convergio AI in production environments.

## Docker

```bash
docker pull instinctbits/convergioai:latest
docker run -p 8000:8000 -e CONVERGIOAI_API_KEY=your-key instinctbits/convergioai:latest
```

## Environment variables

Set these in your deployment environment:

| Variable              | Required | Description                |
| --------------------- | -------- | -------------------------- |
| `CONVERGIOAI_API_KEY` | Yes      | API authentication key     |
| `DATABASE_URL`        | Yes      | PostgreSQL connection URI  |
| `REDIS_URL`           | No       | Redis connection URI       |
| `LOG_LEVEL`           | No       | Logging level (default: `info`) |

!!! info "This page will be expanded"
    Kubernetes manifests, Docker Compose configurations, and cloud-specific deployment guides are coming soon.
