---
title: Changelog
description: Release history and version notes for Convergio AI.
---

# Changelog

All notable changes to Convergio AI are documented here.

The format follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/){ target="_blank" },
and this project adheres to [Semantic Versioning](https://semver.org/){ target="_blank" }.

---

## v3.0.0 — Better Auth & Built-in Automation

### Breaking changes

- **Authentication migrated from JWT to Better Auth** — Cookie-based sessions replace bearer tokens. All API requests now require session cookies instead of `Authorization` headers.
- **Database schema changes** — New `schema-better-auth.sql` and `schema-threading.sql` files added. Run `node run-schema.js` to apply.
- **Node.js 22+ required** — Minimum runtime version increased from 20 to 22.

### Added

- **Better Auth integration** — Email/password and Google OAuth authentication with cookie-based sessions
- **Organization system** — Auto-created on signup with member invitations and role management
- **Built-in email auto-responder** — Cron-based service (every 3 minutes) replaces n8n email dependency
- **Per-inbox auto-responder toggle** — Enable/disable auto-responses per inbox independently
- **Email threading** — RFC 2822 Message-ID, In-Reply-To, and References header tracking
- **Conversation view** — Thread-based email display with thread count badges
- **SafeEmailBody** — Sandboxed iframe rendering with image blocking for security
- **SMTP connection pooling** — Improved email delivery reliability
- **AI email draft generation** — Generate reply drafts using inbox knowledge bases
- **Free Tools module** — AI Prompt Generator with 5 framework templates
- **StreamBoost milestones** — Configurable subscriber threshold tracking with celebrations
- **Story card generation** — Instagram Stories graphics from stream metadata
- **Milestone card generation** — Custom celebration graphics
- **StreamBoost announcements** — Go-live, end-stream, and milestone announcement system
- **Security audit capabilities** — Dedicated security assessment endpoints
- **ContentBoost UI** — Scaffolding for AI content generation (coming soon)
- **IdeaBoost UI** — Scaffolding for idea management (coming soon)
- **CampaignBoost UI** — Scaffolding for email campaigns (coming soon)
- **Dashboard statistics endpoint** — `GET /api/stats` for aggregate metrics

### Changed

- **Express upgraded to 5.2** — Latest major version with improved routing
- **React upgraded to 19.2** — Latest with concurrent features
- **Vite upgraded to 7.2** — Faster build tooling
- **TypeScript upgraded to 5.9** — Latest type system improvements
- **n8n is now optional** — Core email automation is built-in; n8n used only for advanced workflows

### Removed

- JWT token authentication (replaced by Better Auth sessions)
- `JWT_SECRET` environment variable (replaced by `BETTER_AUTH_SECRET`)
- 2FA/TOTP support (to be re-implemented in a future release)

---

## Unreleased

- Initial documentation site launch
