# Empty State Design Specification

Version: 1.0

Status: Draft

Owner: Project Atlas

Display Name: Empty State System

Related Documents

- 00_StyleGuide.md
- 01_DesignSystem.md
- 02_Component.md
- 03_Widget.md
- 10_Onboarding.md

---

# Purpose

Empty State는 데이터가 없는 상황에서도
사용자가 다음 행동을 쉽게 이해할 수 있도록 돕는 UX 시스템이다.

Atlas는 Empty State를 오류 화면으로 생각하지 않는다.

Empty State는 사용자를 다음 단계로 안내하는 화면이다.

---

# Design Philosophy

Empty State는

"비어있음"을 보여주는 것이 아니라

"무엇을 해야 하는지"를 알려주는 것이다.

---

# UX Principles

Empty State는 항상 아래 순서를 따른다.

Situation

↓

Reason

↓

Action

---

Example

아직 목표가 없습니다.

↓

목표를 만들면 진행률을 확인할 수 있습니다.

↓

[ 목표 만들기 ]

---

# Empty State Structure

모든 Empty State는 아래 구조를 따른다.

Title

↓

Description

↓

Primary Action

↓

Secondary Action (Optional)

---

# Design Rules

Empty State는

- Card 기반으로 제공한다.
- 화면 중앙 또는 해당 영역 중앙에 배치한다.
- 불필요한 장식 이미지를 사용하지 않는다.
- 사용자가 바로 행동할 수 있는 버튼을 제공한다.

---

# Writing Rules

## Title

현재 상태를 짧고 명확하게 설명한다.

좋은 예

- 아직 목표가 없습니다.
- 아직 계좌가 없습니다.
- 아직 거래 내역이 없습니다.

나쁜 예

- 데이터가 없습니다.
- 오류가 발생했습니다.
- Empty

---

## Description

사용자가 왜 이 화면을 보고 있는지 설명한다.

예)

목표를 만들면 Dashboard에서 진행률을 확인할 수 있습니다.

---

## Action

항상 다음 행동을 제공한다.

예)

[ 목표 만들기 ]

---

# Icon Rules

Version 1

Illustration 사용하지 않는다.

간단한 Outline Icon만 사용한다.

예)

- Goal → Flag
- Asset → Wallet
- Ledger → Receipt
- Investment → Chart

---

# Button Rules

Primary Action은 항상 하나만 제공한다.

Secondary Action은 선택 사항이다.

예)

[ 계좌 등록 ]

[ 나중에 ]

---

# Empty State Types

## First Experience

최초 실행

예)

Onboarding

---

## No Data

데이터가 없는 상태

예)

Goal 없음

---

## No Search Result

검색 결과 없음

예)

"ETF" 검색 결과가 없습니다.

↓

검색 조건을 변경해보세요.

---

## Filter Result Empty

필터 결과 없음

예)

이번 달 거래가 없습니다.

↓

기간을 변경해보세요.

---

## Permission (Future)

Version 2

권한 부족

---

# Screen Templates

## Dashboard

Title

아직 시작하지 않았습니다.

Description

목표와 계좌를 등록하면 Dashboard를 사용할 수 있습니다.

Action

[ 시작하기 ]

---

## Asset

Title

아직 등록된 자산이 없습니다.

Description

첫 번째 자산을 등록해보세요.

Action

[ 자산 등록 ]

---

## Investment

Title

아직 등록된 투자 자산이 없습니다.

Description

투자 자산을 등록하면 수익률을 관리할 수 있습니다.

Action

[ 투자 등록 ]

---

## Goal

Title

아직 목표가 없습니다.

Description

첫 번째 목표를 만들어보세요.

Action

[ 목표 만들기 ]

---

## Ledger

Title

아직 거래 내역이 없습니다.

Description

첫 번째 거래를 기록해보세요.

Action

[ 거래 등록 ]

---

## Management Principles

Version 1에서는 사용하지 않는다.

Template가 항상 존재한다.

---

# Onboarding Relationship

Onboarding과 Empty State는 동일한 철학을 공유한다.

Onboarding

↓

최초 행동

Empty State

↓

다음 행동

둘 다 사용자를 Dashboard로 안내하는 역할을 한다.

---

# Platform Strategy

Desktop

모든 Empty State 지원

---

Mobile

Compact Layout 사용

기능은 동일하게 유지한다.

---

# V1 Scope

포함

- First Experience
- No Data
- No Search Result
- Filter Result Empty

제외

- AI 추천
- 애니메이션
- Illustration
- 사용자 맞춤 Empty State

---

# Future Features

## Version 1.2

- Recommendation 연동
- Empty State 개인화

---

## Version 2

- AI Action 추천
- 상황별 도움말

---

## Version 3

- Mobile 전용 Empty State

---

# Figma AI Prompt

Design a reusable Empty State component system for a desktop finance application.

Requirements

- Clean and minimal
- Center aligned
- Outline icons only
- White background
- Rounded card
- One primary action button
- Optional secondary action
- Professional financial application
- Consistent with Atlas Design System

---

# Review Checklist

- [ ] 다음 행동(Action)이 존재하는가?
- [ ] "데이터가 없습니다."를 사용하지 않는가?
- [ ] Action Button이 하나만 존재하는가?
- [ ] Illustration를 사용하지 않는가?
- [ ] Onboarding과 동일한 철학을 따르는가?
- [ ] Dashboard로 자연스럽게 이어지는가?

---

# Notes

Empty State는 빈 화면이 아니다.

사용자가 다음 행동을 이해하도록 돕는 UX이다.

Atlas에서 Empty State는

Onboarding의 연장선이다.