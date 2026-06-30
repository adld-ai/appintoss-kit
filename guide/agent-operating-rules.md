# Agent Operating Rules

## Core Working Style

- Research the codebase before editing. Never change code you have not read.
- Prefer the smallest correct change that satisfies the request.
- Match the existing project style, even when you would choose a different
  style in a new project.
- Do not refactor, reformat, rename, or clean adjacent code unless it is
  required for the task.
- Surface uncertainty early. If the request has multiple valid meanings or a
  risky assumption, name the assumption before acting.
- Push back when a simpler, safer, or more maintainable approach is clearly
  better.

## Project Context

- At the start of work in any project, always check for `PRD.md` in the project
  root and read it first.
- Treat `PRD.md` as the source of truth for scope, decisions, and requirements.
- Keep the implementation aligned with the PRD and the task-specific guide
  files under `guide/`.

## Instruction Inheritance

- At the start of work in any mini-app project under this directory, make sure
  that project has its own `AGENTS.md`.
- Each project-level `AGENTS.md` must explicitly tell agents to read and follow
  `/Users/tonylee/abld/Product/app-in-toss/AGENTS.md` first, then apply any
  project-specific rules.
- If the project-level `AGENTS.md` is missing, create it before making project
  changes.

## Karpathy Guidelines

Use the `karpathy-guidelines` skill for coding work. Its standing rules are:

- Think before coding: state important assumptions and ask when ambiguity would
  materially change the solution.
- Simplicity first: avoid speculative features, one-off abstractions, and
  configurability that was not requested.
- Surgical changes: touch only the files and code paths required, and clean up
  only artifacts introduced by your own change.
- Goal-driven execution: define verifiable success, run focused validation, and
  report any checks that could not be run.

## Browser Automation Cleanup

When `.claude`, `.codex`, or `.opencode` agents open an `agent-browser`,
Playwright, or similar browser automation session, they must close or kill that
browser session before finishing the task.
