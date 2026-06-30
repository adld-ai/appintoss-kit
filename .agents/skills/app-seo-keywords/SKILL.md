---
name: app-seo-keywords
description: >
  Use as a subagent when creating or submitting an 앱인토스 mini-app. Generates
  SEO-optimized app search keywords tailored to the product's function and
  target user intent. Always trigger this subagent as a script step during app
  creation before filling the console exposure information.
---

# App SEO Keywords Subagent

This subagent is triggered as a script step during app creation. Resolve
`CONSOLE_CREATION` through `/Users/tonylee/abld/Product/app-in-toss/guide/resolver.md`
before using it. It produces the app search keyword list for the Toss console
exposure information.

## SEO principles for 앱인토스 search keywords

1. **User search intent first** — Pick keywords that real users would type
   when looking for this app's function, not keywords that describe the app
   internally. Think "what would I search if I needed this?"

2. **Concrete nouns and task words** — Prefer concrete nouns (알약, 영수증,
   택배) and task verbs (복용, 기록, 계산) over abstract marketing terms
   (관리, 도우미, 플러스). Avoid unsupported claims (최고, 1위, 무료).

3. **Category-aligned terms** — Include at least one keyword that maps to the
   app's console category path so search and category browse reinforce each
   other.
   - Example: a `생활 > 건강 > 건강 관리` app should include `건강` as a
     keyword.

4. **Colloquial and long-tail variants** — Mix short head terms (약, 세탁)
   with colloquial phrases users actually type (오늘뭐먹지, 놓고감,
   깜빡). Long-tail colloquial terms have less competition and higher
   conversion.

5. **No duplicates across meaning** — Each keyword should cover a distinct
   search intent. Do not list near-synonyms that cannibalize each other
   (e.g. both `지출관리` and `지출` — pick the stronger one).

6. **7-10 keywords** — The console expects a focused list. Aim for 7-10
   keywords, each 1-7 Korean characters.

## Subagent input

The calling agent must provide:

- App function description (1-2 sentences in Korean)
- Korean app name and English app name
- Category path (e.g. `생활 > 건강 > 건강 관리`)
- Core user task (e.g. "check if I took my pill", "find what to cook with
  leftover ingredients")

## Subagent output

Return keywords as a `-` bullet list, one keyword per line:

```
- <keyword 1>
- <keyword 2>
...
```

Plus a one-line rationale per keyword explaining the search intent it targets.

## Examples (existing apps in this workspace)

| appName        | Keywords                                                     |
|----------------|--------------------------------------------------------------|
| pill-timer     | 알약, 약, 복용, 영양제, 비타민, 타이머, 기록, 건강            |
| bag-check      | 가방, 체크리스트, 외출준비, 깜빡, 출근, 필수품, 챙기기        |
| banchan-mate   | 반찬, 냉장고, 유통기한, 식단, 식재료, 음식물쓰레기, 보관       |
| fare-calc      | 교통비, 환승, 정기권, 버스, 지하철, 출퇴근, 계산기            |
| laundry-log    | 세탁, 빨래, 옷관리, 세탁주기, 의류, 위생, 착용기록            |
| menu-picker    | 오늘뭐먹지, 메뉴추천, 냉장고, 레시피, 식단, 장보기, 간편식    |
| parcel-log     | 택배, 배송, 놓고감, 경비실, 택배함, 수령, 송장               |
| receipt-snap   | 영수증, 가계부, 지출관리, 소액지출, 내역, 소비, 월별          |
| sub-tracker    | 구독, 정기결제, 넷플릭스, 월정액, 결제일, 해지, 지출관리      |
| trash-schedule | 분리수거, 쓰레기, 배출일, 재활용, 음식물, 아파트, 종량제      |
