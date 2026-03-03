---
name: commit-standards
description: Draft concise, factual commit messages with required rationale, assumptions, and issue-fix validation details.
---

# Commit Standards

Use for drafting, revising, or reviewing commit messages.

## Goals

- Be terse; every line must earn tokens.
- Optimize for human and agent readers.
- Keep claims factual and specific.
- Do not use `--no-verify`. If checks fail, fix and retry.

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
- ...
```
