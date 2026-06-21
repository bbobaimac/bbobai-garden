# bbobai-garden

Public digital garden powered by Obsidian, LLM, Git, and Quartz.

## Architecture

```text
private Obsidian vault: second
        ↓
Hermes / LLM rewrite and redaction
        ↓
public Quartz repo: bbobai-garden
        ↓
GitHub Pages
```

## Local commands

```bash
npm ci
npx quartz build
npx quartz build --serve
```

## Publishing rule

Only public-safe, rewritten notes belong in `content/`.
