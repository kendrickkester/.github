# .github

Shared GitHub contribution and pull-request standards for Kendrick Kester's repositories.

## What this is

This repository holds account-wide default community health files. For a repository owned by this account that does not define its own version of a supported file, GitHub falls back to the file stored here.

| File | Purpose |
|---|---|
| [`PULL_REQUEST_TEMPLATE.md`](PULL_REQUEST_TEMPLATE.md) | Default pull-request body |
| [`CONTRIBUTING.md`](CONTRIBUTING.md) | Short shared contribution guidance |
| [`docs/PR_DOCUMENTATION_STANDARD.md`](docs/PR_DOCUMENTATION_STANDARD.md) | Canonical PR documentation standard |

The canonical standard is `docs/PR_DOCUMENTATION_STANDARD.md`. The default PR body is `PULL_REQUEST_TEMPLATE.md`. This README only points to them and does not duplicate the standard.

## Overrides and authority

A repository may define its own `PULL_REQUEST_TEMPLATE.md` (or other community health file) when it has legitimate project-specific requirements. The repository's own file takes precedence over the default here.

Project repositories remain authoritative for their own architecture, code, tests, and operational controls. Nothing here replaces those.

## Pattern in practice

The standard favors PR descriptions that explain root cause and behavior in a table, state exact verification results, and say plainly which live systems were and were not touched. It is project-neutral and applies equally to infrastructure, application code, data work, automation, security, and documentation.
