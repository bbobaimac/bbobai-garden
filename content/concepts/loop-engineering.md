---
title: "Loop Engineering"
description: "AI 에이전트가 반복 실행할 트리거, 액션, 검증, 메모리, 관찰, 정지조건을 설계하는 방법론"
type: concept
tags:
  - ai
  - agent
  - workflow
  - tooling
sources:
  - raw/articles/hpd-loop-engineering.md
created: 2026-06-22
updated: 2026-07-06
confidence: medium
draft: false
---

# Loop Engineering

**Loop Engineering**은 AI 에이전트에게 매번 단발성 프롬프트를 주는 대신, 에이전트가 반복적으로 실행할 **루프**를 설계하는 접근이다. 핵심은 “무엇을 시킬까?”보다 “언제 시작하고, 무엇을 반복하며, 어떤 신호를 보고 멈출까?”를 명시하는 데 있다.

[[hpd.ai — 프롬프트는 끝났다, 이제 루프를 짠다]] 캡처는 이 변화를 “프롬프트의 시대에서 루프의 시대로” 이동하는 흐름으로 요약한다.

## 핵심 구조

루프의 최소 단위는 세 가지다.

1. **Trigger** — 루프가 언제 시작되는가?
   - 예: 새 이슈가 생김, 테스트가 실패함, 새 자료가 inbox에 들어옴.
2. **Action** — 루프가 무엇을 수행하는가?
   - 예: 코드 수정, 자료 요약, 위키 페이지 갱신, 리포트 생성.
3. **Stop condition** — 루프가 언제 멈추는가?
   - 예: 지정 테스트 100% 통과, 회귀 테스트 PASS, 변경 없음, 예산 한도 도달.

하지만 이 세 요소만으로는 부족하다. 실제 운영 가능한 에이전트 루프에는 아래 안전장치가 함께 들어가야 한다.

## 운영에 필요한 추가 요소

### 1. Verifier

루프의 산출물을 독립적으로 검사하는 검증자다. 코드라면 테스트·타입체크·린트·CI가 될 수 있고, 지식관리라면 링크 무결성·frontmatter 검사·출처 확인이 될 수 있다.

검증자는 에이전트 자신의 자기평가보다 환경에서 관측되는 신호에 가까울수록 좋다.

### 2. Memory

루프가 매번 같은 시행착오를 반복하지 않도록 이전 결과, 실패 원인, 선호 규칙, 작업 맥락을 저장하는 장치다. [[LLM Wiki]]처럼 raw source를 구조화된 wiki page로 바꾸는 방식도 장기 기억을 만드는 루프의 한 형태다.

### 3. Observation / Log

루프가 무엇을 했고 어떤 신호를 봤는지 남기는 기록이다. 로그가 있어야 실패한 루프를 디버깅하고, 너무 많은 비용을 쓰는 루프를 조기에 멈출 수 있다.

### 4. Budget guardrail

루프는 성공할 때까지 무한히 도는 구조가 되기 쉽다. 그래서 시간, 토큰, API 비용, 반복 횟수, 파일 변경 범위 같은 예산 한도가 필요하다. 좋은 루프는 “성공하면 멈춘다”뿐 아니라 “너무 비싸지면 멈춘다”도 포함한다.

## 좋은 정지조건의 기준

나쁜 정지조건은 주관적이다.

- “충분히 좋아 보이면 멈춘다.”
- “에이전트가 완료했다고 말하면 멈춘다.”
- “더 할 일이 없어 보이면 멈춘다.”

좋은 정지조건은 관측 가능하다.

- 지정 테스트가 모두 통과한다.
- 회귀 테스트가 통과한다.
- 빌드가 성공한다.
- 링크 검사와 schema 검사가 통과한다.
- 변경 diff가 기대 범위 안에 있다.
- 예산 한도 안에서 verifier가 PASS를 반환한다.

따라서 Loop Engineering의 핵심 문장은 다음처럼 정리할 수 있다.

> 에이전트의 말보다 환경 신호와 예산 있는 정지조건을 믿는다.

## 자동화의 역설

모든 작업을 바로 루프로 만들면 오히려 위험하다. 불안정한 작업을 자동화하면 실패도 자동으로 반복된다.

실무적으로는 다음 순서가 안전하다.

1. 사람이 수동으로 같은 작업을 여러 번 성공시킨다.
2. 반복되는 trigger와 action을 식별한다.
3. verifier와 observation log를 먼저 붙인다.
4. stop condition을 관측 가능한 신호로 정의한다.
5. budget guardrail을 둔다.
6. 그다음 자동 실행 범위를 넓힌다.

## 이 위키에 주는 의미

이 `bbobai-garden` 자체도 하나의 작은 루프로 운영될 수 있다.

```text
public source / screenshot / transcript
        ↓ trigger
raw source로 저장
        ↓ action
concept · entity · query page 생성/갱신
        ↓ verifier
schema, 링크, Quartz build 검사
        ↓ stop condition
빌드 성공 + index/log 갱신 + push 완료
```

이 관점에서 [[Knowledge Compounding]]은 단순히 “많이 저장하기”가 아니라, 검증 가능한 루프를 통해 지식을 계속 정제하는 과정이다.

## Related

- [[agent-work-operating-system|AI Agent Work Operating System]]
- [[LLM Wiki]]
- [[Knowledge Compounding]]
