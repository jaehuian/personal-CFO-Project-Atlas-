# Atlas RuleBook

Version: 1.1

Status: Draft

Owner: Project Atlas

Related Documents

- README.md
- 00_Common/01_Glossary.md
- 01_Vision.md
- 03_UserFlow.md

---

# Purpose

RuleBook은 Atlas의 설계 원칙을 정의한다.

모든 기획, 디자인, 개발은 본 문서를 기준으로 판단한다.

기능 추가 또는 변경 시 RuleBook을 우선 검토한다.

---

# Core Principles

## 1. Goal First

모든 기능은 사용자의 목표 달성을 돕기 위해 존재한다.

자산은 목적(Purpose)을 가지며,

Purpose는 Goal과 연결된다.

---

## 2. Dashboard First

Dashboard는 Atlas의 시작 화면이다.

사용자는 Dashboard 하나만으로

현재 상태와 다음 행동을 이해할 수 있어야 한다.

---

## 3. Recommendation over Automation

Atlas는 자동으로 행동하지 않는다.

추천을 제공하지만,

최종 결정은 항상 사용자가 내린다.

자동 실행은 V1 범위에 포함하지 않는다.

---

## 4. Simplicity First

복잡한 기능보다

이해하기 쉬운 경험을 우선한다.

설정보다 좋은 기본값(Default)을 제공한다.

---

## 5. Desktop First

Atlas는 생산성 도구이다.

Desktop을 기준으로 설계한다.

모바일은 Companion App으로 제공한다.

---

## 6. Consistency over Uniformity

모든 화면이 같은 형태일 필요는 없다.

하지만 동일한 경험을 제공해야 한다.

기능보다 사용 목적이 우선이다.

---

## 7. Template First

사용자가 직접 규칙을 만드는 것보다

Atlas가 준비한 Template를 우선 제공한다.

직접 생성 기능은 V2 이후 지원한다.

---

# Data Principles

## Purpose

모든 자산은 반드시 하나의 Purpose를 가진다.

Purpose는 Atlas의 핵심 데이터이다.

---

## Account

Account는 자산의 저장 위치이다.

Purpose와 동일한 개념이 아니다.

---

## Goal

Goal은 Purpose와 연결된다.

Goal은 Asset를 직접 관리하지 않는다.

---

## Transfer Rule

이체는

- 수입이 아니다.
- 지출이 아니다.

이체는 자산의 위치만 변경한다.

---

## Market Value Rule

모든 진행률과 자산 비중은

평가금액(Market Value)을 기준으로 계산한다.

매수금액은 투자 분석에만 사용한다.

---

# UX Principles

## Dashboard

Dashboard에서는

데이터를 직접 수정하지 않는다.

Dashboard는

현재 상태와 추천만 제공한다.

---

## Asset

Asset는

"내 돈은 어디에 있는가?"

를 보여준다.

---

## Investment

Investment는

"내 투자는 건강한가?"

를 보여준다.

---

## Goal

Goal은

"목표까지 얼마나 남았는가?"

를 보여준다.

---

## Ledger

Ledger는

거래를 기록한다.

분석은 Dashboard가 담당한다.

---

## Management Principles

사용자는 Rule를 만드는 것이 아니라

자신만의 관리 원칙을 설정한다.

---

# Recommendation Rules

Recommendation은 다음 우선순위를 따른다.

1. 사용자 관리 원칙
2. 시스템 기본 원칙
3. 일반 추천

Recommendation은 항상

사용자가 무시할 수 있어야 한다.

---

# Version Rules

Version 1

필수 기능만 구현한다.

Version 1.2

사용성을 개선한다.

Version 2

고급 관리 기능을 추가한다.

Version 3

모바일 Companion App을 지원한다.

---

# Scope Rules

새로운 기능은 다음 질문을 통과해야 한다.

- Goal 달성에 도움이 되는가?
- Dashboard와 연결되는가?
- V1 범위를 벗어나지 않는가?
- 사용자가 쉽게 이해할 수 있는가?

하나라도 "아니오"라면 V2 이후로 연기한다.

---

# Design Rules

모든 화면은

- Widget 기반
- Card 기반
- White Space 중심
- 최소한의 설정

을 따른다.

---

# Naming Rules

사용자에게 보여지는 용어와

개발 용어를 구분한다.

예)

UI

관리 원칙

↓

Code

Rule

---

# Platform Rules

Desktop

Primary Platform

모든 기능 제공

---

Mobile

Companion Platform

조회

간단한 입력

간단한 수정

복잡한 관리 기능은 Desktop에서만 제공한다.

---

# Future Rules

향후 추가될 기능도

본 RuleBook을 우선 따른다.

새로운 기능이 RuleBook과 충돌한다면

기능보다 RuleBook을 우선 수정한다.

---

# Version History

## v1.1

- Desktop First 원칙 추가
- Mobile Companion 전략 추가
- Recommendation Rule 추가
- Template First 원칙 추가
- Transfer Rule 추가
- Market Value Rule 추가
- Scope Rule 추가
- Version Rule 추가
- Naming Rule 추가