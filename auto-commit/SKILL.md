---
name: auto-commit
description: Automatically create git commits during code-change tasks by committing each validated discrete change as soon as it is complete. Use when implementing features, fixes, refactors, or cleanup so the agent does not wait for a separate commit prompt, while enforcing atomic commit boundaries and scoped staging.
---

# Auto Commit

Execute work in discrete changes and commit each one immediately after validation.

## Required Policy

- Treat auto-commit as the default behavior for code-change tasks.
- Complete one discrete change at a time.
- Run relevant validation for the current change before committing.
- Create the commit immediately after validation passes.
- Do not wait for an additional user prompt to commit.

## Define Discrete Change

Use one commit for one intent.

Examples:
- Add a feature endpoint and its tests.
- Fix one bug and add regression coverage.
- Perform a pure rename/refactor with no behavior changes.
- Apply formatting-only updates.

Do not combine unrelated intents in one commit.

## Commit Workflow

1. Identify the next discrete change.
2. Implement only that change.
3. Run relevant checks for that scope.
4. Stage only files for that change.
5. Commit with an intent-specific message.
6. Repeat for the next discrete change.

## Staging Guardrails

- Prefer explicit path staging (`git add <path...>`).
- Do not use broad staging that risks unrelated files.
- Never include unrelated dirty working tree changes.
- If unrelated staged changes exist, unstage or bypass them and commit only scoped files.

## Disallowed Patterns

- Combining feature behavior changes and unrelated refactors in one commit.
- Mixing formatting-only changes with logic changes when separable.
- Deferring all commits until the end when discrete validated units already exist.

## Overrides and Exceptions

- If the user explicitly requests a different commit strategy, follow the user request.
- Allow exceptions only for narrow emergency constraints (for example, urgent hotfix sequencing).
- When using an exception, document justification in the commit body.
- After the emergency path, return to atomic commits and add follow-up normalization commits when feasible.

## Commit Message Quality

Keep commit messages concise and specific to the scoped intent. Reuse `commit-standards` expectations for message body quality when additional detail is needed.
