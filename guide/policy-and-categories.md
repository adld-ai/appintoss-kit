# Policy and Categories

## Service Policy Gate

Before ideating a new app, choosing a category, writing `submission/inputs.md`,
or submitting release metadata, check the current Apps in Toss service open
policy:

<https://developers-apps-in-toss.toss.im/intro/guide.md>

Do not propose, build, categorize, or describe a mini-app as any restricted
service or content type below:

- Digital asset or virtual asset services, including NFT ownership, transfer,
  storage, trading, brokerage, or issuance.
- Services that enable money laundering, including direct exchange, conversion,
  or refund of cash or cash-like assets inside the mini-app.
- Illegal or abusive services, including identity manipulation, hacking,
  illegal documents, or bypassing information collection limits.
- Gambling, lottery, betting, or speculative prize content.
- Financial product brokerage, sale, or advertising, including loans,
  insurance, cards, securities, or similar products.
- Investment advisory, stock-picking, paid investing information, or investment
  "reading room" concepts.
- Medical services that provide or connect telemedicine, connect users directly
  to medical acts, provide hospital booking, collect advertising or user
  acquisition fees from hospitals, or can be interpreted as hospital promotion
  or marketing.
- Existing-company or existing-service promotion where the mini-app is only a
  promotional shell.
- Any concept that depends on app install prompts, app-market links, external
  payment pages, external sign-up flows, or a core feature that cannot be
  completed inside the mini-app.

Treat the following as additional-review categories. Only proceed when the
implemented service and submission copy can satisfy the stated conditions:

- Medical information lookup can be submitted only when it is based on public
  data, has no ranking, recommendation, or booking function, lists hospitals by
  the same standard, states the data source, and has no hospital advertising or
  paid promotion.
- Shopping services need customer support, anti-counterfeit, and refund policy
  coverage.
- Education services that generate revenue around national professional or
  technical certifications need the required qualifications.

For category ideation and app naming, restrict candidates to categories that
the implemented behavior can honestly satisfy under this policy. If a concept
touches a restricted or additional-review area, either narrow the app to a
permitted in-app utility or stop and ask the user for the required eligibility,
licenses, policies, or source data before writing console copy.

## Platform Policy Constraints

- Do not include copy, banners, images, links, or incentives that encourage
  users to install a separate app.
- Use external links only when they are legally required notices, official
  public/partner pages, simple third-party information pages, or another
  policy-permitted exception. Core app flows must be complete in the mini-app.
- If the app uses generative AI and exposes AI-generated text, image, audio, or
  video results, disclose AI use before or at first use and label generated
  results clearly in the UI and submission copy.
- Use Toss login only for login. Do not add other social or easy-login methods.
- For physical goods, use Toss Pay only. For digital goods, use in-app payment
  only.
- Use only Apps in Toss full-screen, rewarded, or banner ads. Do not integrate
  external ad networks.
- Do not repeatedly launch mini-apps with substantially the same core function
  in the same workspace. Update the existing app unless the new app has a
  clearly different purpose and core function.

## Category Rules

- If a captured category has no distinct third-level options, use the same value
  as the second-level parent for the third dropdown.
- Choose the category by implemented behavior, not by visual theme.
- Choose the most specific category that describes the app's completed in-app
  function. Do not choose a higher-traffic or more favorable category if the
  implemented behavior belongs elsewhere.
- For a pill, medicine, supplement, health routine, or medication timer app,
  prefer `생활 > 건강 > 건강 관리`, not `생활 > 건강 > 의료`, unless the app is
  strictly a permitted public-data medical information lookup that satisfies the
  policy conditions above.

## Captured Non-Game Category Tree

```text
생활
├─ 음식 · 음료
│  └─ 음식 · 음료
├─ 교육
│  └─ 교육
├─ 건강
│  ├─ 건강 관리
│  ├─ 심리
│  ├─ 운동
│  ├─ 의료
│  ├─ 영양 · 식단
│  └─ 기타
├─ 교통
│  ├─ 자동차
│  ├─ 렌터카
│  ├─ 항공
│  └─ 기타
├─ 공공 · 행정
│  └─ 공공 · 행정
├─ 소셜
│  └─ 소셜
├─ 편의
│  ├─ 도구
│  ├─ 구독 · 렌탈
│  └─ 기타
├─ 쇼핑
│  └─ 쇼핑
├─ AI
│  └─ AI
├─ 비즈니스
│  ├─ 구인구직
│  ├─ 직장
│  ├─ 사장님
│  └─ 기타
├─ 콘텐츠
│  ├─ 공연 · 이벤트
│  ├─ 웹툰
│  ├─ 음악 · 오디오
│  ├─ 영상
│  ├─ 운세
│  ├─ 테스트
│  └─ 기타
├─ 여행
│  ├─ 숙박
│  ├─ 지도
│  ├─ 해외
│  └─ 기타
├─ 일상
│  ├─ 가족
│  ├─ 날씨
│  ├─ 집 · 이사
│  ├─ 반려동물
│  ├─ 뷰티
│  ├─ 자기계발
│  ├─ 취미
│  ├─ 패션
│  └─ 기타
└─ 정보
   ├─ 뉴스
   ├─ 도서
   └─ 기타
```
