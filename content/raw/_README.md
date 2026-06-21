---
title: "Raw Sources"
description: "웹 캡처, 공유 자료, 논문, transcript를 저장하는 변경 불가 source layer"
tags:
  - source
  - llm-wiki
created: 2026-06-21
updated: 2026-06-21
draft: false
---

# Raw Sources

`raw/`는 LLM Wiki의 원자료 계층입니다. LLM은 이 폴더를 읽지만, 생성 후에는 원칙적으로 수정하지 않습니다.

## Folders

- `articles/`: 웹 기사, 블로그, gist, 문서
- `papers/`: 논문, PDF, technical report
- `transcripts/`: 영상, 팟캐스트, 인터뷰, 회의 transcript
- `assets/`: 이미지, 다이어그램, 스크린샷

## Rule

원자료 전문을 public repo에 올려도 되는지 애매하면, 전문 대신 URL과 짧은 발췌/요약만 저장합니다.
