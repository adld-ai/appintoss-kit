<p align="center">
  <img src="./.agents/assets/readme/app-in-toss-icon.png" alt="appintoss-kit 캐릭터" width="140">
</p>

<h1 align="center">appintoss-kit</h1>

<p align="center">
  <em>app-in-toss 작업을 위한 비공식 키트입니다. 규칙을 찾고, 스킬을 쓰고, 매 루프를 검증합니다.</em>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/OpenAI-10A37F?style=flat-square&logo=data%3Aimage%2Fsvg%2Bxml%3Bbase64%2CPHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgaGVpZ2h0PSIxNiIgZmlsbD0id2hpdGUiIGNsYXNzPSJiaSBiaS1vcGVuYWkiIHZpZXdCb3g9IjAgMCAxNiAxNiI%2BCiAgPHBhdGggZD0iTTE0Ljk0OSA2LjU0N2EzLjk0IDMuOTQgMCAwIDAtLjM0OC0zLjI3MyA0LjExIDQuMTEgMCAwIDAtNC40LTEuOTM0QTQuMSA0LjEgMCAwIDAgOC40MjMuMiA0LjE1IDQuMTUgMCAwIDAgNi4zMDUuMDg2YTQuMSA0LjEgMCAwIDAtMS44OTEuOTQ4IDQuMDQgNC4wNCAwIDAgMC0xLjE1OCAxLjc1MyA0LjEgNC4xIDAgMCAwLTEuNTYzLjY3OUE0IDQgMCAwIDAgLjU1NCA0LjcyYTMuOTkgMy45OSAwIDAgMCAuNTAyIDQuNzMxIDMuOTQgMy45NCAwIDAgMCAuMzQ2IDMuMjc0IDQuMTEgNC4xMSAwIDAgMCA0LjQwMiAxLjkzM2MuMzgyLjQyNS44NTIuNzY0IDEuMzc3Ljk5NS41MjYuMjMxIDEuMDk1LjM1IDEuNjcuMzQ2IDEuNzguMDAyIDMuMzU4LTEuMTMyIDMuOTAxLTIuODA0YTQuMSA0LjEgMCAwIDAgMS41NjMtLjY4IDQgNCAwIDAgMCAxLjE0LTEuMjUzIDMuOTkgMy45OSAwIDAgMC0uNTA2LTQuNzE2bS02LjA5NyA4LjQwNmEzLjA1IDMuMDUgMCAwIDEtMS45NDUtLjY5NGwuMDk2LS4wNTQgMy4yMy0xLjgzOGEuNTMuNTMgMCAwIDAgLjI2NS0uNDU1di00LjQ5bDEuMzY2Ljc3OHEuMDIuMDExLjAyNS4wMzV2My43MjJjLS4wMDMgMS42NTMtMS4zNjEgMi45OTItMy4wMzcgMi45OTZtLTYuNTMtMi43NWEyLjk1IDIuOTUgMCAwIDEtLjM2LTIuMDFsLjA5NS4wNTdMNS4yOSAxMi4wOWEuNTMuNTMgMCAwIDAgLjUyNyAwbDMuOTQ5LTIuMjQ2djEuNTU1YS4wNS4wNSAwIDAgMS0uMDIyLjA0MUw2LjQ3MyAxMy4zYy0xLjQ1NC44MjYtMy4zMTEuMzM1LTQuMTUtMS4wOThtLS44NS02Ljk0QTMuMDIgMy4wMiAwIDAgMSAzLjA3IDMuOTQ5djMuNzg1YS41MS41MSAwIDAgMCAuMjYyLjQ1MWwzLjkzIDIuMjM3LTEuMzY2Ljc3OWEuMDUuMDUgMCAwIDEtLjA0OCAwTDIuNTg1IDkuMzQyYTIuOTggMi45OCAwIDAgMS0xLjExMy00LjA5NHptMTEuMjE2IDIuNTcxTDguNzQ3IDUuNTc2bDEuMzYyLS43NzZhLjA1LjA1IDAgMCAxIC4wNDggMGwzLjI2NSAxLjg2YTMgMyAwIDAgMSAxLjE3MyAxLjIwNyAyLjk2IDIuOTYgMCAwIDEtLjI3IDMuMiAzLjA1IDMuMDUgMCAwIDEtMS4zNi45OTdWOC4yNzlhLjUyLjUyIDAgMCAwLS4yNzYtLjQ0NW0xLjM2LTIuMDE1LS4wOTctLjA1Ny0zLjIyNi0xLjg1NWEuNTMuNTMgMCAwIDAtLjUzIDBMNi4yNDkgNi4xNTNWNC41OThhLjA0LjA0IDAgMCAxIC4wMTktLjA0TDkuNTMzIDIuN2EzLjA3IDMuMDcgMCAwIDEgMy4yNTcuMTM5Yy40NzQuMzI1Ljg0My43NzggMS4wNjYgMS4zMDMuMjIzLjUyNi4yODkgMS4xMDMuMTkxIDEuNjY0ek01LjUwMyA4LjU3NSA0LjEzOSA3LjhhLjA1LjA1IDAgMCAxLS4wMjYtLjAzN1Y0LjA0OWMwLS41Ny4xNjYtMS4xMjcuNDc2LTEuNjA3cy43NTItLjg2NCAxLjI3NS0xLjEwNWEzLjA4IDMuMDggMCAwIDEgMy4yMzQuNDFsLS4wOTYuMDU0LTMuMjMgMS44MzhhLjUzLjUzIDAgMCAwLS4yNjUuNDU1em0uNzQyLTEuNTc3IDEuNzU4LTEgMS43NjIgMXYybC0xLjc1NSAxLTEuNzYyLTF6Ii8%2BCjwvc3ZnPg%3D%3D" alt="OpenAI">
  <img src="https://img.shields.io/badge/Claude-D97757?style=flat-square&logo=anthropic&logoColor=white" alt="Claude">
  <img src="https://img.shields.io/badge/Cursor-000000?style=flat-square&logo=cursor&logoColor=white" alt="Cursor">
  <img src="https://img.shields.io/badge/Theme-Toss%20Blue%20%233182f6-3182f6?style=flat-square" alt="Toss Blue theme">
</p>

<p align="center">
  <sub><a href="./README.md">English</a> &middot; <a href="./README.ko.md">한국어</a></sub>
</p>

---

<p align="center">
  <img src="./.agents/assets/readme/app-in-toss-hero.png" alt="appintoss-kit 히어로 비주얼" width="100%">
</p>

`appintoss-kit`은 app-in-toss 작업을 위한 비공식 에이전트 운영 키트입니다.
흩어진 프롬프트에 기대지 않고, 작고 반복 가능한 작업 흐름을 먼저 제공합니다.
루트 계약을 읽고, 맞는 가이드 파일을 찾고, 필요한 로컬 스킬을 불러온 뒤, 준비됐다고 말하기 전에 결과를 검증하는 방식입니다.

> `AGENTS.md`는 에이전트가 작업을 어떻게 라우팅해야 하는지 설명합니다.
> `.agents/`는 스킬, 훅, 서브에이전트, 레퍼런스, README 자산을 담은 재사용 실행 레이어입니다.

**작업을 resolve하고, 맞는 스킬을 적용하고, 가장 작은 변경을 만든 뒤, 증거로 검증하고 다음 단계로 넘어갑니다.**

## 왜 필요한가요?

app-in-toss 작업에는 제품 정책, 한국어 UX 문구, Toss 스타일의 시각 규칙, 스토어 자산, 스크린샷, 빌드 결과물, 콘솔 메타데이터가 함께 얽혀 있습니다.
에이전트가 기억에만 기대면 이 요소들이 쉽게 섞입니다.
이 키트는 에이전트가 움직이기 전에 읽어야 할 규칙을 한곳에 둡니다.

## 작동 방식

| 레이어 | 역할 | 제어하는 것 |
|---|---|---|
| `AGENTS.md` | 루트 계약 | 작업 방식, 지침 상속, 라우트 해결 |
| `guide/` | 작업 라우터 | UI, 자산, 메타데이터, 정책, 에이전트 파일별 규칙 |
| `.agents/skills/` | 실행 스킬 | 이름 생성, SEO 키워드, imagegen 자산, Toss 디자인 테마 |
| `.agents/hooks/` | 루프 정책 | 사전 resolve, 편집 전 게이트, 편집 후 검증, 실패 재계획 |
| `.agents/agents/` | 서브에이전트 | 적대적 리뷰와 위임 검증 |
| `.agents/references/` | 로컬 문맥 | 라우팅될 때만 읽는 큰 참고 자료 |

## AGENTS.md

`AGENTS.md`는 모든 에이전트가 가장 먼저 읽는 파일입니다.
여기서 작업 계약이 정해집니다.

- 편집 전 코드베이스를 조사합니다.
- 요청을 만족하는 가장 작은 올바른 변경을 선호합니다.
- 프로젝트별 지침 상속을 따릅니다.
- 모든 작업을 `guide/resolver.md`로 라우팅합니다.
- 완료를 말하기 전에 검증합니다.

핵심은 라우팅입니다.
UI 변경, 자산 변경, 메타데이터 변경, 에이전트 규칙 변경은 같은 체크리스트를 쓰지 않습니다.
`AGENTS.md`는 에이전트가 편집하기 전에 resolver로 맞는 규칙을 불러오게 합니다.

## .agents

`.agents/`는 재사용 가능한 에이전트 런타임 레이어입니다.

```text
.agents/
  agents/       # 위임 리뷰어 정의
  assets/       # README와 에이전트 문서 이미지
  hooks/        # 개발 루프의 라이프사이클 게이트
  references/   # 큰 로컬 참고 자료
  skills/       # SKILL.md를 가진 네이티브 스킬
```

스킬 레이어는 반복 작업을 명시적으로 만듭니다.
앱 생성은 손으로 추측하지 않고 이름 생성과 SEO 스킬을 사용합니다.
자산 작업은 imagegen과 Toss 디자인 테마 스킬을 사용합니다.
에이전트 규칙 작업은 링크, 경로, 행동 규칙 검사를 통과해야 합니다.

## 루프

이 키트는 의미 있는 모든 작업에 같은 루프를 기대합니다.

```text
resolve
-> 필요한 규칙 읽기
-> 가장 작은 범위의 변경 만들기
-> 관련된 가장 엄격한 게이트로 검증하기
-> 검증 실패 시 root cause에서 다시 계획하기
-> 완료 전 증거를 다시 실행하기
```

이 루프는 에이전트 산출물이 지원하지 않는 기능, 검증되지 않은 주장, 제품과 맞지 않는 제출 문구로 흐르지 않게 막습니다.

## 저장소 표면

최종 키트에서 저장소는 공개 협업 레이어만 추적하도록 의도적으로 제한되어 있습니다.

```text
.agents/
.claude/
.gitignore
.june-2026-vibe-contest/
AGENTS.md
CLAUDE.md
guide/
LICENSE
README.md
README.ko.md
```

생성된 미니앱, 로컬 빌드 결과, 스크린샷, 포스터, 임시 작업 폴더, 제출 번들은 ignore 규칙을 의도적으로 바꾸기 전까지 로컬에만 남습니다.

## 에이전트 사용법

여기서 시작합니다.

```bash
cat AGENTS.md
```

그다음 작업 라우트를 찾습니다.

```bash
cat guide/resolver.md
```

resolved route가 요구할 때 로컬 스킬을 사용합니다.

```text
.agents/skills/app-naming/
.agents/skills/app-seo-keywords/
.agents/skills/codex-imagegen/
.agents/skills/toss-design-theme/
```

## 정책

이 저장소는 app-in-toss를 위한 비공식 키트입니다.
미니앱 아이디어, 생성 자산, 제출 문구는 Apps in Toss 정책과 로컬 Toss 디자인 규칙 안에 있어야 합니다.
공식 Toss 마크를 키트나 앱 정체성으로 쓰지 않습니다.
구현되지 않은 동작을 만들지 않습니다.
최신 검증 증거 없이 준비 완료를 말하지 않습니다.

## 라이선스

[MIT](./LICENSE)
