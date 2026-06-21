---
title: "Wiki Schema"
description: "bbobai's Garden을 Karpathy식 LLM Wiki로 유지하기 위한 운영 규칙"
tags:
  - llm-wiki
  - knowledge-management
  - schema
created: 2026-06-21
updated: 2026-06-21
draft: false
---

# Wiki Schema

## Domain

이 공개 가든은 **웹에서 학습한 자료를 LLM이 누적 편집하는 공개 지식 위키**다. 중심 주제는 AI/LLM, 지식관리, 생산성, 일하는 방식, 디지털 가든, 학습 방법론이다.

개인 Obsidian vault `second`는 필요할 때 참고할 수 있지만, 이 repo의 기본 입력은 웹에서 캡처하거나 공유받은 공개 자료다.

## Core architecture

Karpathy의 LLM Wiki 패턴을 따른다.

```text
content/
├── raw/             # Layer 1: 변경하지 않는 공개 원자료
├── entities/        # Layer 2: 사람, 조직, 제품, 모델 등
├── concepts/        # Layer 2: 개념, 원리, 방법론
├── comparisons/     # Layer 2: 비교/판단/의사결정
├── queries/         # Layer 2: 보존 가치가 있는 질문 답변
├── SCHEMA.md        # Layer 3: LLM 운영 규칙
├── index.md         # 공개 홈페이지이자 위키 카탈로그
└── log.md           # append-only 운영 로그
```

## Source policy

- `raw/`는 공개 가능한 웹 자료, 논문, transcript, 캡처, 공유 자료를 저장한다.
- `raw/`의 파일은 source of truth이므로 생성 후 원칙적으로 수정하지 않는다.
- private vault `second`의 원본 노트를 이 repo에 그대로 복사하지 않는다.
- 웹 캡처도 public GitHub repo에 올라간다는 점을 전제로 저작권, 개인정보, 민감정보를 확인한다.
- 원자료 전문 공개가 부적절하면 `raw/`에는 짧은 인용, URL, 나의 요약 메모, 캡처 메타데이터만 둔다.

## Raw frontmatter

`raw/`의 모든 Markdown source는 아래 정보를 포함한다.

```yaml
---
title: "Source title"
type: raw-source
source_kind: article | paper | transcript | capture | note
source_url: https://example.com
author: "Author or Unknown"
ingested: YYYY-MM-DD
sha256: "body-only-sha256"
draft: false
---
```

`sha256`은 frontmatter 아래 본문만 해시한다. 같은 URL을 다시 ingest할 때 해시가 같으면 재처리를 건너뛴다.

## Wiki page frontmatter

`entities/`, `concepts/`, `comparisons/`, `queries/`의 페이지는 아래 형식을 따른다.

```yaml
---
title: "Page Title"
description: "One-line summary"
type: entity | concept | comparison | query
tags:
  - tag-from-taxonomy
sources:
  - raw/articles/source-file.md
created: YYYY-MM-DD
updated: YYYY-MM-DD
confidence: high | medium | low
draft: false
---
```

## Tag taxonomy

새 태그를 쓰기 전 이 목록에 먼저 추가한다.

- `llm-wiki`: LLM이 유지하는 위키 운영 방식
- `knowledge-management`: 지식관리, 디지털 가든, 노트 구조
- `ai`: AI 전반
- `llm`: 대규모 언어모델
- `agent`: LLM agent, workflow automation
- `research`: 리서치, 논문, 장기 학습
- `workflow`: 반복 가능한 작업 흐름
- `tooling`: 도구, CLI, Obsidian, Git, Quartz
- `productivity`: 생산성, 업무 방식
- `learning`: 학습법, 읽기, 정리
- `person`: 인물 entity
- `source`: 원자료 설명
- `comparison`: 비교 분석
- `query`: 보존 가치가 있는 질문 답변

## Page thresholds

- 한 자료의 중심 주제거나 2개 이상의 source에서 반복 등장하면 별도 페이지를 만든다.
- 단순 언급은 새 페이지를 만들지 않고 관련 페이지의 관련 항목에만 기록한다.
- 페이지가 200줄을 넘으면 하위 개념으로 분리한다.
- 모든 새 위키 페이지는 최소 2개의 `[[wikilinks]]`를 가진다. 단, 첫 초기화 단계에서는 부족한 링크를 `Open links to create` 섹션에 명시할 수 있다.

## Ingest workflow

1. URL, PDF, 캡처, 공유 텍스트를 `content/raw/` 아래에 저장한다.
2. raw source frontmatter와 sha256을 기록한다.
3. 기존 `index.md`, `SCHEMA.md`, 최근 `log.md`를 읽고 중복 페이지를 확인한다.
4. source의 핵심 claim, entity, concept를 식별한다.
5. 필요한 `entities/`, `concepts/`, `comparisons/`, `queries/` 페이지를 생성/갱신한다.
6. 모든 생성/갱신 페이지에 source 링크와 wikilink를 넣는다.
7. `index.md`의 카탈로그와 총 페이지 수를 갱신한다.
8. `log.md`에 `## [YYYY-MM-DD] ingest | Source title` 형식으로 기록한다.
9. `npx quartz build`로 사이트 빌드를 검증한다.

## Query workflow

1. 먼저 `index.md`를 읽는다.
2. 필요하면 `search_files`로 관련 wiki page와 raw source를 찾는다.
3. 답변은 wiki page와 source를 근거로 합성한다.
4. 보존 가치가 있으면 `queries/` 또는 `comparisons/`에 새 페이지로 저장한다.
5. 저장했다면 `index.md`와 `log.md`를 갱신한다.

## Lint workflow

주기적으로 다음을 확인한다.

- 깨진 wikilink
- inbound link가 없는 orphan page
- `index.md`에 누락된 page
- frontmatter 누락
- taxonomy 밖의 tag
- `raw/` sha256 drift
- 200줄 초과 page
- `confidence: low` 또는 contested claim

## Language and style

- 기본 언어는 한국어다.
- 원문 용어가 중요한 AI/기술 개념은 영어 병기를 허용한다.
- 원자료 요약은 "무엇을 주장하는가 → 왜 중요한가 → 다른 페이지와 어떻게 연결되는가" 순서로 쓴다.
- 개인 블로그식 감상보다 재사용 가능한 개념 정리를 우선한다.
