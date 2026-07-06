---
title: "bbobai's Garden"
description: "웹에서 학습한 자료를 raw로 모으고 LLM이 위키로 컴파일하는 공개 디지털 가든"
tags:
  - digital-garden
  - llm-wiki
  - knowledge-management
created: 2026-06-21
updated: 2026-07-06
draft: false
---

# bbobai's Garden

이곳은 웹에서 학습한 자료를 `raw`에 모으고, LLM이 이를 읽어 **지속적으로 갱신되는 공개 위키**로 컴파일하는 공간입니다.

```text
web capture / shared source / paper / transcript
        ↓
content/raw/ 에 원자료 저장
        ↓
LLM이 entity · concept · comparison · query page 생성/갱신
        ↓
Quartz + GitHub Pages로 공개
```

운영 원칙은 [[SCHEMA]]에 있습니다. 이 구조는 Andrej Karpathy의 [[LLM Wiki]] 패턴을 이 repo에 맞게 적용한 것입니다.

> Last updated: 2026-07-06 | Total wiki pages: 6

## Start here

- [[SCHEMA]] — LLM이 이 위키를 유지하는 규칙
- [[log]] — ingest, query, lint 기록
- [[LLM Wiki]] — Karpathy식 LLM-maintained wiki 개념
- [[Knowledge Compounding]] — 읽은 자료가 누적 지식으로 변환되는 원리

## Raw sources

- [[karpathy-llm-wiki]] — Andrej Karpathy, “LLM Wiki” gist
- [[hpd.ai — 프롬프트는 끝났다, 이제 루프를 짠다]] — hpd.ai의 Loop Engineering 캡처 요약
- [[peter-yang-fable-worthy-work]] — Peter Yang의 Fable 5 사용 전략 source notes
- [[peter-yang-advisor-skill]] — Peter Yang의 Advisor Skill source notes

## Entities

- [[Andrej Karpathy]] — LLM Wiki 패턴을 제안한 AI 연구자/교육자

## Concepts

- [[LLM Wiki]] — raw source와 query-time RAG 사이에 지속 갱신되는 markdown wiki를 두는 패턴
- [[Knowledge Compounding]] — 자료를 매번 다시 검색하지 않고 구조화된 지식으로 축적하는 방식
- [[Loop Engineering]] — AI 에이전트가 반복 실행할 trigger, action, verifier, memory, stop condition을 설계하는 방법론
- [[advisor-council-skill|Peter Yang의 Advisor/Council Skill과 멀티 에이전트 의사결정 구조]] — 개인 AI 참모와 관점별 Council을 멀티 에이전트 업무 운영체계로 확장하는 방법
- [[fable-worthy-work|Peter Yang의 Fable-worthy Work 전략]] — Fable 5 같은 최고급 모델을 큰 맥락·장기 판단·출시 감사·전략 설계에 아껴 쓰는 모델 라우팅 전략

## Comparisons

아직 없음.

## Queries

아직 없음.

## Capture inbox

앞으로 웹에서 자료를 공유하면 다음 위치에 저장합니다.

- 기사/블로그: `content/raw/articles/`
- 논문/PDF: `content/raw/papers/`
- 영상/회의/인터뷰 transcript: `content/raw/transcripts/`
- 이미지/다이어그램/스크린샷: `content/raw/assets/`

그다음 LLM이 관련 wiki page를 갱신합니다.
