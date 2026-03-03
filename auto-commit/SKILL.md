---
name: auto-commit
description: Auto-create git commits during code-change tasks. Commit each validated discrete change immediately (one intent per commit) without waiting for a commit prompt. Use for features, fixes, refactors, and cleanup with scoped staging.
---

# Auto Commit

Commit during implementation, not after a separate prompt.

## Policy

- Default to auto-commit for code changes.
- Finish one discrete change at a time.
- Commit immediately after validation.
- Do not wait for a follow-up commit request.

## Discrete Change

- One commit per intent.
- Keep separable work separate.
- Never mix unrelated intents.

## Commit Workflow

1. Pick the next discrete change.
2. Implement only that scope.
3. Run relevant checks.
4. Stage only scoped files (`git add <path...>`).
5. Commit with an intent-specific message.
6. Repeat.

## Guardrails

- Avoid broad staging.
- Never include unrelated dirty-tree changes.
- If unrelated files are staged, unstage them or bypass them in scoped staging.
- Do not defer all commits to the end once validated units exist.

## Overrides and Exceptions

- Follow explicit user overrides to commit strategy.
- Allow exceptions only for narrow emergency constraints.
- Document exception justification in the commit body.
- Return to atomic commits and add cleanup commits when feasible.

## Message Quality

Keep messages concise and scoped. Reuse `commit-standards` for body detail when needed.
