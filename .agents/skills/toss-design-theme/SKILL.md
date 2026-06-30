---
name: toss-design-theme
description: >
  Use when building, restyling, reviewing, or preparing submission assets for a
  mini-app under /Users/tonylee/abld/Product/app-in-toss, especially when UI
  colors, app logos, thumbnails, UX writing, accessibility, trust, onboarding,
  repeated actions, or high-cognitive-load flows are involved.
---

# Toss Design Theme Skill

This skill resolves to the workspace-native design rules. Do not duplicate or
reinterpret the rules here.

## Required Reads

Before UI, copy, logo, thumbnail, screenshot, or store-asset work, read:

1. `/Users/tonylee/abld/Product/app-in-toss/AGENTS.md`
2. `/Users/tonylee/abld/Product/app-in-toss/guide/resolver.md`
3. Resolve `DESIGN_UI`.
4. If assets are involved, also resolve `ASSETS_SUBMISSION`.
5. If code or browser behavior is involved, also resolve
   `DEVELOPMENT_IMPLEMENTATION`.

## Required Execution Rule

Apply the loop from `guide/development-verification-loop.md`:

```text
develop
-> verify with adversarial verifier as a design rule
-> run focused checks and E2E
-> if E2E fails: capture evidence, find root cause, replan, fix, rerun
-> if checks pass: move to the next step
```

## Minimum Design Gate

Use the `DESIGN_UI` route from `guide/resolver.md`. It resolves
`guide/design-system.md` as the source of truth for:

- Toss palette and forbidden old-theme colors
- product design operating rules
- UI layout and interaction
- UX writing and trust
- accessibility and inclusion
- logo, thumbnail, and dark-mode asset design constraints

Use the `ASSETS_SUBMISSION` route from `guide/resolver.md` for generated raster
assets, screenshots, file organization, and submission mirroring.
