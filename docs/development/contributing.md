---
title: Contributing
description: How to contribute to Convergio AI — workflow, standards, and guidelines.
---

# Contributing

We welcome contributions from the community.

## Workflow

1. **Fork** the repository
2. **Create** a feature branch: `git checkout -b feature/your-feature`
3. **Make** changes following existing code patterns
4. **Test** thoroughly: `npm run lint`
5. **Commit** with conventional commit format
6. **Push** and submit a Pull Request

## Code standards

- TypeScript for all new code (frontend and backend)
- Follow existing patterns in the codebase
- Meaningful commit messages
- Update documentation for new features

## Areas for contribution

| Area | Examples |
| ---- | -------- |
| Frontend | UI improvements, accessibility, responsive design |
| Backend | API enhancements, performance, new endpoints |
| AI | Better prompts, new model integrations |
| Docs | Guides, examples, API documentation |
| Testing | Unit tests, integration tests, E2E |

## Project structure

- `src/` — React frontend (components, pages, context, utils)
- `server/` — Express backend (routes, services, middleware)
- `schema*.sql` — Database migrations
- `n8n-workflows/` — Automation workflow JSON files
- `knowledge-base/` — AI agent prompts and context
