# Workspace Agent Setup

`.agents` is the canonical agent configuration directory for this workspace.
`.claude` is a symlink to this directory so Claude-compatible agents resolve the
same skills, subagents, hooks, and references.

## Structure

```text
.agents/
  agents/       # read-only or delegated subagent definitions
  assets/       # images or static assets used by agent documentation
  hooks/        # lifecycle hook rules for the development loop
  references/   # large non-skill reference material
  scripts/      # optional helper scripts
  skills/       # native skill directories; each skill has SKILL.md
```

## Resolver Rule

All agents start from root `AGENTS.md`, then resolve task routes through
`guide/resolver.md`. If a task touches multiple domains, resolve every matching
route and follow the strictest verification gate.

## Skill Directory Rule

Only directories with `SKILL.md` belong under `.agents/skills/`. Large markdown
references belong under `.agents/references/` and should be loaded only when a
resolved guide or skill asks for them.

## Subagents

Subagents live under `.agents/agents/<name>/AGENT.md`.

Current subagents:

- `adversarial-reviewer`: read-only gatekeeper for pre-build and pre-submit
  review.

## Hooks

Hooks live under `.agents/hooks/`. They describe required lifecycle gates for
agents that support hook-style execution.
