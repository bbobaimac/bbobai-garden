---
title: "AI Agent Work Operating System"
description: "LLM Wiki, Loop Engineering, Fable-worthy Work, Advisor/Council을 하나의 작업 운영체계로 연결하는 관점"
type: concept
tags:
  - ai
  - agent
  - workflow
  - llm-wiki
  - productivity
sources:
  - raw/articles/karpathy-llm-wiki.md
  - raw/articles/hpd-loop-engineering.md
  - raw/articles/peter-yang-fable-worthy-work.md
  - raw/articles/peter-yang-advisor-skill.md
created: 2026-07-06
updated: 2026-07-06
confidence: medium
draft: false
---

# AI Agent Work Operating System

AI Agent Work Operating System은 이 가든에 들어온 raw source들을 하나로 묶는 상위 개념이다. 핵심은 AI를 단발성 챗봇으로 쓰는 것이 아니라, **자료를 저장하고, 맥락을 유지하고, 반복 작업을 돌리고, 중요한 판단을 검증하는 작업 운영체계**로 설계하는 것이다.

현재 raw source들은 네 조각을 제공한다.

```text
LLM Wiki
= 지식이 쌓이는 저장/편집 구조

Loop Engineering
= 반복 작업을 안전하게 돌리는 실행 구조

Fable-worthy Work
= 비싼 모델을 어디에 쓸지 정하는 판단/라우팅 구조

Advisor/Council Skill
= 개인·프로젝트 맥락을 읽고 의사결정하는 참모 구조
```

이 네 가지를 합치면 다음과 같은 운영체계가 된다.

```text
source capture
  → raw/ 저장
  → LLM Wiki page 갱신
  → loop/verifier로 품질 확인
  → frontier model은 고난도 판단에만 투입
  → advisor/council이 방향과 리스크 검토
  → worker agents가 실행
  → 결과와 learnings를 다시 wiki에 누적
```

## 1. LLM Wiki: 기억의 구조

[[LLM Wiki]]는 raw source를 매번 query-time에 다시 검색하는 대신, LLM이 읽은 내용을 `entities/`, `concepts/`, `comparisons/`, `queries/`로 컴파일하게 한다. 이 방식은 [[Knowledge Compounding]]을 만든다. 읽은 자료가 채팅창에 사라지지 않고, 다음 판단의 기반이 된다.

## 2. Loop Engineering: 반복 실행의 구조

[[Loop Engineering]]은 AI 에이전트를 단발성 프롬프트가 아니라 반복 가능한 루프로 설계한다.

```text
trigger → action → verifier → memory/log → stop condition
```

좋은 루프는 에이전트의 “완료했습니다”라는 말이 아니라, build success, test pass, link check, deploy confirmation 같은 환경 신호를 믿는다.

## 3. Fable-worthy Work: 모델 라우팅의 구조

[[fable-worthy-work|Peter Yang의 Fable-worthy Work 전략]]은 최고급 모델을 아무 일에나 쓰지 말고, 큰 맥락·전략·감사·장기 판단에 쓰라는 원칙이다.

```text
싼 모델: 자료 수집, 초안, 반복 실행
강한 모델: 방향성, 리스크, 아키텍처, 최종 검토
싼 모델: 세부 실행
```

이 관점은 agent system에서 비용과 품질을 동시에 관리하는 기준이 된다.

## 4. Advisor/Council: 의사결정의 구조

[[advisor-council-skill|Peter Yang의 Advisor/Council Skill과 멀티 에이전트 의사결정 구조]]는 개인이나 프로젝트의 목표, 원칙, learnings, eval checklist를 파일로 유지하게 한다. Advisor는 장기 맥락을 읽고 판단을 통합한다. Council은 중요한 결정에서 고객, 회의론자, 운영자, 전문가 관점을 충돌시킨다.

## bbobai's Garden에서의 적용

이 가든 자체도 작은 AI Agent Work OS다.

```text
공개 source / 영상 / 캡처
  → content/raw/ 에 source notes 저장
  → 관련 concept/entity/comparison/query page 생성
  → index.md와 log.md 갱신
  → Quartz build
  → GitHub Pages 배포 확인
```

이 구조가 커지면 다음과 같은 작업도 운영 가능하다.

- 회의 녹음본에서 액션아이템을 뽑고 과거 회의록과 비교하는 project memory loop
- `luxBBtravel` 같은 여행 manager profile이 가족 선호와 일정 제약을 장기적으로 기억하는 planning loop
- AI 제품 아이디어를 Advisor/Council/Worker/Verifier 구조로 검토하고 MVP까지 보내는 product loop
- 공개 가든에 올릴 source의 저작권·개인정보·논리 흐름을 검증하는 publishing loop

## 핵심 원칙

- raw source와 wiki page를 분리한다.
- 반복 작업은 loop로 만들되 verifier와 stop condition을 먼저 둔다.
- 강한 모델은 큰 판단에 쓰고, 반복 실행은 worker에게 맡긴다.
- Advisor는 장기 맥락을 읽고, Council은 관점 충돌을 만들고, Worker는 실행하고, Verifier는 결과를 확인한다.
- 좋은 결과는 다시 wiki에 저장해 다음 작업의 맥락으로 만든다.

## Related

- [[LLM Wiki]]
- [[Loop Engineering]]
- [[fable-worthy-work|Peter Yang의 Fable-worthy Work 전략]]
- [[advisor-council-skill|Peter Yang의 Advisor/Council Skill과 멀티 에이전트 의사결정 구조]]
- [[Peter Yang]]
