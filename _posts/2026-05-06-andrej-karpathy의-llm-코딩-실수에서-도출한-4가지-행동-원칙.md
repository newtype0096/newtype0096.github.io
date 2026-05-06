---
layout: post
title: Andrej Karpathy의 LLM 코딩 실수에서 도출한 4가지 행동 원칙
date: '2026-05-06 21:51:53 +0900'
image: /assets/img/20260506/andrej-karpathy-skills.png
category:
- AI
- AI Agent
tags:
- Andrej Karpathy
- llm
- andrej-karpathy-skills
---

> **CLAUDE.md** 파일 하나가 GitHub에서 가장 빠르게 성장하는 저장소 중 하나가 되었다. 이 파일은 **Andrej Karpathy**가 LLM 코딩에서 흔히 발생하는 문제점을 분석하여 도출한 4가지 원칙만을 사용하여, AI 코딩 에이전트를 초보 개발자에서 체계적인 엔지니어로 변화시킨다. 각 원칙을 자세히 살펴보고, 왜 이러한 원칙들이 중요한지 기록한다.

빠르게 진화하는 AI 기반 코딩 분야에서 AI 코딩 에이전트를 위한 행동 지침 모음집 중 가장 인기있는 자료로 떠오른 GitHub 저장소가 하나 있다. 바로 [forrestchang/andrej-karpathy-skills](https://github.com/forrestchang/andrej-karpathy-skills) 이다.

개발자 **Forrest Chang**이 만든 이 저장소는 Andrej Karpathy가 LLM 코딩에서 흔히 발생하는 문제점에 대해 제시한 의견들을 하나의 실용적인 파일로 정리한 것이다.

## 왜 입소문을 탔을까?
이 저장소는 기본적으로 파일 하나만 포함하고 있음에도 불구하고 GitHub에서 가장 빠르게 성장하는 저장소 중 하나가 되었다. 몇 주 만에 수만 개의 별을 받았다.

프레임워크도 아니고, 라이브러리도 아니고, 앱도 아니다. AI 코딩 에이전트를 위한 단일 행동 지침 세트다. 2026년 1월 27일에 개발되어 MIT 라이선스로 배포되었으며, 지금도 계속 성장하고 있다.

## 기원
이 저장소는 OpenAI 공동 창립자이자 테슬라의 전 AI 책임자이며 "바이브 코딩(vibe coding)"이라는 용어를 만든 **Andrej Karpathy**의 트윗에서 직접적으로 유래했다. Karpathy는 해당 트윗에서 도구나 저장소를 공유하지 않았다. 대신, LLM이 코드를 작성할 때 보이는 문제점들에 대한 자신의 경험을 공유했다.

<center>
<blockquote class="twitter-tweet"><p lang="en" dir="ltr">A few random notes from claude coding quite a bit last few weeks.<br><br>Coding workflow. Given the latest lift in LLM coding capability, like many others I rapidly went from about 80% manual+autocomplete coding and 20% agents in November to 80% agent coding and 20% edits+touchups in…</p>&mdash; Andrej Karpathy (@karpathy) <a href="https://twitter.com/karpathy/status/2015883857489522876?ref_src=twsrc%5Etfw">January 26, 2026</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>
</center>

개발자 **Forrest Chang**은 이러한 관찰 내용을 읽고 실용적인 조치를 취했다. 바로 이를 구조화되고 기계가 읽을 수 있는 **CLAUDE.md** 파일로 변환한 것이다.

## 4가지 원칙
Forrest Chang은 Karpathy의 관찰 내용을 4가지 원칙으로 정리했다.

* 코딩하기 전에 생각하라
* 단순함이 최우선
* 수술적 변화
* 목표 중심적 실행

각각에 대해 자세히 살펴보자.

## 1. 코딩하기 전에 생각하라
**추측하지 말것. 혼란스러운 점을 숨기지 말것. 장단점을 명확히 드러낼것.**

이것이 가장 기본적인 원칙이다. LLM들은 암묵적으로 해석을 선택하고 그것을 고수하는 경향이 있다. 이 원칙은 명시적인 추론을 요구한다.

* **가정을 명확하게 명시할것**: 불확실한 경우 추측하기보다는 질문하라
* **다양한 해석을 제시할것**: 모호한 부분이 있을 때는 바로 선택하지마라
* **필요할 때는 반박할것**: 더 간단한 방법이 있다면 말하라
* **이해가 안 될 때는 멈출것**: 무엇이 불분명한지 말하고 설명을 요청하라

## 2. 단순함이 최우선
**문제를 해결하는 데 필요한 최소한의 코드만 작성할것. 추측성 코드는 일절 포함하지 말것.**

이는 LLM의 과도한 설계 경향을 막기 위한 것이다.

* 요청한 사항 외에는 추가적인 기능은 없음.
* 일회용 코드에는 추상화가 필요 없음.
* 요청하지 않은 "유연성"이나 "구성 가능성"은 없음.
* 불가능한 시나리오에 대한 오류 처리 없음.
* 200줄을 50줄로 줄일 수 있다면 다시 쓸것.

## 3. 수술적 변화
**꼭 필요한 것만 만질것. 자신이 저지른 일만 수습할것.**

기존 코드를 편집할 때:

* 인접한 코드, 주석 또는 서식을 "개선"하지말것.
* 멀쩡한 것을 굳이 리팩토링하지말것.
* 기존 스타일과 일치시킬것.
* 관련 없는 사용되지 않는 코드를 발견하면 삭제하지 말고 언급할것.

변경 사항으로 인해 고아 파일이 생성되는 경우:

* 사용자가 변경하여 더 이상 사용되지 않게 된 임포트/변수/함수를 제거할것.
* 요청받지 않는 한 기존의 사용되지 않는 코드를 삭제하지말것.

## 4. 목표 중심적 실행
**성공 기준을 정의하고, 검증될 떄까지 반복할것.**

이 원칙은 Karpathy가 LLM과 협업할 때 가장 중요한 통찰력이라고 생각하는 부분을 담고 있다.

* 유효성 검사 추가 - 잘못된 입력에 대한 테스트를 작성하고, 그 테스트가 통과하도록 만들것.
* 버그 수정 - 문제를 재현하는 테스트를 작성하고, 그 테스트가 통과하도록 만들것.
* 리팩토링 - 전후 테스트가 모두 통과하는지 확인할것.