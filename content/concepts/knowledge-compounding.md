---
title: "Knowledge Compounding"
description: "읽은 자료가 일회성 요약이 아니라 연결된 지식 자산으로 누적되는 방식"
type: concept
tags:
  - knowledge-management
  - learning
  - llm-wiki
sources:
  - raw/articles/karpathy-llm-wiki.md
created: 2026-06-21
updated: 2026-06-21
confidence: medium
draft: false
---

# Knowledge Compounding

Knowledge Compounding은 자료를 읽을 때마다 단발성 요약을 만드는 대신, 기존 지식 구조를 갱신해서 다음 학습의 기반으로 남기는 방식이다.

[[LLM Wiki]] 패턴에서 compounding은 다음 방식으로 일어난다.

- source는 `raw/`에 보존된다.
- LLM은 source를 읽고 관련 [[LLM Wiki]] page를 갱신한다.
- 새 자료가 기존 주장과 충돌하면 덮어쓰지 않고 contradiction으로 표시한다.
- 좋은 query answer는 `queries/`나 `comparisons/`에 저장되어 다시 활용된다.
- `index.md`와 [[log]]가 탐색과 이력의 backbone 역할을 한다.

## Difference from one-off summaries

일회성 요약은 시간이 지나면 채팅 기록에 묻힌다. Knowledge Compounding은 요약을 wiki의 기존 page에 합쳐 넣기 때문에, 다음 질문은 더 풍부한 상태에서 시작한다.

## Related

- [[LLM Wiki]]
- [[SCHEMA]]
- [[Andrej Karpathy]]
