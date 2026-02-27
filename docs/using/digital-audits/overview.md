---
title: Digital Audits
description: AI-powered website and security audit workflows.
---

# Digital Audits

Convergio AI includes an AI-powered audit system for analyzing websites and generating comprehensive digital presence reports.

## How it works

1. Enter a website URL and optional business details
2. The audit request is sent to the n8n digital audit workflow
3. n8n orchestrates the analysis (security checks, SEO, performance)
4. AI generates a structured audit report with an overall score
5. Results are saved and displayed in the dashboard

## Audit types

| Type | Description |
| ---- | ----------- |
| **Digital Audit** | Comprehensive website analysis with AI-generated recommendations |
| **Security Audit** | Focused security assessment |

## Audit results

Results include:

- **Overall score** — Aggregate assessment (0-100)
- **Detailed results** — Stored as JSONB for flexible reporting
- **Business context** — Original business details provided with the request
- **Status tracking** — `pending` → `processing` → `completed`

## API

| Method | Endpoint | Description |
| ------ | -------- | ----------- |
| `GET` | `/api/audits` | List all audits |
| `POST` | `/api/audits` | Create new audit (triggers n8n) |
| `GET` | `/api/audits/{id}` | Get audit details |
| `POST` | `/api/audits/{id}/complete` | Complete audit with results (n8n callback) |
| `GET` | `/api/security-audits` | List security audits |
| `POST` | `/api/security-audits` | Run security audit |
| `GET` | `/api/security-audits/{id}` | Get security audit details |

## Related pages

- [AI Copilot](../ai-copilot/overview.md) — AI-powered analysis interface
- [Best Practices](../best-practices/best-practices.md) — Security recommendations
