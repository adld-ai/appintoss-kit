# Apps in Toss Guide Index

This directory is resolved through [`resolver.md`](resolver.md). Do not choose
guide files by preference; choose them by route.

## Required Resolver

Start with:

1. Root `AGENTS.md`
2. [`resolver.md`](resolver.md)
3. The route-specific files resolved by `resolver.md`

## Guide Files

| File | Responsibility |
|---|---|
| [`resolver.md`](resolver.md) | Maps task types to required guide files and verification gates |
| [`agent-operating-rules.md`](agent-operating-rules.md) | Agent style, PRD rule, inheritance, skill expectations, browser cleanup |
| [`development-verification-loop.md`](development-verification-loop.md) | Develop -> adversarial verify -> E2E -> root-cause/replan loop |
| [`design-system.md`](design-system.md) | Toss visual system, product design, UX writing, accessibility, design verifier |
| [`development.md`](development.md) | Scaffold, SDK APIs, browser testing, build/deploy commands |
| [`console-registration.md`](console-registration.md) | Console app creation fields and naming/SEO subagent requirements |
| [`submission-metadata.md`](submission-metadata.md) | Console metadata, `submission/inputs.md`, release memo copy rules |
| [`assets.md`](assets.md) | Image generation, icons, thumbnails, screenshots, file organization |
| [`policy-and-categories.md`](policy-and-categories.md) | Service policy, platform constraints, category tree |
| [`push-and-challenge.md`](push-and-challenge.md) | Push notification constraints and challenge submission |

## Resolver Principle

If a task touches multiple domains, resolve all matching routes and obey the
strictest verification gate. For example, a UI change that also updates
screenshots resolves `DESIGN_UI`, `DEVELOPMENT_IMPLEMENTATION`, and
`ASSETS_SUBMISSION`.
