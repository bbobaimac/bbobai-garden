---
title: "LLM Wiki"
description: "LLM이 raw source를 읽고 지속 갱신하는 interlinked markdown knowledge base"
type: concept
tags:
  - llm-wiki
  - knowledge-management
  - agent
sources:
  - raw/articles/karpathy-llm-wiki.md
created: 2026-06-21
updated: 2026-06-21
confidence: medium
draft: false
---

# LLM Wiki

LLM Wiki는 raw document를 query 때마다 검색하는 [[RAG]]식 흐름과 달리, LLM이 자료를 읽을 때마다 **지속적으로 유지되는 markdown wiki**를 갱신하는 패턴이다.

핵심은 다음 세 계층이다.

1. `raw/`: 변경하지 않는 source of truth
2. `entities/`, `concepts/`, `comparisons/`, `queries/`: LLM이 작성하고 갱신하는 wiki layer
3. [[SCHEMA]]: LLM이 어떤 규칙으로 ingest, query, lint를 수행할지 정하는 운영 문서

이 repo에서는 `content/raw/`에 웹 캡처와 공유 자료를 넣고, LLM이 이를 읽어 concept/entity page를 갱신한다. 그 결과는 Quartz로 공개된다.

## Why it matters

보통의 RAG는 질문이 들어올 때마다 관련 조각을 다시 찾고 다시 합성한다. 반면 LLM Wiki는 한 번 읽은 자료를 wiki page로 컴파일하고, 이후 source가 추가될 때 기존 page를 갱신한다. 그래서 지식이 대화 안에서 사라지지 않고 repo 안에 축적된다.

이 축적 효과는 [[Knowledge Compounding]]의 핵심이다.

## Operating loop

```text
capture source → save raw → update wiki pages → update index/log → build Quartz
```

## Related

- [[Andrej Karpathy]]
- [[Knowledge Compounding]]
- [[SCHEMA]]

## Open links to create

- [[RAG]]
- [[Obsidian]]
- [[Quartz]]
