# Apps in Toss - Agent Resolver

This file is the resolver entrypoint for every agent working under
`/Users/tonylee/abld/Product/app-in-toss`.

## Resolution Algorithm

Before any project change:

1. Read this file.
2. If the current project has `PRD.md`, read it and treat it as the scope
   source of truth.
3. Read [`guide/resolver.md`](guide/resolver.md).
4. Resolve the task type against the route table in `guide/resolver.md`.
5. Read every resolved guide file before editing, generating assets, writing
   console copy, selecting categories, or claiming verification.
6. Apply the resolved verification gate. If multiple routes match, use the
   union of all required files and the strictest gate.

## Always-Resolved Rules

Every task resolves these files:

- [`guide/agent-operating-rules.md`](guide/agent-operating-rules.md)
- [`guide/development-verification-loop.md`](guide/development-verification-loop.md)

For coding, debugging, refactoring, reviewing, or documentation that changes
agent behavior, also apply the local `karpathy-guidelines` skill.

## Required Development Gate

All implementation work resolves to the loop in
[`guide/development-verification-loop.md`](guide/development-verification-loop.md):

```text
develop
-> verify with adversarial verifier as a design rule
-> run focused checks and E2E
-> if E2E fails: stop, capture evidence, find root cause, replan, fix, rerun
-> if checks pass: move to the next step
```

Do not claim completion, correctness, readiness, or submission safety until the
fresh verification evidence required by the resolved route has been read.

## Quick Resolver

Use the full route table in [`guide/resolver.md`](guide/resolver.md). This
summary exists only to orient the first decision:

| If the task is about | Resolve through |
|---|---|
| UI, UX writing, visual design, accessibility | `DESIGN_UI` |
| Logo, dark logo, thumbnail, screenshot, bundle files | `ASSETS_SUBMISSION` |
| Code, debugging, browser behavior, E2E, build | `DEVELOPMENT_IMPLEMENTATION` |
| App creation, naming, console modal | `CONSOLE_CREATION` |
| `submission/inputs.md`, release copy, exposure fields | `SUBMISSION_METADATA` |
| Category choice, service policy, restricted concepts | `POLICY_CATEGORY` |
| Push notifications or challenge submission | `PUSH_CHALLENGE` |
| `.agents`, `.claude`, skills, subagents, hooks, guide rules | `AGENT_RULES` |

## Instruction Inheritance

- At the start of work in any mini-app project under this directory, make sure
  that project has its own `AGENTS.md`.
- Each project-level `AGENTS.md` must explicitly tell agents to read and follow
  `/Users/tonylee/abld/Product/app-in-toss/AGENTS.md` first, then apply any
  project-specific rules.
- If the project-level `AGENTS.md` is missing, create it before making project
  changes.
