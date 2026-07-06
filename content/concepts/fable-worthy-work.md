---
title: "Peter Yang의 Fable-worthy Work 전략"
description: "Fable 5 같은 최고급 모델을 어디에 써야 하는지 판단하는 모델 라우팅 전략"
type: concept
tags:
  - ai
  - llm
  - agent
  - workflow
  - productivity
sources:
  - raw/articles/peter-yang-fable-worthy-work.md
created: 2026-07-06
updated: 2026-07-06
confidence: medium
draft: false
---

# Peter Yang의 Fable-worthy Work 전략

Peter Yang이 Fable 5 관련 콘텐츠에서 강조하는 핵심은 **“가장 똑똑한 모델을 가장 비싼 방식으로 낭비하지 말라”**는 것이다. Fable은 단순 답변기가 아니라 **전략가, 감사자, 설계자, 고난도 리뷰어**처럼 써야 한다.

Fable-worthy work는 대체로 다음 조건을 만족한다.

```text
1. 큰 맥락을 읽어야 한다.
2. 여러 단계의 판단이 필요하다.
3. 결과가 앞으로 몇 달의 방향에 영향을 준다.
4. 실수 비용이 크다.
5. 더 싼 모델이 실행할 수 있을 만큼 좋은 계획을 만들 수 있다.
```

## 왜 중요한가

Frontier model은 비싸고 사용량 제한이 있다. 따라서 “모든 일을 가장 강한 모델에게 시키는 것”보다 **모델 라우팅**이 중요하다.

```text
싼 모델: 자료 수집, 초안, 단순 실행
Fable: 고난도 판단, 설계, 위험 파악
싼 모델: 세부 구현
```

Peter Yang의 표현으로 요약하면 다음과 같다.

```text
Plan with Fable.
Execute with another model.
```

이 관점은 [[Loop Engineering]]과도 연결된다. Fable에게 긴 작업을 맡길 때는 goal, verifier, stop condition, budget guardrail이 필요하다.

## 1. Fable에게 Fable-worthy work를 찾게 하기

첫 번째 사용법은 Fable에게 “내가 너를 어디에 써야 가장 가치가 있니?”라고 묻는 것이다.

예시 프롬프트 구조:

```text
You are Fable 5, the most capable AI model available.
Look through my projects and memory.
List the top five tasks that require deep thinking
and are genuinely worth running by you.
```

Fable이 잘 찾는 작업 유형은 다음과 같다.

- 장기 사업 전략 점검
- 새로운 상품/오퍼 설계
- 콘텐츠 → 전환율 분석
- 과거 콘텐츠 아카이브를 바탕으로 로드맵 만들기
- 개인 OS, 스킬, 자동화 시스템 감사

핵심은 Fable이 **큰 정보 덩어리에서 패턴을 찾고, 우선순위를 정하고, 실행 방향을 제안하는 데 강하다**는 점이다.

## 2. 인생/비즈니스 조언 받기

Peter Yang이 가치 있게 본 사용법 중 하나는 **장기 의사결정 조언**이다. 단, 그냥 “내 사업 어떻게 해야 해?”라고 물으면 안 된다. 먼저 Fable에게 충분한 맥락을 줘야 한다.

필요한 맥락은 다음과 같다.

- 올해 목표와 의사결정 원칙
- 사업 포지셔닝, 타깃 고객, 차별점
- 경쟁자/대안
- 에너지를 주는 일과 빼앗는 일
- 재무 상황 또는 제약조건
- 콘텐츠 일정과 성과 데이터
- 관련 API/MCP 데이터

핵심 사용법은 다음과 같다.

```text
1. 고수준 plan document를 만든다.
2. 관련 데이터/API/MCP를 연결한다.
3. Fable에게 3개월, 6개월, 1년 단위의 조언을 요청한다.
```

한 번의 좋은 판단이 앞으로 몇 달의 방향을 바꿀 수 있기 때문에, 이런 장기 의사결정은 Fable-worthy하다.

## 3. 프로젝트를 ship-ready 상태로 만들기

세 번째 사용법은 출시 전 프로젝트 점검이다.

프롬프트 방향:

```text
이 앱을 곧 출시하려고 한다.
전체 코드베이스를 읽고,
실제 사용자 앞에서 깨질 수 있는 버그,
엣지 케이스,
품질 문제를 모두 찾아라.
높은 품질 기준으로 수정해야 할 목록을 만들어라.
```

Fable은 단순히 테스트 통과 여부만 보는 것이 아니라 다음과 같은 문제를 찾는 감사자 역할에 적합하다.

- 로그아웃/세션 문제
- 사용자 데이터 누수 가능성
- cloud sync edge case
- 이상 입력 처리
- MCP/API 관련 문제
- 실제 사용 중 망가질 수 있는 흐름

핵심은 **테스트가 통과해도 제품이 안전하다는 뜻은 아니다**라는 점이다.

## 4. 다음 큰 기능/제품을 계획하게 하기

네 번째 사용법은 실행이 아니라 **상세한 실행 계획을 만드는 것**이다.

좋은 요청 방식:

```text
새 기능에 대한 상세 계획을 작성해줘.
관련 자료를 검색하고,
주요 단계,
결정해야 할 것,
리스크,
망할 수 있는 지점,
열린 질문을 정리해줘.
더 싼 모델이 단계별로 실행할 수 있을 만큼 명확하게 써줘.
```

Fable이 직접 끝까지 구현하지 않아도 된다. Fable은 좋은 계획을 만들고, 실제 구현은 더 싼 모델에게 넘길 수 있다.

## 5. 큰 코드베이스 또는 개인 OS 리팩터링

다섯 번째 사용법은 대규모 리팩터링이다. 개인 수준에서는 꼭 수천만 줄 코드가 아니어도 된다.

Fable-worthy한 리팩터링 대상:

- 개인 AI 스킬 폴더
- 자동화 시스템
- Claude Code 설정
- Obsidian/Hermes 기반 개인 OS
- 오래 쌓인 스크립트/문서/템플릿
- 콘텐츠 제작 워크플로우

Fable에게 기대할 수 있는 결과:

- 중복 제거
- 모호한 지시 수정
- 죽은 escalation block 제거
- 임시 파일 정리
- 잘못된 routing 수정
- 더 효과적인 skill 구조 제안

이 부분은 bbobai's Garden이나 Hermes skill 운영에도 직접 적용 가능하다.

## 운영 원칙

- **싼 모델로 먼저 준비하라.** 자료 조사, plan document 초안, API/MCP 연결 준비, 요구사항 정리, 리스크 초안, handoff prompt 작성은 더 싼 모델에게 맡긴다.
- **Fable은 계획, 실행은 다른 모델.** Fable은 상세 기획, 아키텍처 판단, 리스크 파악, 제품 방향성 결정, 리뷰/감사에 쓰고, 실제 코딩이나 반복 작업은 더 싼 모델에게 넘긴다.
- **effort를 무조건 최대로 두지 말고 감시하라.** Ultra effort를 항상 쓰지 말고, 진행 방향을 확인하며, 성공 기준과 멈춤 조건을 명확히 준다.

## 나쁜 사용과 좋은 사용

나쁜 사용은 PDF 요약, 글 초안, 작은 코드 수정, 아이디어 나열처럼 **저비용 모델도 충분히 할 수 있는 일**이다.

좋은 사용은 전체 프로젝트와 목표를 보고 중요한 일을 판단하거나, 출시 전 치명적 문제를 찾거나, 3개월 전략을 데이터 기반으로 점검하거나, 복잡한 개인 OS를 감사하거나, 더 싼 모델이 실행할 수 있는 완성도 높은 계획을 만드는 것이다.

즉 Fable의 가치는 “더 좋은 문장”이 아니라 **큰 맥락에서의 판단 품질**에 있다. 이 전략은 [[LLM Wiki]]처럼 지식을 누적하는 시스템에서도 중요하다. 좋은 모델을 매번 검색과 요약에 태우는 대신, 이미 누적된 자료를 바탕으로 고차원 판단을 하게 해야 [[Knowledge Compounding]]이 일어난다.

## bbobai's Garden에 적용하기

bbobai's Garden과 Hermes 운영에 적용하면 Fable-worthy work는 다음과 같다.

- `bbobai-garden`의 구조, 콘텐츠 방향, 타깃 독자, 3개월 운영 전략 점검
- Hermes skills, memories, Obsidian 구조, garden 구조의 중복·위험·자동화 기회 감사
- 공개 발행 전 개인정보, 저작권, 과장, 출처 부족, 논리 흐름 문제 감사
- AI/Obsidian/LLM Wiki 관련 자료를 바탕으로 10편짜리 공개 콘텐츠 시리즈 설계
- 여행 매니저 개인 OS처럼 장기 목표와 제약이 많은 시스템 설계

이런 일은 단순 답변보다 판단과 구조화가 중요하기 때문에 Fable류 모델에 적합하다.

## Related

- [[Loop Engineering]]
- [[LLM Wiki]]
- [[Knowledge Compounding]]
