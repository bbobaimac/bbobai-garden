---
title: "Obsidian + LLM + Git + Quartz"
description: "개인 노트를 공개 가능한 디지털 가든으로 바꾸는 자동화 스택"
tags:
  - obsidian
  - llm
  - git
  - quartz
  - digital-garden
created: 2026-06-21
updated: 2026-06-21
draft: false
---

# Obsidian + LLM + Git + Quartz

이 스택의 목적은 개인 노트를 공개 가능한 지식 자산으로 바꾸는 것입니다.

```text
Obsidian에서 생각을 쓴다
        ↓
LLM이 공개 가능한 글로 정리한다
        ↓
Git이 버전관리하고 GitHub로 보낸다
        ↓
Quartz가 Markdown을 웹사이트로 변환한다
        ↓
GitHub Pages가 공개한다
```

## 각 도구의 역할

### Obsidian

Obsidian은 생각을 쓰고 연결하는 공간입니다. 파일은 Markdown이기 때문에 Git, LLM, Quartz가 모두 다룰 수 있습니다.

### LLM / Hermes

LLM은 원본 노트를 공개용 글로 바꾸는 편집자입니다.

- 민감정보 제거
- 개념 정리
- 제목/설명/태그 생성
- 관련 노트와 `[[위키링크]]` 연결
- 공개용 Markdown 생성

### Git

Git은 변경 이력을 보존하고 배포를 트리거합니다.

```bash
git add .
git commit -m "publish: 공개 노트 추가"
git push origin main
```

### Quartz

Quartz는 Markdown 노트를 정적 웹사이트로 바꿉니다.

- Obsidian 위키링크 처리
- 태그 페이지 생성
- 그래프와 백링크 제공
- 검색 인덱스 생성
- GitHub Pages 배포에 적합한 정적 파일 생성

## 안전한 두 repo 구조

개인적인 내용이 많은 vault를 그대로 공개 repo로 만들면 위험합니다. 그래서 이 사이트는 두 repo 구조를 사용합니다.

```text
second = private source vault
bbobai-garden = public Quartz garden
```

원본 생각은 `second`에 자유롭게 기록하고, 공개할 가치가 있는 내용만 Hermes가 재작성해서 `bbobai-garden/content/`에 발행합니다.

## 핵심 원칙

- 공개 repo에는 공개 가능한 글만 넣습니다.
- `draft: true`는 보안 장치가 아닙니다.
- 민감한 원본은 private vault에만 둡니다.
- 공개 글은 개념 중심으로 다시 씁니다.
