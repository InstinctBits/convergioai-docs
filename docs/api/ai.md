---
title: AI API
description: API endpoints for AI model management, content generation, chat, email intelligence, and draft generation.
---

# AI API

## Model management

### Get current model

```
GET /api/ai-model
```

Returns the currently active AI model.

### Set active model

```
POST /api/ai-model
```

```json
{
  "model": "claude"
}
```

Available models: `gemini`, `claude`, `qwen`, `qwen3`

## Content generation

### Generate content

```
POST /api/ai/generate
```

Generate AI content with optional model override.

```json
{
  "prompt": "Write a professional email response to a partnership inquiry",
  "model": "claude"
}
```

### Chat (AI Copilot)

```
POST /api/ai/chat
```

Multi-turn AI conversation endpoint. See [AI Operations Copilot](../using/ai-copilot/overview.md).

```json
{
  "message": "Summarize my recent emails from the Partners inbox"
}
```

## Email-specific AI

### Email intelligence

```
GET /api/ai/email-intelligence
```

AI analysis of email content providing urgency assessment, action items, and insights.

### Email draft generation

```
POST /api/ai/email-draft
```

Generate an email reply draft using the inbox-specific knowledge base for context.

```json
{
  "email_id": 42,
  "inbox": "hello"
}
```

The AI loads the relevant knowledge base files (e.g., `general.md` + `hello.md`) and generates a contextual draft with anti-injection prompts.

## API key management

Manage developer API keys for programmatic access:

| Method | Endpoint | Description |
| ------ | -------- | ----------- |
| `GET` | `/api/api-keys` | List API keys |
| `POST` | `/api/api-keys` | Create a new API key |
| `DELETE` | `/api/api-keys/:keyId` | Revoke an API key |

## n8n integration endpoints

Used by n8n workflows for advanced automation:

| Method | Endpoint | Description |
| ------ | -------- | ----------- |
| `POST` | `/api/n8n/email-response` | Generate AI email response (legacy) |
| `POST` | `/api/n8n/digital-audit` | Generate AI audit report |
| `GET` | `/api/n8n/model-info` | Get current model info and availability |

!!! info "Legacy endpoints"
    The `/api/n8n/email-response` endpoint is maintained for backward compatibility. New deployments should use the built-in auto-responder instead.
