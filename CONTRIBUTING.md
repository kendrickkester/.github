# Contributing

Shared guidance for repositories owned by this account. A repository's own `CONTRIBUTING.md` takes precedence over this file.

## Principles

**Scope discipline.** Keep PRs cohesive. Do not bundle unrelated changes merely because they were discovered in the same work session.

**Root-cause documentation.** A bug-fix PR explains why the behavior was wrong, not only which files changed.

**Evidence.** A substantive PR states exactly how correctness was validated: which checks ran and what they returned.

**Safety and side effects.** PRs touching infrastructure, security, deployment, data, or external systems state explicitly which live systems were and were not changed.

**Cross-project ownership.** Do not silently fix another repository's responsibility inside the current PR. Document the dependency and address it in the owning repository.

**Truthfulness.** Keep these states distinct, and never describe code-only capability as live-proven:

- implemented
- tested
- deployed
- live-verified
- code-only / reference
- deferred

## Pull requests

Follow [`docs/PR_DOCUMENTATION_STANDARD.md`](docs/PR_DOCUMENTATION_STANDARD.md) and the default [`PULL_REQUEST_TEMPLATE.md`](PULL_REQUEST_TEMPLATE.md). Match the level of detail to the size and risk of the change, and remove template sections that do not apply.
