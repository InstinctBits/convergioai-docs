---
title: Settings API
description: API endpoints for user profile, security, billing, and token management.
---

# Settings API

All settings endpoints require JWT authentication.

## Profile

| Method | Endpoint | Description |
| ------ | -------- | ----------- |
| `GET` | `/api/settings/profile` | Get user profile |
| `PATCH` | `/api/settings/profile` | Update name, company, phone, timezone |
| `POST` | `/api/settings/profile/avatar` | Update avatar URL |
| `PATCH` | `/api/settings/profile/notifications` | Update notification preferences |

## Security

| Method | Endpoint | Description |
| ------ | -------- | ----------- |
| `POST` | `/api/settings/security/password` | Change password |
| `GET` | `/api/settings/security/2fa` | Get 2FA status |
| `POST` | `/api/settings/security/2fa/setup` | Initialize 2FA (returns TOTP secret) |
| `POST` | `/api/settings/security/2fa/verify` | Verify and enable 2FA |
| `POST` | `/api/settings/security/2fa/disable` | Disable 2FA |
| `GET` | `/api/settings/security/sessions` | List active sessions |
| `DELETE` | `/api/settings/security/sessions/{id}` | Revoke a session |
| `GET` | `/api/settings/security/api-keys` | List user API keys |
| `POST` | `/api/settings/security/api-keys` | Create API key (`cai_` prefix) |
| `DELETE` | `/api/settings/security/api-keys/{id}` | Revoke API key |
| `GET` | `/api/settings/security/login-history` | Login history (last 50) |

## Billing

| Method | Endpoint | Description |
| ------ | -------- | ----------- |
| `GET` | `/api/settings/billing/subscription` | Current subscription |
| `GET` | `/api/settings/billing/plans` | Available plans |
| `GET` | `/api/settings/billing/payment-methods` | Payment methods |
| `GET` | `/api/settings/billing/invoices` | Invoice history |
| `GET` | `/api/settings/billing/usage` | Usage overview |

## Tokens

| Method | Endpoint | Description |
| ------ | -------- | ----------- |
| `GET` | `/api/settings/tokens/balance` | Token balance |
| `GET` | `/api/settings/tokens/usage` | Usage over time (7d/30d/90d) |
| `GET` | `/api/settings/tokens/usage/by-model` | Usage by AI model |
| `GET` | `/api/settings/tokens/packages` | Purchasable packages |
| `POST` | `/api/settings/tokens/purchase` | Purchase tokens |
| `GET` | `/api/settings/tokens/history` | Usage history (paginated) |
| `GET` | `/api/settings/tokens/alerts` | List usage alerts |
| `POST` | `/api/settings/tokens/alerts` | Create alert |
| `PATCH` | `/api/settings/tokens/alerts/{id}` | Update alert |
| `DELETE` | `/api/settings/tokens/alerts/{id}` | Delete alert |
