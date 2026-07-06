---
title: "Peter Yang의 Advisor/Council Skill과 멀티 에이전트 의사결정 구조"
description: "개인 AI 참모와 관점별 Council을 멀티 에이전트 업무 운영체계로 확장하는 방법"
type: concept
tags:
  - ai
  - llm
  - agent
  - workflow
  - productivity
sources:
  - raw/articles/peter-yang-advisor-skill.md
created: 2026-07-06
updated: 2026-07-06
confidence: medium
draft: false
---

# Peter Yang의 Advisor/Council Skill과 멀티 에이전트 의사결정 구조

Peter Yang의 Advisor Skill은 Codex나 Claude Code 같은 AI coding agent를 **개인 인생·커리어·비즈니스 조언자**처럼 쓰기 위한 markdown 기반 skill 구조다. 핵심은 매번 긴 맥락을 다시 설명하는 대신, 개인의 목표·원칙·학습·검증 기준을 파일로 유지해서 AI가 그 위에서 조언하게 만드는 것이다.

이 아이디어는 [[fable-worthy-work|Peter Yang의 Fable-worthy Work 전략]]과 연결된다. Fable-worthy Work가 “가장 강한 모델을 어디에 써야 하는가”를 다룬다면, Advisor/Council 구조는 “그 모델이 어떻게 계속 좋은 판단을 하게 만들 것인가”를 다룬다.

## Advisor Skill의 기본 구조

Advisor는 보통 다음 네 파일로 구성된다.

```text
advisor/
├── SKILL.md
├── plan.md
├── learnings.md
└── eval.md
```

`SKILL.md`는 advisor의 행동 규칙이다. 개인 정보 자체를 많이 넣기보다, 어떤 역할을 해야 하는지, 어떤 파일을 읽어야 하는지, 어떤 형식으로 조언해야 하는지를 정의한다.

`plan.md`는 가장 중요한 맥락 문서다. 올해 목표, 의사결정 원칙, 에너지를 주는 일과 빼앗는 일, 사업 포지셔닝, 가족·생활 맥락, 재무적 제약 같은 정보를 담는다. 좋은 조언은 좋은 맥락에서 나온다.

`learnings.md`는 대화를 통해 누적되는 패턴의 기록이다. 예를 들어 “사용자는 추상적인 조언보다 실행 가능한 조언을 선호한다”, “사용자는 콘텐츠 제작보다 직접 AI 제품을 만드는 일에서 에너지를 얻는다” 같은 반복 학습을 저장한다.

`eval.md`는 답변 전 체크리스트다. 최신 `plan.md`와 `learnings.md`를 읽었는지, 사실과 가정을 구분했는지, 이번 주 실행 가능한 next step을 제시했는지 확인한다. 이 파일은 AI가 그럴듯한 일반론으로 도망가지 못하게 하는 품질 gate다.

## Advisor와 Council의 차이

Advisor는 사용자의 장기 맥락을 알고 조언을 통합하는 주 참모다. Council은 중요한 결정에서 여러 관점을 충돌시키는 검토 회의다.

```text
Advisor = 장기 맥락과 최종 통합 판단
Council = 고객, 회의론자, 운영자, 전문가 관점의 충돌
```

예를 들어 “이 AI 제품 아이디어를 다음 달에 출시할까?”라는 질문이 들어오면 Advisor는 먼저 `plan.md`와 `learnings.md`를 읽는다. 바로 답하기 어렵다면 Council을 소집한다.

```text
- Customer Advocate: 실제 고객이 이 문제를 아파하는가?
- Skeptic: 이 계획은 왜 실패할 수 있는가?
- Operator: 이번 주에 무엇을 해야 하는가?
- Knowledge Architect: 기존 지식 구조와 연결되는가?
```

그 뒤 Advisor가 각 관점을 종합해서 최종 추천과 next step을 제시한다. Council은 인격 놀이가 아니라 **의사결정에 필요한 관점들을 구조화하는 장치**다.

## 멀티 에이전트 app/task 군집으로 확장하기

이 구조를 멀티 에이전트 시스템으로 확장하면 다음과 같은 end-to-end 흐름이 된다.

```text
User Request
   ↓
Intake Agent
   ↓
Advisor Layer
   ↓
Council Review
   ↓
Planner Agent
   ↓
Worker Agent Swarm
   ↓
Verifier / QA Agents
   ↓
Integrator
   ↓
Memory / Learnings Update
```

Intake Agent는 사용자의 요청, 성공 기준, 제약, 공개·비공개 경계를 정리한다. Advisor Layer는 장기 목표와 원칙을 기준으로 이 일을 지금 어떻게 처리할지 판단한다. Council Review는 중요한 결정에서 여러 관점을 충돌시킨다. Planner Agent는 작업을 worker에게 넘길 수 있을 만큼 작게 쪼갠다. Worker Agent Swarm은 조사, 작성, 구현, 검증을 수행한다. Verifier는 요구사항, 안전성, 품질, 배포 여부를 확인한다. Integrator는 산출물을 통합하고, 마지막으로 learnings를 갱신한다.

중요한 것은 “에이전트를 많이 만든다”가 아니다. 핵심은 **맥락을 가진 참모진, 역할이 나뉜 실행팀, 검증 gate가 있는 작업 운영체계**를 만드는 것이다.

## 예시 A: garden 글 발행 군집

bbobai's Garden에 글을 발행하는 작업은 이미 작은 멀티 에이전트 workflow에 가깝다.

```text
User: 이 링크 garden에 올려줘.

Intake: 공개 글인지, source 종류가 뭔지 파악
Advisor: 이 주제가 garden 방향과 맞는지 판단
Council: 독자 관점, 저작권/개인정보, 지식 구조, 배포 리스크 검토
Workers: source notes 작성, concept page 작성, index/log 갱신
Verifier: Quartz build, GitHub Pages 배포 URL 확인
```

이때 Council은 특히 공개 발행 리스크를 줄인다. raw source에 전문 transcript를 넣지 않고 source notes만 저장하는 결정도 이런 gate에서 나온다. 이는 [[LLM Wiki]]와 [[Knowledge Compounding]]을 공개 repo에서 안전하게 운영하기 위한 방식이다.

## 예시 B: 여행 매니저 `luxBBtravel` 군집

여행 매니저 프로필에서는 Advisor가 가족의 장기 여행 aspiration, 예산, 선호도, 일정 제약을 기억한다.

```text
User: 내년 봄 가족 여행 후보를 짜줘.

Advisor: 장기 여행 목표와 가족 조건 확인
Council: Family Experience Advocate, Budget Skeptic, Logistics Operator, Child-Friendly Reviewer
Workers: 여행지 조사, 항공/동선, 숙소, 일정, 리스크 확인
Verifier: 일정 충돌, 예산 범위, 아이 동반 난이도, 날씨/비자/이동시간 확인
```

단순 추천보다 중요한 것은 “우리 가족에게 맞는 여행인가”를 지속적으로 판단하는 것이다.

## 예시 C: AI 제품 만들기 군집

AI 제품이나 앱을 만들 때 Advisor/Council 구조는 vibe coding보다 안전한 실행 체계를 만든다.

```text
User: 이 아이디어로 MVP 만들어줘.

Advisor: 장기 목표와 맞는 아이디어인지 판단
Council: Customer, Skeptic, Product Manager, Engineer, Operator
Workers: 리서치, PRD, 디자인, 백엔드, 프론트엔드, QA
Verifier: 요구사항 충족, 테스트, 보안/개인정보, 배포 확인
```

Advisor는 방향과 우선순위를 잡고, Worker는 실행한다. Council은 실패 가능성과 고객 가치를 검토한다. Verifier는 실제로 작동하는지 확인한다.

## 예시 D: 회의록 녹음본 기반 액션아이템 추적 군집

가장 현실적인 업무 예시는 회의 녹음본 처리다. 사용자가 회의 녹음본을 공유하면 시스템은 단순 요약이 아니라 **회의의 연속성**을 관리해야 한다.

```text
User: 회의 녹음본 공유할게. 액션아이템 뽑고, 지난 회의록들과 비교해서 누락된 것과 다음 회의에 챙겨야 할 것을 알려줘.
```

E2E 흐름은 다음과 같다.

```text
Meeting Audio
   ↓
Transcription Agent
   ↓
Meeting Understanding Agent
   ↓
Action Item Extractor
   ↓
Historical Meeting Notes Access
   ↓
Action Tracker Agent
   ↓
Follow-up Planner Agent
   ↓
Verifier / Ambiguity Checker
   ↓
Next Meeting Brief
```

Transcription Agent는 녹음본을 전사하고 가능하면 화자를 구분한다. Meeting Understanding Agent는 회의 주제, 결정사항, 쟁점을 정리한다. Action Item Extractor는 `누가 / 무엇을 / 언제까지 / 어떤 완료 기준으로`를 구조화한다.

```yaml
action_items:
  - owner: A
    task: 랜딩페이지 초안 작성
    due: 이번 주 금요일
    status: new
    source: 00:03:12
    confidence: high
  - owner: C
    task: API 비용 이슈 확인
    due: 다음 회의 전
    status: carried_over
    source: 00:06:45
    confidence: medium
```

Historical Meeting Notes Access는 누적된 회의록 파일에 접근한다. 예를 들어 비공개 Obsidian vault나 프로젝트 폴더에는 다음과 같은 구조가 있을 수 있다.

```text
Meetings/MVP Sync/2026-06-01.md
Meetings/MVP Sync/2026-06-08.md
Meetings/MVP Sync/2026-06-15.md
Action Items/mvp-action-tracker.md
```

Action Tracker Agent는 새 액션아이템과 기존 항목을 비교한다. 새로 생긴 일, 완료된 것으로 보이는 일, 지난 회의에서 넘어온 일, 반복적으로 지연되는 블로커를 구분한다. Follow-up Planner Agent는 다음 회의에서 반드시 확인할 질문과 agenda를 만든다.

최종 산출물은 다음과 같은 brief다.

```text
# 이번 회의 요약

## 주요 결정
- MVP 랜딩페이지 초안을 이번 주 금요일까지 만든다.
- 고객 인터뷰 5명을 다음 주까지 추가한다.
- API 비용 이슈는 다음 회의 전까지 확인한다.

## 신규 액션아이템
- A: 랜딩페이지 초안 작성 — 금요일
- B: 고객 인터뷰 5명 섭외 — 다음 주

## 이전 회의에서 넘어온 항목
- C: API 비용 이슈 확인 — 미완료, 다음 회의 전 확인 필요

## 다음 회의에서 반드시 확인할 것
1. API 비용 구조 확인 결과
2. 랜딩페이지 초안 리뷰
3. 고객 인터뷰 섭외 현황
4. MVP scope 변경 필요 여부

## 모호하거나 확인 필요한 항목
- 디자인 리뷰 담당자와 일정이 명확하지 않음
```

이 예시에서 Verifier/Ambiguity Checker가 중요하다. 회의 전사는 틀릴 수 있고, “디자인도 이번 주에 보면 좋겠다”처럼 담당자와 기한이 불명확한 문장을 확정 액션아이템처럼 저장하면 안 된다. 따라서 담당자, due date, 발언 근거, 전사 오류 가능성, 완료 여부의 확실성을 함께 표시해야 한다.

이 구조는 “회의록 요약 도구”가 아니라 **프로젝트 운영 기억을 가진 회의 follow-up 시스템**이다. 반복되는 업무의 맥락을 기억하고, 이전 결과와 현재 입력을 비교하며, 다음 실행을 놓치지 않게 만드는 것이 멀티 에이전트 시스템의 진짜 가치다.

## 설계 원칙

- Advisor는 방향을 잡고 Worker는 실행한다.
- Council은 되돌리기 어려운 결정, 공개/보안 리스크가 있는 작업, 장기 방향에 영향이 큰 작업에만 쓴다.
- Eval/Gate가 없으면 멀티 에이전트는 위험하다. Context gate, Safety gate, Spec gate, Quality gate, Deploy gate를 분리한다.
- Learnings는 반복적으로 유용한 패턴만 저장한다. 일시적 작업 상태, 곧 낡을 숫자, 단발성 URL, 민감정보는 저장하지 않는다.
- 권한을 분리한다. Research Agent는 읽기만, Writer는 초안 작성, Publisher만 push 권한을 갖는 식으로 설계한다.

## 결론

Peter Yang의 Advisor/Council 구조는 단순한 프롬프트 모음이 아니다. AI가 좋은 판단을 하도록 **맥락, 원칙, 학습, 자기검증, 관점 충돌**을 파일 시스템으로 구조화한 것이다.

이를 멀티 에이전트 app에 적용하면 다음과 같은 운영체계가 된다.

```text
Advisor = 장기 맥락과 판단의 중심
Council = 중요한 결정의 관점 충돌 장치
Worker Agents = 실제 조사·작성·구현 담당
Verifier Agents = 결과 검증과 배포 gate
Learnings = 시스템이 시간이 지날수록 좋아지는 기억
```

따라서 목표는 AI 여러 개를 동시에 돌리는 것이 아니라, **맥락을 가진 참모진 + 역할이 나뉜 실행팀 + 검증 gate가 있는 작업 운영체계**를 만드는 것이다. 이 관점은 [[Loop Engineering]]과 직접 연결된다.

## Related

- [[fable-worthy-work|Peter Yang의 Fable-worthy Work 전략]]
- [[Loop Engineering]]
- [[LLM Wiki]]
- [[Knowledge Compounding]]
