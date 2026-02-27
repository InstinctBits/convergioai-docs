---
title: AI API
description: API endpoints for AI model management, content generation, chat, and email intelligence.
---

# AI API

## Get current model

```
GET /api/ai-model
```

Returns the currently active AI model.

## Set active model

```
POST /api/ai-model
```

```json
{
  "model": "claude"
}
```

Available models: `gemini`, `claude`, `qwen`, `qwen3`

## Generate content

```
POST /api/ai/generate
```

Generate AI content with optional model override.

```json
{
  "prompt": "Write a professional email response",
  "model": "claude"
}
```

## Chat (AI Copilot)

```
POST /api/ai/chat
```

Natural language chat endpoint. See [AI Operations Copilot](../using/ai-copilot/overview.md).

```json
{
  "message": "Summarize my recent emails"
}
```

## Email intelligence

```
POST /api/ai/email-intelligence
```

AI analysis of email content for urgency, insights, and action items.

## Runtime API key management

Manage AI provider API keys at runtime without restarting the server:

| Method | Endpoint | Description |
| ------ | -------- | ----------- |
| `GET` | `/api/api-keys` | List configured AI keys (status only) |
| `POST` | `/api/api-keys` | Add or override an AI provider key |
| `DELETE` | `/api/api-keys/{keyId}` | Remove a runtime key override |

## n8n integration endpoints

Used by n8n workflows to interact with the AI system:

| Method | Endpoint | Description |
| ------ | -------- | ----------- |
| `POST` | `/api/n8n/email-response` | Generate AI email response |
| `POST` | `/api/n8n/digital-audit` | Generate AI audit report |
| `GET` | `/api/n8n/model-info` | Get current model info |
