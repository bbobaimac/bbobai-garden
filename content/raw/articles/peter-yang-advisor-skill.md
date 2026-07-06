---
title: "Peter Yang Advisor Skill source notes"
type: raw-source
source_kind: transcript
source_url: https://youtu.be/H29laIK8q7M
author: "Peter Yang"
ingested: 2026-07-06
sha256: "abdfd36c1c6d9198ea142860c422b20bd988ab81860f559433076c288c80f12b"
draft: false
---

# Peter Yang Advisor Skill source notes

## Source metadata

- Author: Peter Yang
- Source post: https://www.threads.com/@petergyang/post/DZsPcH6GvA0/heres-my-new-tutorial-on-how-to-turn-codex-or-claude-code-into-an-ai-advisor/
- Video: https://youtu.be/H29laIK8q7M
- Retrieved: 2026-07-06
- Source handling: public source notes only. The full YouTube transcript is not stored here because this repo is public.

## Short source summary

Peter Yang describes an `/advisor` skill for Codex or Claude Code that turns an AI coding agent into a life and business advisor. The advisor is implemented as a folder of markdown files:

- `SKILL.md`: how the advisor should behave, what role it should play, what files to read, and how it should answer.
- `plan.md`: the user's goals, principles, energy sources/drains, business context, life context, and constraints.
- `learnings.md`: insights the advisor learns from past conversations.
- `eval.md`: a yes/no checklist the advisor runs before giving advice.

The key claim is that useful AI advice comes less from a clever one-off prompt and more from persistent context, explicit principles, accumulated learnings, and self-evaluation before answering.

## Notable short quotes

> "It knows my goals, gives me useful feedback, and gets better the more I talk to it."

> "Your skill.md is basically how you want the AI to give you advice."

> "plan.md is what I believe about my life and business right now, and learnings.md is what the advisor learns about me over time."

## Garden interpretation

This pattern is relevant to bbobai's Garden because it turns personal or project context into an operational layer for AI agents. It also connects to multi-agent systems: an Advisor can hold long-term context and decision principles, while a Council can bring multiple perspectives to important decisions, and Worker/Verifier agents can execute and check the resulting plan.

The useful abstraction is not "an AI personality" but a small operating system for judgment:

```text
context + principles + learnings + evals + tools + review roles
```

That structure can be applied to public garden publishing, travel planning, product building, and meeting action-item tracking.
