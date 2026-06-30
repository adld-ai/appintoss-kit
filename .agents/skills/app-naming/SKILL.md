---
name: app-naming
description: >
  Use as a subagent when creating or renaming an 앱인토스 mini-app. Generates
  Korean and English app names that clearly communicate the app's function or
  category while keeping a rhythmic, memorable cadence. Always trigger this
  subagent as a script step during app creation before filling the console
  "앱 만들기" modal.
---

# App Naming Subagent

This subagent is triggered as a script step during app creation. Resolve
`CONSOLE_CREATION` through `/Users/tonylee/abld/Product/app-in-toss/guide/resolver.md`
before using it. It produces the Korean display name, English app name, and
appName for a new mini-app.

## Naming principles

1. **Clear function or category first** — The name must tell the user what the
   app does at a glance. A user reading only the name should infer the app's
   core function or category without reading the description.
   - Good: `알약 타이머` (pill + timer → function is obvious)
   - Good: `반찬냉장고` (side-dish + fridge → category is obvious)
   - Bad: `마이도우` (no function or category signal)

2. **Rhythm and memorability** — After clarity, add a rhythmic cadence that
   makes the name stick. Korean names benefit from reduplication, two-beat
   structures, or playful onomatopoeia/mimetic words that still carry meaning.
   - Good: `빨래빨래` (reduplication + laundry = rhythmic + clear)
   - Good: `버려버려` (reduplication + throw-away = rhythmic + clear)
   - Good: `챙겨챙겨` (reduplication + pack/prepare = rhythmic + clear)
   - Good: `택배왔나` (question rhythm + parcel = memorable + clear)
   - Good: `톡톡요금` (onomatopoeia + fare = rhythmic + clear)
   - Bad: `복용관리도우미` (no rhythm, generic helper suffix)

3. **Korean name constraints**:
   - Must be ≤ 10 characters (console limit).
   - Must be a real Korean word or natural compound, not machine-concatenated
     fragments.

4. **English name constraints**:
   - Must be ≤ 15 characters (console limit).
   - Follow `단어의 첫 글자만 대문자로 작성해 주세요.` — capitalize only the
     first letter of each word, space-separated, no camelCase.
   - Should be a clear calque or natural English equivalent of the Korean
     name, not a literal transliteration.

5. **appName constraints**:
   - Lowercase kebab-case, must match `granite.config.ts` exactly.
   - Derived from the English name or core function (e.g. `pill-timer`,
     `bag-check`, `trash-schedule`).

## Subagent input

The calling agent must provide:

- App function description (1-2 sentences in Korean)
- Core object or action (e.g. pill, receipt, trash, laundry)
- Target category path (e.g. `생활 > 건강 > 건강 관리`)

## Subagent output

Return exactly three values:

```
Korean app name: <korean name>
English app name: <english name>
appName: <kebab-case id>
```

Plus a one-line rationale explaining how the name balances clarity and rhythm.

## Examples (existing apps in this workspace)

| appName         | Korean        | English       | Clarity signal    | Rhythm device        |
|-----------------|---------------|---------------|-------------------|----------------------|
| pill-timer      | 알약 타이머    | Pill Timer    | pill + timer      | two-beat compound    |
| bag-check       | 챙겨챙겨       | Bag Check     | pack/prepare      | reduplication        |
| banchan-mate    | 반찬냉장고     | Fridge Mate   | side-dish + fridge| compound noun        |
| fare-calc       | 톡톡요금       | Fare Calc     | fare              | onomatopoeia prefix  |
| laundry-log     | 빨래빨래       | Laundry Log   | laundry           | reduplication        |
| menu-picker     | 냠냠           | Menu Pick     | eating            | mimetic reduplication|
| parcel-log      | 택배왔나       | Parcel Log    | parcel            | question rhythm      |
| receipt-snap    | 영수증쿡       | Receipt Snap  | receipt           | slang suffix         |
| sub-tracker     | 구독알림       | Sub Tracker   | subscription      | compound noun        |
| trash-schedule  | 버려버려       | Trash Guide   | throw-away        | reduplication        |
