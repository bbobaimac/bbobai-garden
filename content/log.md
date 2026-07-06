---
title: "Wiki Log"
description: "bbobai's Garden의 ingest, query, lint 작업 로그"
tags:
  - llm-wiki
  - log
created: 2026-06-21
updated: 2026-07-06
draft: false
---

# Wiki Log

> Chronological record of all wiki actions. Append-only.
> Format: `## [YYYY-MM-DD] action | subject`
> Actions: create, ingest, update, query, lint, archive, delete

## [2026-06-21] create | Karpathy-style LLM Wiki structure initialized
- Created `content/SCHEMA.md`, `content/index.md`, `content/log.md`.
- Created wiki directories: `raw/`, `entities/`, `concepts/`, `comparisons/`, `queries/`.
- Adapted the repo from a general public garden into a raw-source → LLM wiki → Quartz workflow.

## [2026-06-21] ingest | Andrej Karpathy, “LLM Wiki”
- Added raw source: `raw/articles/karpathy-llm-wiki.md`.
- Added entity page: `entities/andrej-karpathy.md`.
- Added concept pages: `concepts/llm-wiki.md`, `concepts/knowledge-compounding.md`.
- Updated `index.md` catalog.


## [2026-06-22] ingest | hpd.ai, “프롬프트는 끝났다, 이제 루프를 짠다”
- Added raw capture summary: `raw/articles/hpd-loop-engineering.md`.
- Added screenshot asset: `raw/assets/hpd-loop-engineering-2026-06-21.jpg`.
- Added concept page: `concepts/loop-engineering.md`.
- Updated `index.md` catalog.

## [2026-07-06] ingest | Peter Yang, “Fable-worthy Work”
- Added raw source notes: `raw/articles/peter-yang-fable-worthy-work.md`.
- Added concept page: `concepts/fable-worthy-work.md`.
- Updated `index.md` catalog.


## [2026-07-06] ingest | Peter Yang, “Advisor Skill”
- Added raw source notes: `raw/articles/peter-yang-advisor-skill.md`.
- Added concept page: `concepts/advisor-council-skill.md`.
- Included the meeting-recording action-item tracking multi-agent example.
- Updated `index.md` catalog.

## [2026-07-06] update | Raw-based garden organization pass
- Added entity page: `entities/peter-yang.md`.
- Added synthesis concept: `concepts/agent-work-operating-system.md`.
- Added comparison page: `comparisons/rag-vs-llm-wiki.md`.
- Updated `index.md` with reading paths and a cleaner catalog.
- Updated cross-links in `concepts/llm-wiki.md`, `concepts/loop-engineering.md`, `concepts/fable-worthy-work.md`, and `concepts/advisor-council-skill.md`.