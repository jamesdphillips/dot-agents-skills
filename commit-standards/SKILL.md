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
- Do not use `--no-verify`. If checks fail, fix and retry.

## Message Layout

- Subject
- Blank line
- Body (if needed)
- Blank line
- Optional trailers (`Token: Value`, one per line)

## Subject Line

- Use imperative mood (`add`, `fix`, `refactor`), not past tense.
- Target `<= 50` chars. Hard cap `<= 72`.
- No trailing period.

## Conditional Inclusion

- Include only sections that add decision or verification value.
- Omit empty or non-applicable sections; do not leave placeholder bullets.

## Minimal Body (Trivial Changes)

Use when the diff is very small and intent is obvious:

```text
Changes:
- ...

Why:
- ...
```

## Non-Trivial Body

For non-trivial changes, include:
- `Changes`
- `Why`
- `Assumptions`

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
- `Alternatives considered`
- `Context/history`
- `Abandoned approaches`

## Suggested Body Template

```text
Changes:
- ...

Why:
- ...

Assumptions:
- ...

Alternatives considered:
- ...

Context/history:
- ...

Abandoned approaches:
- ...
```
