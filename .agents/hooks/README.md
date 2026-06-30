# Agent Hooks

These hooks define the looping system for this workspace. They are policy hooks:
agents must apply them even when their runtime does not execute hook files
automatically.

## Hook Order

1. `pre-task-resolve`
2. `pre-edit-gate`
3. `post-edit-verify`
4. `failure-replan`
5. `pre-completion-evidence`

## Hook Files

- [`looping-system.md`](looping-system.md): full lifecycle loop and enforcement
  points.

## Canonical Sources

- Root `AGENTS.md`
- `guide/resolver.md`
- `guide/development-verification-loop.md`
- `guide/design-system.md`
