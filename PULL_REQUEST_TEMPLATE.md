## Summary

<!--
In 2-4 sentences:
- Why does this change exist?
- What outcome does it produce?
- Does live behavior change, or is this code-only / reference?
- Call out the most important invariant when relevant (for example: "Current production state is unchanged.").

Standard: docs/PR_DOCUMENTATION_STANDARD.md in kendrickkester/.github
Delete every section below that does not apply. Small PRs need only Summary, Changes, and Verification.
-->

## Changes

<!--
For substantive work, prefer a table that explains behavior, not files:

| Area / Finding | Root Cause | Resolution |
|---|---|---|
| ... | ... | ... |

For a small PR, concise bullets are fine. Files belong in the diff, not here.
-->

## Architecture / Behavior Impact

<!--
Optional: remove if not applicable.
State behavioral or architectural effects, and important invariants that are preserved
(for example: "No privilege expansion." or "Public API unchanged.").
-->

## Cross-Repository Impact

<!--
Optional: remove if none.
Name the affected repository/project, the impact, who owns it, whether anything was mutated there, and any prerequisites.
-->

## Deferred / Out of Scope

<!--
Optional: remove if none.
List directly relevant work intentionally excluded from this PR. Do not list unrelated ideas.
-->

## Verification

<!--
State the exact validation performed. Prefer:

| Check | Result |
|---|---|
| `make check` | PASS |

Avoid "tests pass." Do not report CI as passing until it has completed.
-->

## Live Effects

<!--
Optional: required for infrastructure, deployment, external-system, account, or data-changing PRs.
Remove when clearly irrelevant. Include only rows that matter to this project.

| Surface | Effect |
|---|---|
| Cloud resources | No change |
| Repository settings | No change |
| Runtime | Unchanged |
-->

## Rollback

<!--
Optional: remove if rollback is trivial or obvious (for example, a plain git revert).
Otherwise describe the ordered steps.
-->

## Merge Readiness

<!--
Optional: use for high-rigor or controlled workflows; remove otherwise.

- Exact head reviewed: `<SHA>`
- CI: PASS / PENDING
- Recommended for merge: Yes / No
- Remaining blocker: None / ...

Do not claim readiness without evidence.
-->
