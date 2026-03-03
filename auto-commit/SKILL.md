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
- Never create empty/no-op commits.

## Discrete Change

- One commit per intent.
- Keep separable work separate.
- Never mix unrelated intents.

## Commit Workflow

1. Pick the next discrete change.
2. Implement only that scope.
3. Run at least one check: targeted test, lint/typecheck, or build.
4. If checks fail, do not commit; fix issues and rerun checks.
5. If no formal check exists, run fallback sanity checks in order: targeted run, focused build/lint, static inspection. Note the limit.
6. Stage only scoped files (`git add <path...>`).
7. If one file has mixed intents, split edits or use partial staging (`git add -p`).
8. Keep dependency-first commit order (prerequisites before dependents).
9. If nothing is staged for this scope, stop; do not commit.
10. Commit with an intent-specific message.
11. If hooks fail, fix and retry. Do not bypass hooks unless the user explicitly asks.
12. Repeat.

## Guardrails

- Avoid broad staging.
- Never include unrelated dirty-tree changes.
- If unrelated files are staged, unstage them (`git restore --staged <path...>`) or commit only explicitly staged scoped paths.
- Do not defer all commits to the end once validated units exist.

## Overrides and Exceptions

- Follow explicit user overrides to commit strategy.
- Allow exceptions only for narrow emergency constraints.
- Document exception justification in the commit body.
- Return to atomic commits and add cleanup commits when feasible.

## Message Quality

Keep messages concise and scoped. Reuse `commit-standards` for body detail when needed.
