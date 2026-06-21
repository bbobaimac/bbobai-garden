# Public digital garden rules

This repository is public. Only publish internet-safe content.

## Source boundary

- The private Obsidian vault `second` is the source of raw/private material.
- This repository, `bbobai-garden`, must contain only rewritten, redacted, public-facing notes.
- Never copy private vault notes verbatim.

## Safety

Remove or generalize before publishing:

- family details
- company/client/customer names
- financial details
- health details
- private conversations
- credentials, tokens, emails, phone numbers, addresses
- any detail that could identify someone who did not consent

`draft: true` hides a page from the Quartz site but is **not** a privacy mechanism because the Markdown can still exist in this public GitHub repo.

## Writing style

- Write in Korean by default unless the user requests another language.
- Prefer clear, practical, essay-like Markdown.
- Each note should focus on one concept.
- Use Obsidian-style wikilinks when useful.
- Avoid AI-ish filler; keep the user's voice and point of view.

## Frontmatter

Every note in `content/` should include:

```yaml
---
title: "..."
description: "..."
tags:
  - tag-one
created: YYYY-MM-DD
updated: YYYY-MM-DD
draft: false
---
```

## Publishing flow

1. Rewrite/redact the source note into a public-facing note.
2. Save it under `content/`.
3. Run `npx quartz build` locally.
4. Commit and push only after the build succeeds.
