---
name: commit-standards
description: Draft terse, factual commit messages with explicit what/why/assumptions and issue-fix validation evidence.
---

# Commit Standards

Use for drafting, revising, or reviewing commit messages.

## Goals

- Be terse. No byte is gratis—only the Via Dolorosa.
- Optimize for human and agent readers.
- Keep claims factual and specific.
- Do not use `--no-verify`. If checks fail, fix and retry ([Git Commit Docs]).

## Message Layout

- Subject
- Blank line
- Body (if needed)
- Blank line
- Optional trailers (`Token: Value`, one per line) ([Git Trailer Parser])[^trailers]

## Subject Line

- Use imperative mood (`add`, `fix`, `refactor`), not past tense.
- Target `<= 50` chars. Hard cap `<= 72` ([Kubernetes PR Guide], [Submitting Patches]).[^subject]
- No trailing period.
- Keep the subject focused on the action; move nuance, rationale, and constraints to the body.

## Conditional Inclusion

- Include only sections that add decision or verification value.
- Omit empty or non-applicable sections; do not leave placeholder bullets.

## Body Requirements

Use `Changes` and `Why` for all commits with a body ([Submitting Patches]).[^what-why]

Use Title Case for section headers (for example, `Changes`, `Why`, `Assumptions`).

`Assumptions` is required whenever behavior depends on context not obvious in the diff; include all such assumptions for auditability ([Submitting Patches]).[^assumptions]

`Validation` is recommended for any commit with testable outcomes, even when the commit is not framed as an issue-fix.

For trivial changes, keep the body minimal:

```text
Changes:
- ...

Why:
- ...
```

## Issue-Fix Body

If the commit solves an issue, include:
- `Problem`
- `Validation`
- `Reproduction` (when known/relevant)

Use structured validation evidence:

```text
Validation:
- `command`: ...
- `expected`: ...
- `actual`: ...
```

## Recommended Sections

Add only when they add decision value:
- `Alternatives Considered`
- `Context/History`
- `Abandoned Approaches`

## Suggested Body Template

```text
Changes:
- ...

Why:
- ...

Assumptions:
- ...

Alternatives Considered:
- ...

Context/History:
- ...

Abandoned Approaches:
- ...
```

## Issue Link Semantics

- Use `Refs: <id>` for non-closing linkage/context ([GitHub Issue Linking]).[^issue-link]
- Use `Fixes: <id>` only when closure is intended ([GitHub Issue Linking]).[^issue-link]

## Optional Trailers

- Trailers are optional. If used, keep them machine-parseable (`Token: Value`) ([Git Trailer Parser]).[^trailers]
- Keep one trailer per line.
- Common trailers:
  - `Refs: #123`
  - `Fixes: #123`
  - `Signed-off-by: Name <email>`
  - `Prompted-by: ...`
  - `Generated-by: ...`

## Footnotes

[^subject]: Subject-length guidance improves scanability in logs and review tools ([Kubernetes PR Guide], [Submitting Patches]).
[^what-why]: Recording both what changed and why preserves durable decision context ([Submitting Patches]).
[^assumptions]: Explicit assumptions improve auditability when context is not obvious in the diff ([Submitting Patches]).
[^trailers]: Trailer format is chosen for parser compatibility and automation ([Git Trailer Parser]).
[^issue-link]: `Refs` vs `Fixes` semantics follow GitHub auto-linking and auto-closing behavior ([GitHub Issue Linking]).

[Git Commit Docs]: https://git-scm.com/docs/git-commit
[Submitting Patches]: https://www.kernel.org/pub/software/scm/git/docs/SubmittingPatches.html
[Git Trailer Parser]: https://git-scm.com/docs/git-interpret-trailers
[GitHub Issue Linking]: https://docs.github.com/en/issues/tracking-your-work-with-issues/using-issues/linking-a-pull-request-to-an-issue
[Kubernetes PR Guide]: https://www.kubernetes.dev/docs/guide/pull-requests/
