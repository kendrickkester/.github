# Pull Request Documentation Standard v1

A project-neutral standard for pull-request descriptions. It applies to infrastructure, application code, data engineering, automation, architecture, security, documentation, and personal projects.

The default PR body is [`PULL_REQUEST_TEMPLATE.md`](../PULL_REQUEST_TEMPLATE.md). Project repositories remain authoritative for their own architecture, code, tests, and operational controls.

## 1. Core questions

Every substantive PR should let a reviewer quickly answer:

1. Why does this change exist?
2. What was wrong or missing?
3. What changed?
4. What behavior or architecture is affected?
5. How was correctness proven?
6. What was intentionally not changed?
7. Are there live side effects?
8. Is it safe to merge?

## 2. Title

Prefer:

```
<type>(<scope>): <clear outcome>
```

Examples:

```
fix(platform): correct dormant environment and sample contracts
fix(foundation): restore operator and control-plane correctness
feat(runtime): add independent shutdown attestation
docs(platform): restore repository truth
refactor(foundation): consolidate federation evidence projection
```

Prefer outcomes over file names or implementation mechanics.

## 3. Complexity levels

Choose the smallest level that lets a reviewer make a merge decision. Do not include empty sections for compliance.

| Level | Sections | Use for |
|---|---|---|
| Small | Summary, Changes, Verification | Small bug fixes, documentation, narrow dependency updates, isolated tests |
| Standard | Summary, Changes, Architecture / Behavior Impact, Verification, Live Effects | The default for a substantive PR |
| High-Rigor | Summary, Findings / Changes, Architecture / Behavior Impact, Cross-Repository Impact, Deferred / Out of Scope, Verification, Live Effects, Rollback, Merge Readiness | Infrastructure, IAM/security, migrations, architecture, lifecycle, production-impacting changes, cross-repository contracts, substantial remediation |

## 4. Section standards

### Summary

2-4 sentences. Explain the problem, the outcome, and whether live behavior or only code/reference behavior changes. Call out the most important invariant when appropriate, for example:

```
**Current Dev desired state is unchanged.**
```

### Findings / Changes

For substantial work, prefer:

```
| Finding / Area | Root Cause | Resolution |
|---|---|---|
| ... | ... | ... |
```

The table must explain behavior. Avoid file-list-only documentation.

Bad:

```
main.tf updated
values.yaml updated
```

Good:

```
Generic IAM policy encoded the Dev resource prefix, causing stage/prod policies to target the wrong resource family.
```

### Architecture / Behavior Impact

Explain behavioral changes, architectural changes, important preserved invariants, and migration or lifecycle implications. Examples:

```
Current Dev state unchanged.
No privilege expansion.
Runtime remains down.
Foundation authority unchanged.
```

### Cross-Repository Impact

Use when another repository, project, or service owns or consumes related behavior. State the affected project, the impact, who owns it, whether mutation occurred, and any prerequisites. Never silently cross ownership boundaries.

### Deferred / Out of Scope

Document relevant adjacent work intentionally not included. Examples:

```
Dev KMS posture remains a later cost/security decision.
Runtime migration is not part of this PR.
Foundation boundary parameterization remains separate work.
```

Do not use this section for unrelated ideas.

### Verification

Mandatory for substantive code changes. Prefer a table:

```
| Check | Result |
|---|---|
| `make check` | PASS: 553 checks |
| `make acceptance-local` | PASS |
| IAM contract tests | 114/114 PASS |
| `git diff --check` | clean |
| GitHub CI | 10/10 successful |
```

Include important behavioral proofs separately when useful. Avoid vague statements such as "Tests pass."

### Live Effects

Required for infrastructure, deployments, external systems, accounts, databases, or data-changing PRs. Preferred format:

```
| Surface | Effect |
|---|---|
| AWS resources | No change |
| GitHub settings | No change |
| Runtime | Not recreated |
| Database | Not enabled |
| Images | Not pushed |
```

Adapt surfaces to the project. Do not include irrelevant rows to fill the table.

### Rollback

Include when rollback is not obvious. Either a one-liner:

```
Git revert; no live migration involved.
```

or the ordered steps for a migration.

### Merge Readiness

Use for controlled or high-rigor workflows. Recommended:

```
- Exact head reviewed: `<SHA>`
- CI: PASS
- Recommended for merge: **Yes**
- Remaining blocker: None
```

Do not claim readiness without evidence.

## 5. Style rules

- **Evidence over confidence.** Write `make acceptance-local: PASS`, not "This should work."
- **Root cause over symptom.** Explain why the issue existed.
- **Outcomes over file lists.** Files belong in the diff. The PR body explains behavior.
- **Preserved invariants matter.** State important non-changes explicitly.
- **Intentional deferral is not omission.** State relevant deferred work.
- **Code-only is not live.** Never conflate implemented, tested, deployed, and live-verified.
- **Historical context is not current state.** Label it as history.
- **Tables where comparison improves readability.** Use prose when a table would add ceremony rather than clarity.
- **No artificial verbosity.** A PR should contain enough evidence to make a merge decision, not reproduce the implementation.

## 6. Guidance for coding agents

When an agent creates or updates a PR:

1. Read the diff and tests before writing the description.
2. Do not copy the task prompt into the PR.
3. Document verified final behavior, not intended behavior.
4. Distinguish findings from fixes.
5. Include exact validation results.
6. Include live effects for infrastructure and external actions.
7. Identify cross-repository prerequisites.
8. Remove sections that are not applicable.
9. Do not claim CI success until CI has actually completed.
10. When updating an existing PR after corrections, update the body so it describes the final head, not the original implementation.

## 7. Project overrides

The shared template is the default. A repository may define its own `PULL_REQUEST_TEMPLATE.md` when it has legitimate project-specific requirements. Repository-specific templates take precedence over the account default.

A project override should generally preserve the same core concepts unless there is a reason not to:

- Summary
- Root cause / changes
- Impact
- Verification
- Live effects
