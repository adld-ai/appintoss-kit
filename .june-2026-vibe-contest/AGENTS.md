# 6월 바이브코딩 챌린지 — 우승 작품 제작 규칙 (Strict)

> Source of truth: https://toss.im/apps-in-toss/blog/2606_vibecoding_challenge
> 이 규칙은 챌린지 공식 페이지를 기반으로 한 강화된 내부 제작 표준이다. 공식 규정과
> `/Users/tonylee/abld/Product/app-in-toss/AGENTS.md`(앱인토스 공통 가이드)를 모두
> 충족해야 하며, 둘이 충돌하면 더 엄격한 쪽을 따른다.

이 디렉터리 아래의 모든 미니앱 프로젝트는 **반드시** 아래 규칙을 통과해야 하며,
`adversarial-reviewer` 서브에이전트의 사전 심사를 거쳐야 출품/빌드한다.

---

## 0. 강제 게이트 (Mandatory gate)

1. 모든 프로젝트는 구현 시작 전·출품 전에 각각 한 번씩 `adversarial-reviewer`
   서브에이전트를 실행한다. 서브에이전트가 `FAIL`을 내면 출품하지 않는다.
2. `adversarial-reviewer`는 거부 이유를 먼저 찾는 대항 심사자(adversarial
   reviewer)다. 통과하려면 모든 항목이 `PASS`여야 한다.
3. 이 규칙의 어떤 항목도 "거의 맞음"으로 통과시키지 않는다. 빈칸·누락·모호한
   문구·구현되지 않은 기능 묘사는 즉시 `FAIL`이다.

---

## 1. 챌린지 정체 (Challenge identity)

- 챌린지명: 6월 바이브코딩 챌린지
- 주제: **"일상이 편해지는 순간"**
- 출품 기간: 2026-06-08 ~ 2026-06-30 (6월 30일 자정 마감)
- 테마 지면 노출: 2026년 7월 첫째 주 ~ 7월 26일
- 결과 발표: 2026년 7월 마지막 주
- 신청폼: https://toss.im/_m/JTkiSRsh
- 콘솔: https://apps-in-toss.toss.im/

> 6월 30일 마감이므로, 마지막 날 빌드 업로드 장애를 피해 **6월 29일까지 첫 빌드
> 등록**을 완료한다.

---

## 2. 주제 적합성 (Theme fit) — 가장 중요한 거절 사유

주제 가이드에 **정확히** 해당해야 한다. 아래 중 하나 이상을 만족해야 한다:

- 반복되는 일을 자동화해주는 앱
- 귀찮은 계산·기록을 대신해주는 앱
- 일상의 작은 불편을 해결하는 앱
- 생활 정보를 한눈에 보여주는 앱

**거절 대상 (심사 제외):**
- 별도 핵심 기능이 없는 단순 리워드성 미니앱 (예: 출석 체크만 하고 포인트 주는 앱)
- 주제 가이드에서 벗어난 앱 (예: 순수 게임, 오락성 콘텐츠, 주제와 무관한 도구)
- "일상을 편하게"라는 감성이 구현된 기능으로 뒷받침되지 않는 앱

주제 적합성은 신청폼의 **한줄 소개**와 **챌린지 주제와의 연관성** 필드로 판단된다.
이 필드들은 출품 적합성 판단 기준이므로 정성껏, 그리고 구현된 기능에 정확히
맞게 작성한다. 구현되지 않은 기능을 부풀려 적으면 거절 사유가 된다.

---

## 3. 출품 자격 (Eligibility)

- 2026년 6월 8일 이전에 출시된 미니앱으로 출품 불가. 신규 앱이어야 한다.
- 1인(또는 동일 법인)이 복수 미니앱 출품 가능. 단, 상금은 가장 우수한 1개만
  기준이며 동일인이 복수 순위 동시 수상 불가.
- 미니앱의 모든 권리가 본인에게 귀속되어야 한다.
- 제3자 지식재산권 침해 금지. 침해 시 민/형사상 조치 대상.
- 앱인토스 운영 정책 위반 시 노출 중단 및 보상 제한.

---

## 4. 심사 방식 (Judging) — 이것에 맞춰 설계한다

| 단계 | 기준 | 설계 시 함의 |
| --- | --- | --- |
| 1차 심사 | 7월 1일~26일 활성 유저 수(AU) | 첫 진입이 매끄럽고 재방문 동기가 있어야 한다. |
| 최종 심사 | 미니앱 완성도 종합 평가 (테마 적합성·UX 포함) | 완성도·디자인·안정성이 1차 통과작 사이에서 순위를 갈른다. |

설계 원칙:
- **AU 확보**: 첫 화면에서 핵심 가치가 5초 안에 전달되어야 한다. 온보딩 장벽
  최소화. 핵심 기능이 비회원/비로그인 상태에서도 바로 작동해야 한다.
- **재방문 동기**: 매일 쓰는 루틴(알림·기록·체크)을 내장하여 7월 1~26일 AU를
  끌어올린다.
- **완성도**: 크래시·흰화면·멈춤이 없어야 한다. TDS 컴포넌트는 토스 네이티브
  브릿지가 필요하므로 브라우저 폴백을 반드시 둔다 (공통 AGENTS.md 참조).

---

## 5. 출품 절차 (Submission) — 누락 금지

1. **앱 개발**: 6월 8일~30일 테마에 맞는 미니앱 개발.
2. **콘솔 등록**: 앱인토스 콘솔에서 앱 생성
   - 만들고 싶은 앱 설명: 10자 이상, 실제 서비스 설명 (앱 이름만으로는 거절됨)
   - 앱 이름(한국어 표시명)
   - appName: `granite.config.ts`와 정확히 일치, 소문자 kebab-case
   - 앱 유형: 게임/비게임 (구현이 실제 게임일 때만 게임)
3. **버전 등록**: 6월 30일까지 콘솔에서 첫 `.ait` 번들 등록. 앱 정보 미승인 상태라도
   버전 등록은 가능. 등록 후 순차 검수.
4. **신청폼 제출**: https://toss.im/_m/JTkiSRsh
   - 한국어 앱 이름 (콘솔 '앱 정보'와 일치)
   - appName (콘솔과 정확히 일치 — 불일치 시 출품 인정 안 됨)
   - 한줄 소개
   - 챌린지 주제와의 연관성

> 신청폼의 appName이 콘솔과 다르면 출품이 인정되지 않는다. 세 곳(콘솔·신청폼·
> `granite.config.ts`)의 appName이 문자열 단위로 동일해야 한다.

---

## 6. 콘솔 제출 자산 (Store assets) — 공통 AGENTS.md 준수

모든 자산은 공통 AGENTS.md의 "Console submission reporting"과 "Asset creation
rules"를 따른다. 요약:

- 한국어 앱 이름: 필수 (10자 한도)
- 영어 앱 이름: 필수 (15자 한도, 단어 첫 글자만 대문자, 띄어쓰기 분리)
- 부제목: 필수 (20자 한도, 구체적 사용자 가치)
- 상세 설명: 필수, 구현된 동작만, 한 문장 한 줄바꿈
- 앱 ID/appName: 필수, `granite.config.ts`와 일치
- 사용자 연령 등급: 필수
- 고객지원 이메일: 필수, 실제 이메일
- 버전 메모: `-` 불릿, 한 줄 한 변경, 120자 이내
- 카테고리: 구현 동작 기준 선택 (알약/건강 류면 `생활 > 건강 > 건강 관리`)
- 검색 키워드: 불릿 1개씩, 사용자가 입력할 구체 명사/작업어
- 앱 로고: 600x600, 16비트 픽셀아트, Toss 팔레트, Codex imagegen 생성
- 다크모드 로고: 600x600, 라이트 로고에서 파생(배경 `#191f28`, 내부 `#6db1fe`)
- 썸네일: 1932x828, 히어로 구도, Codex imagegen 생성
- 스크린샷: 실제 앱 화면 캡처, 세로 636x1048 최소 3장 또는 가로 1504x741 최소 1장
  (이미지 생성 금지)

파일 조직:
- `public/logo/`, `public/screenshot/`, `public/asset/`
- `submission/<appName>.ait`, `submission/logo/`, `submission/screenshot/`,
  `submission/asset/`, `submission/inputs.md`
- 파일명: 소문자 ASCII kebab-case, 치수 포함
  (`app-logo-600.png`, `app-logo-dark-600.png`, `thumbnail-1932x828.png`,
  `screenshot-<nn>-<screen-name>-636x1048.png`)

---

## 7. 디자인 테마 (Toss design theme)

공통 AGENTS.md의 Toss 팔레트 토큰을 `granite.config.ts`의 `primaryColor`와
`src/App.tsx`의 모든 인라인 스타일에 일관되게 적용한다. 비-Toss 색(
`#4CAF50`, `#80848B` 등) 혼용 금지.

| 역할 | 토큰 |
| --- | --- |
| Primary | `#3182f6` |
| Primary tint bg | `#e8f3ff` |
| Text primary | `#191f28` |
| Text secondary | `#6b7684` |
| Background | `#f2f4f6` |
| Border | `#e5e8eb` |
| Success | `#03b26c` |
| Success tint bg | `#f0faf6` |
| Danger | `#f04452` |
| CTA black | `#191f28` |

---

## 8. 기술 표준 (Tech)

- Scaffold: `npx create-ait-app <appName> --inline --pm npm --template react-ts --tds --skills --ai claude`
- `appName`: 소문자 kebab-case
- Storage: `@apps-in-toss/web-framework`의 `Storage`. AsyncStorage 사용 금지(흰화면).
  브라우저 dev에선 `localStorage` 폴백 (`__AIT_INTERNAL__` 감지).
- TDS 컴포넌트는 토스 네이티브 브릿지 필요. 브라우저 테스트 시 순수 HTML/CSS로
  대체하거나 환경 가드. `TDSMobileAITProvider`는 TDS 미사용 시 제거.
- 개발: `npm run dev` (localhost:5173), 빌드: `npm run build` (`<appName>.ait`)

---

## 9. 출품 전 체크리스트 (Pre-submission checklist)

`adversarial-reviewer`가 아래를 모두 확인한다:

- [ ] 주제("일상이 편해지는 순간") 가이드에 정확히 부합, 단순 리워드성 아님
- [ ] 2026-06-08 이후 신규 앱
- [ ] `granite.config.ts` appName == 콘솔 appName == 신청폼 appName
- [ ] 콘솔 앱 생성: 설명 10자 이상, 한국어 이름, appName, 앱 유형
- [ ] 첫 `.ait` 빌드 6월 30일 전(권장 6월 29일) 콘솔 등록
- [ ] 신청폼 제출: 한국어 이름·appName·한줄 소개·주제 연관성 (구현 기반)
- [ ] 한국어/영어 이름·부제목·상세 설명·연령·지원이메일·버전메모·카테고리·키워드
- [ ] 로고 600x600(16비트 픽셀아트), 다크 로고 600x600(파생), 썸네일 1932x828
- [ ] 스크린샷: 실제 앱 화면, 세로 636x1048≥3 또는 가로 1504x741≥1
- [ ] Toss 팔레트 일관 적용, 비-Toss 색 제로
- [ ] 브라우저 폴백 동작, 흰화면/크래시/멈춤 없음
- [ ] 핵심 가치 5초 진입 + 재방문 동기(루틴/기록/알림) 내장
- [ ] `submission/inputs.md`에 모든 콘솔 입력값 기록
- [ ] 권리 전부 본인 귀속, 타인 IP 침해 없음

---

## 10. 서브에이전트 의무 (Mandatory subagent)

- 프로젝트 구현 시작 전: `adversarial-reviewer`로 아이디어·주제 적합성 사전 심사.
- 출품 직전: `adversarial-reviewer`로 전체 체크리스트 + 실제 구현/자산 심사.
- 두 심사 모두 `PASS`여야 출품한다. `FAIL` 시 항목별 거절 이유를 받아 수정 후 재심사.
- 서브에이전트 정의: `.agents/agents/adversarial-reviewer/AGENT.md`
