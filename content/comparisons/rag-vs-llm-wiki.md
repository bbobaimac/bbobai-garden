---
title: "RAG vs LLM Wiki"
description: "query-time retrieval과 persistent compiled wiki의 차이"
type: comparison
tags:
  - comparison
  - llm-wiki
  - knowledge-management
  - ai
sources:
  - raw/articles/karpathy-llm-wiki.md
created: 2026-07-06
updated: 2026-07-06
confidence: medium
draft: false
---

# RAG vs LLM Wiki

[[LLM Wiki]]는 일반적인 RAG와 비슷해 보이지만 작동 방식이 다르다. 둘 다 raw document를 활용하지만, 지식이 축적되는 위치가 다르다.

## 핵심 차이

```text
RAG
= 질문이 들어올 때마다 raw source에서 관련 chunk를 찾아 답변한다.

LLM Wiki
= source를 읽을 때마다 markdown wiki를 갱신하고, 이후 질문은 이 축적된 wiki를 기반으로 답한다.
```

## RAG의 장점

- 초기 구축이 비교적 쉽다.
- 많은 문서를 빠르게 검색할 수 있다.
- 원문 chunk에 직접 접근하기 좋다.
- source가 매우 자주 바뀌는 경우 유용하다.

## RAG의 한계

- 질문할 때마다 지식을 다시 찾고 다시 합성한다.
- 이전 질문에서 만든 좋은 분석이 시스템 안에 남지 않는다.
- 여러 source 사이의 연결, 충돌, 누적된 해석이 약하다.
- 좋은 답변이 나와도 다음 질문의 기반으로 자동 축적되지 않는다.

## LLM Wiki의 장점

- source를 한 번 읽고 wiki page로 컴파일한다.
- entity, concept, comparison, query page가 시간이 지나며 풍부해진다.
- 충돌이나 업데이트를 페이지에 남길 수 있다.
- 좋은 질문/답변을 `queries/`나 `comparisons/`로 저장해 재사용할 수 있다.
- Obsidian/Quartz/Git과 잘 맞는다.

## LLM Wiki의 리스크

- LLM이 잘못 정리하면 오류가 wiki에 굳어질 수 있다.
- `index.md`, `log.md`, wikilink를 관리하지 않으면 금방 지저분해진다.
- source와 해석을 분리하지 않으면 출처 추적이 어려워진다.
- 공개 repo에서는 저작권과 개인정보 정책이 필요하다.

## bbobai's Garden의 선택

bbobai's Garden은 RAG보다 LLM Wiki 쪽에 가깝다.

```text
content/raw/
= source of truth

content/entities/, concepts/, comparisons/, queries/
= LLM이 컴파일한 wiki layer

content/SCHEMA.md, index.md, log.md
= 운영 규칙, 카탈로그, 변경 이력
```

이 방식의 목표는 단순히 자료를 찾는 것이 아니라, 자료를 읽을 때마다 [[Knowledge Compounding]]이 일어나게 만드는 것이다.

## Related

- [[LLM Wiki]]
- [[Knowledge Compounding]]
- [[SCHEMA]]
- [[agent-work-operating-system|AI Agent Work Operating System]]
