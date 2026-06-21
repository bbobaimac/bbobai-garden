---
title: "Wiki Log"
description: "bbobai's Garden의 ingest, query, lint 작업 로그"
tags:
  - llm-wiki
  - log
created: 2026-06-21
updated: 2026-06-21
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
