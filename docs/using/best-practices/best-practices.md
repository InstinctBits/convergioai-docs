---
title: Best Practices
description: Production patterns for reliability, security, and performance with Convergio AI.
---

# Best Practices

## Email management

- **Tune knowledge bases** — Keep inbox-specific knowledge base files concise and up-to-date. The AI uses these for auto-reply context, so stale information leads to inaccurate responses.
- **Toggle auto-responder selectively** — Enable auto-responses for high-volume inboxes (Support, Info) and keep sales-critical inboxes (Hello, Partners) manual for personal touch.
- **Monitor auto-reply quality** — Review auto-replies periodically in the dashboard. Adjust knowledge bases when responses miss the mark.
- **Use threading** — Reply to emails through the dashboard to maintain proper threading headers. This keeps conversations grouped correctly.

## Authentication & security

- **Use a strong `BETTER_AUTH_SECRET`** — Generate a random 64+ character string. This signs all session cookies.
- **Rotate API keys** — Periodically regenerate developer API keys from Settings. Revoke unused keys.
- **Enable Google OAuth** — For team environments, Google OAuth simplifies onboarding and avoids password management overhead.
- **Session hygiene** — Review active sessions in Settings > Security. Revoke sessions from unknown devices.

## Performance

- **IMAP sync frequency** — Don't trigger manual sync too frequently. The auto-responder checks every 3 minutes, which is sufficient for most workflows.
- **SMTP pooling** — The built-in SMTP pool handles connection reuse automatically. Avoid creating manual SMTP connections.
- **Database indexing** — The schema files include indexes on frequently queried columns (`tag`, `direction`, `status`). Monitor query performance as email volume grows.

## StreamBoost

- **Test credentials** — Always use the test endpoint (`POST /api/streamboost/credentials/:platform/test`) after updating platform credentials.
- **Customize channel voice** — Generic captions perform poorly. Set tone presets and hashtag templates per platform for better engagement.
- **Review captions before posting** — Even with good voice settings, review AI-generated captions before approval. Edit for factual accuracy and timing.
- **Set meaningful milestones** — Configure milestone thresholds that match your growth stage. Celebrating too-small milestones dilutes impact.

## AI usage

- **Model selection** — Use Claude for high-quality email replies and complex analysis. Use Gemini for faster responses when quality tradeoffs are acceptable. Use Qwen for cost-effective bulk operations.
- **Knowledge base structure** — Each inbox's knowledge base should cover: company overview, product details, common questions, and response tone guidelines.
- **Prompt hygiene** — The auto-responder includes anti-injection prompts. Don't override these without understanding the security implications.

## Deployment

- **Use PM2 for production** — PM2 provides process management, auto-restart, and log management.
- **Separate database** — Run PostgreSQL on a dedicated instance or managed service for production workloads.
- **Environment isolation** — Use separate `.env` files for development, staging, and production. Never share credentials across environments.
- **Monitor disk space** — Email attachments and audit results consume storage. Set up alerts for disk usage.
