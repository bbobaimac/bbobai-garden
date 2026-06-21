# Public LLM Wiki rules

This repository is public. It is `bbobai-garden`: a Quartz site operated as a Karpathy-style LLM Wiki.

## Core model

Use this repo as a raw-source → LLM-maintained wiki → Quartz publishing pipeline.

```text
web capture / shared source / PDF / transcript
        ↓
content/raw/              # immutable public source layer
        ↓
content/entities/         # entity pages generated/maintained by LLM
content/concepts/         # concept pages generated/maintained by LLM
content/comparisons/      # side-by-side analysis
content/queries/          # durable answers worth keeping
        ↓
content/index.md + content/log.md
        ↓
Quartz build + GitHub Pages
```

Before any ingest/query/lint work, read:

1. `content/SCHEMA.md`
2. `content/index.md`
3. recent entries in `content/log.md`

## Public safety boundary

- This repo is public GitHub content. Only publish internet-safe material.
- The private Obsidian vault `second` may be referenced only when the user explicitly asks, and must never be copied verbatim here.
- The default input for this garden is public web material: articles, papers, docs, transcripts, screenshots, and links the user shares.
- Remove or generalize family details, company/client/customer names, financial details, health details, private conversations, credentials, tokens, emails, phone numbers, addresses, and any detail that could identify a non-consenting person.
- `draft: true` hides a page from the Quartz site but is not a privacy mechanism because the Markdown can still exist in this public GitHub repo.

## Raw source rules

- Store public sources under `content/raw/`.
- Treat `content/raw/` as immutable after ingest. If interpretation changes, update wiki pages instead of editing raw.
- If reposting full source text could violate copyright or privacy expectations, store only metadata, URL, short quotations, and the user's notes.
- Every raw markdown file needs frontmatter with `title`, `type: raw-source`, `source_kind`, `source_url`, `author`, `ingested`, `sha256`, and `draft: false`.

## Wiki maintenance rules

- Follow `content/SCHEMA.md` for taxonomy, frontmatter, page thresholds, ingest/query/lint workflows.
- Use Korean by default; preserve English technical terms when useful.
- Use Obsidian-style `[[wikilinks]]` aggressively enough that the graph becomes useful.
- Every created or updated wiki page must be reflected in `content/index.md`.
- Every ingest/query/lint/archive action must be appended to `content/log.md`.
- Run `npx quartz build` before committing or pushing.

## Frontmatter for wiki pages

```yaml
---
title: "..."
description: "..."
type: entity | concept | comparison | query
tags:
  - tag-from-schema
sources:
  - raw/articles/source.md
created: YYYY-MM-DD
updated: YYYY-MM-DD
confidence: high | medium | low
draft: false
---
```

## Publishing flow

1. Capture source into `content/raw/`.
2. Generate/update wiki pages under `content/entities/`, `content/concepts/`, `content/comparisons/`, or `content/queries/`.
3. Update `content/index.md` and `content/log.md`.
4. Run `npx quartz build` locally.
5. Commit and push only after the build succeeds.
