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

## Subject Line

- Use imperative mood (`add`, `fix`, `refactor`), not past tense.
- Keep subject concise (target `<= 72` chars).

## Required Body Content

Include:
- What changed (key files/behavior).
- Why this approach was chosen.
- Assumptions that affect correctness.

## Recommended Body Content

Add when relevant:
- Alternatives considered and rejection reason.
- Relevant context/history.
- Request summary (original prompt).
- Abandoned approaches and why.

## Conditional Inclusion

- Include only sections that add decision or verification value.
- Omit empty or non-applicable sections; do not leave placeholder bullets.
- For tiny/self-evident changes, use the minimal body format below.

## Minimal Body (Trivial Changes)

Use this when the diff is very small and intent is obvious:

```text
Changes:
- ...

Why:
- ...
```

## If The Commit Solves An Issue

Also include:
- Problem statement.
- Assumptions during diagnosis/fix.
- Repro steps (if known/relevant).
- Validation steps and evidence of fix.

## Style

- Use short sections with clear labels.
- Prefer concrete nouns, filenames, commands, and outcomes.
- Avoid filler, repetition, and long prose.
- Keep scope aligned with the diff.

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

## Suggested Issue-Fix Addendum

```text
Problem:
- ...

Reproduction:
- ...

Validation:
- `command`: ...
- `expected`: ...
- `actual`: ...
```
