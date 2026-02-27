---
title: AI Operations Copilot
description: Natural language chat interface for email summaries, lead tracking, and operational insights.
---

# AI Operations Copilot

The AI Operations Copilot is a conversational interface embedded in the Convergio AI dashboard. It provides natural language access to your email data, tasks, and operational metrics.

## Capabilities

- **Summarize emails** — Get concise summaries of recent emails across all inboxes
- **Identify urgent items** — Surface emails and tasks that need immediate attention
- **Track leads** — Overview of leads and business opportunities from the Hello inbox
- **Task summaries** — Status of all tasks with priority breakdown
- **General questions** — Ask anything about your data

## Quick actions

The copilot includes pre-built quick actions:

| Action | Prompt |
| ------ | ------ |
| Summarize emails | "Summarize my recent emails" |
| Urgent items | "What urgent items need my attention?" |
| Leads overview | "Show me leads and opportunities" |
| Task summary | "Give me a task summary" |

## How it works

The copilot uses the `/api/ai/chat` endpoint, which:

1. Accepts a natural language message
2. Queries relevant data from the database (emails, tasks, stats)
3. Passes context to the active AI model (Claude, Gemini, or Qwen)
4. Returns a structured response

## Multi-model support

The copilot respects the globally selected AI model. Switch models at any time via the AI model selector:

- **Google Gemini** — Fast responses, good for general queries
- **Anthropic Claude** — High quality reasoning, best for complex analysis
- **Qwen 480B** — Alternative via OpenRouter
- **Qwen3-8B** — Lightweight option via Bytez

## Related pages

- [Email Automation](../email-automation/overview.md) — AI-powered email management
- [AI API](../../api/ai.md) — AI endpoint reference
- [Task Management](../tasks/overview.md) — Task operations via copilot
