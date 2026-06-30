# Toss Design System Rules

All mini-apps under this directory must use the Toss design system color palette
in their UI components and brand identity. Apply the theme consistently across
`granite.config.ts` (`primaryColor`) and every inline style in `src/App.tsx`.
The goal is not to copy Toss screens or branding; build small, trustworthy,
task-focused mini-apps that feel compatible with the Apps in Toss environment
while keeping their own app identity.

## Product Design Operating Rules

Treat design as the structure of the task, not surface decoration.

- Define the real blockage before changing screens. Ask where the user stops,
  what they must remember, and what decision feels risky.
- Break large flows into action units such as choose date, add item, confirm
  state, edit value, delete value, or recover from error.
- For each action, decide whether to keep, remove, automate, or assist it.
  Prefer fewer choices, fewer inputs, and clearer next actions.
- Start with the smallest change that can improve completion, trust, or
  comprehension. Avoid broad redesigns when one flow or message is the issue.
- Promote repeated fixes into reusable components, copy patterns, helpers, or
  validation rules instead of one-off screen tweaks.
- Judge success with task metrics: completion rate, time to complete, error
  rate, re-entry rate, search time, support burden, and user confidence.

## Component Color Theme

Use these exact hex values as the canonical Toss theme tokens. Do not mix in
non-Toss colors such as Material `#4CAF50` or generic grays like `#80848B`.

| Role | Token value | Notes |
|---|---|---|
| Primary / accent | `#3182f6` | Toss blue. Buttons, active states, highlights. |
| Primary tint bg | `#e8f3ff` | Light blue chip / icon background. |
| Text primary | `#191f28` | Headings, primary labels. |
| Text secondary | `#6b7684` | Captions, helper text. |
| Background | `#f2f4f6` | Page background. |
| Border / divider | `#e5e8eb` | Hairlines, inactive toggle borders. |
| Success | `#03b26c` | Taken / done check. |
| Success tint bg | `#f0faf6` | Light green icon background. |
| Danger | `#f04452` | Delete / destructive actions. |
| CTA black | `#191f28` | Primary CTA button background. |

## Migration Map

When restyling an app that used a default orange/gray theme, apply this mapping
to every inline style:

| Old value | New value |
|---|---|
| `#FD9B3C` | `#3182f6` |
| `#FFF3E0` | `#e8f3ff` |
| `#E85D04` | `#3182f6` |
| `#1B1C1E` | `#191f28` |
| `#80848B` | `#6b7684` |
| `#F4F5F7` | `#f2f4f6` |
| `#D6D8DB` | `#e5e8eb` |
| `#F0F1F3` | `#e5e8eb` |
| `#4CAF50` | `#03b26c` |
| `#E8F5E9` | `#f0faf6` |
| `#E5484D` | `#f04452` |

## UI Layout and Interaction

- Prefer dense, calm, task-first screens over marketing-style hero layouts
  inside the app.
- Make the primary action obvious, stable, and reachable. Secondary actions
  should not compete with it.
- Use cards for repeated items, modals, and framed tools only. Do not nest
  cards inside cards or turn every section into a floating card.
- Design empty, loading, success, error, edit, delete, and undo states when the
  flow can naturally reach them.
- Keep state changes visible. A user should know what changed after a tap
  without reading instructions.
- Use motion and illustration only when they improve recognition, progress, or
  confidence. Decorative effects must not reduce clarity.

## UX Writing and Trust

- Write copy as part of the system, not as decoration. Reuse patterns for
  headings, empty states, helper text, errors, and confirmations.
- Use concrete, action-oriented Korean. Prefer friendly `~해요` / `~아요`
  endings for user-facing copy unless the app has a stronger reason not to.
- Explain the outcome of actions before asking users to confirm destructive,
  sensitive, paid, or irreversible operations.
- Avoid pressure tactics, exaggerated claims, fake urgency, or wording that
  hides risk. Trust has priority over conversion.
- Keep submission copy aligned with implemented behavior. Do not describe
  features, data sources, automations, medical value, financial value, or AI
  behavior that the app does not actually provide.

## Accessibility and Inclusion

Accessibility is task success, not a checklist.

- Check whether a user can complete the main flow with readable text, clear
  hierarchy, visible focus/pressed states, and non-color-only status cues.
- Ensure text does not overlap or shrink into unreadability on mobile.
- Use sufficient contrast with the canonical palette. Do not solve contrast
  problems by introducing non-theme colors.
- Preserve logical reading order for screen readers and keyboard navigation
  where the implementation supports it.
- Design for first-time users, older users, and users under time pressure by
  reducing memory load and making recovery paths obvious.

## Adversarial Design Verification

Before accepting any UI, copy, or asset change, try to reject it using this
checklist. If any item fails, return to the development loop in
[`development-verification-loop.md`](development-verification-loop.md), identify
the root cause, replan the smallest fix, and rerun verification.

- Main task: the user can identify the next action without explanation.
- Action count: every input, step, and confirmation is necessary or assisted.
- State coverage: empty, loading, success, error, edit, delete, and recovery
  states are handled when the flow can reach them.
- Trust: copy is concrete, truthful, non-pressuring, and aligned with
  implemented behavior.
- Accessibility: status is not communicated by color alone, text is readable,
  and layout does not overlap on mobile or desktop.
- Theme: `granite.config.ts` and `src/App.tsx` use only the approved palette.
- Assets: logos, thumbnails, and screenshots follow [`assets.md`](assets.md).

## Validation Scans

```bash
rg '#FD9B3C|#FFF3E0|#E85D04|#80848B|#F4F5F7|#D6D8DB|#F0F1F3|#4CAF50|#E8F5E9|#E5484D' src/App.tsx granite.config.ts
rg '#[0-9A-Fa-f]{6}' src/App.tsx granite.config.ts
```
