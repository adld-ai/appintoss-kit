# 6월 바이브코딩 챌린지 — 우승 작품 제작 키트

공식 챌린지 페이지: https://toss.im/apps-in-toss/blog/2606_vibecoding_challenge

## 구성

| 경로 | 역할 |
| --- | --- |
| `AGENTS.md` | 챌린지 우승용 강화 제작 규칙 (strict). 공통 app-in-toss AGENTS.md와 함께 따른다. |
| `adversarial-reviewer/AGENT.md` | canonical reviewer 위치를 가리키는 포인터. |

## 활성 서브에이전트

`adversarial-reviewer`의 canonical 정의는
`.agents/agents/adversarial-reviewer/AGENT.md`에 있다. parent agent는 이
정의를 기준으로 `run_subagent` 또는 동등한 subagent 호출을 실행한다.

## 의무 워크플로우

모든 미니앱 프로젝트는 두 번 심사를 받아야 한다:

1. **구현 전 (`pre-build` 모드)**: 아이디어·주제 적합성·AU 동기 사전 심사.
   ```bash
   # 예: parent agent가 호출
   run_subagent(profile="adversarial-reviewer",
     task="pre-build mode. Review the pill-timer idea at
     /Users/tonylee/abld/Product/app-in-toss/pill-timer against the contest rules.")
   ```
2. **출품 전 (`pre-submit` 모드)**: 전체 체크리스트 + 실제 구현/자산 심사.

두 심사 모두 `VERDICT: PASS`여야 출품한다. `FAIL`이면 `## Required fixes` 항목을
수정 후 재심사.

## 심사 기준 요약

- 주제: "일상이 편해지는 순간" (반복 자동화 / 귀찮은 계산·기록 / 일상 불편 해결 /
  생활 정보 한눈에). 단순 리워드성·주제 이탈 앱은 심사 제외.
- 1차 심사 = 7/1~7/26 활성 유저(AU). 최종 심사 = 완성도 종합 평가.
- 마감: 2026-06-30 첫 빌드 콘솔 등록 (권장 06-29). 신청폼 appName == 콘솔 ==
  `granite.config.ts`.
- 자산·디자인·기술 표준은 `AGENTS.md`와 공통 app-in-toss AGENTS.md를 따른다.
