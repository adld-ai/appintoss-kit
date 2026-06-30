# Guide Resolver

This file resolves a task type to the exact guide files and verification gate
that must be used. It is the canonical routing table for this workspace.

## Resolver Contract

For every task:

1. Start with `ALWAYS`.
2. Add every route whose trigger matches the user request or planned work.
3. Read all resolved files before acting.
4. Use the strictest resolved verification gate.
5. If the route is ambiguous, resolve more files, not fewer.

## ALWAYS

Always read:

- `AGENTS.md`
- `guide/agent-operating-rules.md`
- `guide/development-verification-loop.md`
- Project `PRD.md`, if present
- Project-level `AGENTS.md`, if present

Gate:

- Evidence before claims.
- No completion claim without fresh verification output.
- If a command cannot be run, report the exact missing command, blocker, and
  residual risk.

## Route Table

| Route | Trigger | Required files | Verification gate |
|---|---|---|---|
| `DEVELOPMENT_IMPLEMENTATION` | Writing, changing, debugging, refactoring, or reviewing code | `guide/development.md`, `guide/development-verification-loop.md` | Focused check first, then build or E2E when user-visible behavior changes |
| `DESIGN_UI` | UI layout, UX writing, visual styling, accessibility, product flow, onboarding, trust, or high-cognitive-load behavior | `guide/design-system.md`, `guide/development-verification-loop.md` | Adversarial design verification must pass before moving on |
| `ASSETS_SUBMISSION` | Logo, dark logo, thumbnail, screenshots, `.ait` bundle placement, `public/`, or `submission/` files | `guide/assets.md`, `guide/design-system.md`, `guide/development-verification-loop.md` | Exact dimensions, canonical paths, public/submission mirroring, and real-app screenshot provenance |
| `CONSOLE_CREATION` | Creating an app in the console, choosing appName, Korean name, English name, or app type | `guide/console-registration.md`, `guide/policy-and-categories.md`, `guide/submission-metadata.md` | Service policy check plus required naming/SEO subagents before console copy |
| `SUBMISSION_METADATA` | `submission/inputs.md`, exposure info, release memo, subtitle, detailed description, keywords, support email, age rating | `guide/submission-metadata.md`, `guide/policy-and-categories.md`, `guide/assets.md` | Copy must match implemented behavior and every console field must be reported |
| `POLICY_CATEGORY` | App ideation, category selection, restricted-service review, medical/financial/shopping/education policy risk | `guide/policy-and-categories.md` | Current official service policy must be checked before proposing or submitting |
| `PUSH_CHALLENGE` | Push notifications, 스마트 발송, 바이브코딩 챌린지 | `guide/push-and-challenge.md`, `guide/policy-and-categories.md` | Human review and deadline constraints must be surfaced before planning |
| `AGENT_RULES` | Creating, editing, or reviewing `AGENTS.md`, `guide/*.md`, `.agents/**`, `.claude`, local skills, subagents, or hooks | `guide/agent-operating-rules.md`, `guide/resolver.md`, `guide/development-verification-loop.md`, `.agents/README.md`, `.agents/hooks/README.md` | Link/path scan plus behavior-rule keyword scan before claiming complete |

## Verification Resolver

Resolve verification in this order:

1. **Documentation-only changes**
   - Verify all referenced guide paths exist.
   - Verify required keywords for the changed rule exist.
   - Verify forbidden source names or deprecated phrasing do not appear.

2. **Code changes without visible UI**
   - Run the narrowest relevant test or typecheck.
   - Run `npm run lint` and `npm run build` if available.

3. **Visible UI or user-flow changes**
   - Run static/build checks.
   - Run E2E if available.
   - If no E2E setup exists, run browser automation against the local app and
     report URL, viewport, scenario, and result.
   - Run adversarial design verification from `guide/design-system.md`.

4. **Submission or asset changes**
   - Verify dimensions and paths.
   - Verify files are mirrored between `public/` and `submission/`.
   - Verify screenshots come from the real running app.
   - Verify metadata copy does not claim unsupported behavior.

## Failure Resolver

If any verification fails:

```text
fail
-> stop expansion
-> capture command and output
-> identify root cause
-> replan smallest fix
-> fix only root cause
-> rerun the same failing check
-> rerun broader resolved checks
-> only then move forward
```

Use the root-cause template in
`guide/development-verification-loop.md`.
