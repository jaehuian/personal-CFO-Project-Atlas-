# Dashboard Specification

Version: 1.0

Status: Draft

Owner: Project Atlas

Related Documents

- README.md
- ../00_Common/01_Glossary.md
- ../01_Product/01_Vision.md
- ../01_Product/02_RuleBook.md
- ../01_Product/03_UserFlow.md
- 05_Asset.md
- 06_Investment.md
- 07_Goal.md
- 08_Ledger.md
- 09_MyRules.md

---

# Purpose

Dashboard는 Atlas의 시작 화면이며 가장 중요한 화면이다.

사용자는 Dashboard 하나만으로 현재 자산 상태를 이해하고,
다음에 해야 할 행동을 결정할 수 있어야 한다.

Dashboard는 데이터를 수정하는 화면이 아니다.

Dashboard는 **현재 상태를 이해하고 의사결정을 내리는 화면**이다.

---

# Dashboard Philosophy

Dashboard는 정보를 많이 보여주는 화면이 아니다.

Dashboard는 가장 중요한 정보만 보여준다.

Atlas는 다음 세 가지 질문에 답해야 한다.

1. 지금 내 자산은 어떤 상태인가?
2. 무엇이 달라졌는가?
3. 지금 무엇을 해야 하는가?

---

# UX Principle

Dashboard는 항상 아래 흐름을 따른다.

Observe

↓

Understand

↓

Act

사용자는 Dashboard에서

- 현재 상태를 확인하고
- 이유를 이해하고
- 필요한 화면으로 이동한다.

---

# Dashboard Rules

Dashboard에서는

- 생성(Create)
- 수정(Edit)
- 삭제(Delete)

를 지원하지 않는다.

Dashboard에서는

- 확인(Observe)
- 판단(Understand)
- 이동(Navigate)

만 지원한다.

---

# Information Hierarchy

## High Priority

- 순자산
- Recommendation

---

## Medium Priority

- 자산 비중
- 목표 진행률
- 투자 현황

---

## Low Priority

- 이번 달 소비

Dashboard에는 Low Priority 이하의 정보를 추가하지 않는다.

---

# Layout

```
┌────────────────────────────────────────────────────────────┐

오늘도 목표에 한 걸음 가까워졌습니다.

────────────────────────────────────────────────────────────

① 순자산

────────────────────────────────────────────────────────────

② 자산 비중

③ 목표 진행률

────────────────────────────────────────────────────────────

④ 투자

⑤ 이번 달 소비

────────────────────────────────────────────────────────────

⑥ Recommendation

────────────────────────────────────────────────────────────
```

Dashboard는 1~1.5 화면 안에서 모든 핵심 정보를 제공해야 한다.

---

# Widget Architecture

모든 Widget은 동일한 구조를 따른다.

Question

↓

Primary KPI

↓

Secondary KPI

↓

Action

↓

Target Page

---

# Widget Specification

## 1. Net Worth Widget

### Question

현재 내 자산은 얼마인가?

### Primary KPI

- 총 순자산

### Secondary KPI

- 이번 달 자산 증감

### Click

Asset

### Priority

High

---

## 2. Asset Allocation Widget

### Question

내 자산은 어떻게 구성되어 있는가?

### Primary KPI

- 도넛 차트

### Toggle

- Purpose
- Account

### Click

Asset

### Priority

Medium

---

## 3. Goal Widget

### Question

목표까지 얼마나 남았는가?

### Primary KPI

- 대표 목표 진행률

### Secondary KPI

- 목표 금액
- 현재 금액

### Click

Goal

### Priority

Medium

---

## 4. Investment Widget

### Question

현재 투자는 어떤 상태인가?

### Primary KPI

- 총 평가금액

### Secondary KPI

- 총 수익률

### Click

Investment

### Priority

Medium

---

## 5. Ledger Widget

### Question

이번 달 얼마나 사용했는가?

### Primary KPI

- 이번 달 총 지출

### Secondary KPI

- 지난달 대비 증감

### Click

Ledger

### Priority

Low

---

## 6. Recommendation Widget

### Question

지금 무엇을 하면 좋은가?

Recommendation은 항상 다음 구조를 따른다.

Current State

↓

Reason

↓

Recommendation

↓

Action

Example

생활계좌 잔액

230만원

↓

관리 원칙

100만원 유지

↓

130만원을 예금으로 이동하는 것을 추천합니다.

↓

Asset 화면 이동

### Priority

High

---

# Navigation Rules

Dashboard의 모든 Widget은 해당 화면으로 이동한다.

Net Worth

↓

Asset

---

Asset Allocation

↓

Asset

---

Goal

↓

Goal

---

Investment

↓

Investment

---

Ledger

↓

Ledger

---

Recommendation

↓

관련 화면

---

# Recommendation Rules

Recommendation은 아래 우선순위를 따른다.

1. Management Principles
2. Goal
3. Asset
4. Investment
5. Ledger

Recommendation은 자동 실행하지 않는다.

항상 사용자가 직접 결정한다.

---

# Empty State

최초 실행 시

```
환영합니다.

Atlas를 시작해볼까요?

1. 계좌 등록

2. 자산 등록

3. 목표 설정

4. 관리 원칙 설정

[ 시작하기 ]
```

"데이터가 없습니다."는 사용하지 않는다.

---

# Platform Strategy

## Desktop

모든 Widget 제공

모든 Navigation 제공

---

## Mobile (V3)

지원

- 순자산
- 목표
- 투자
- Recommendation
- 빠른 거래 등록

제한

- Dashboard 편집
- 복잡한 관리 기능

---

# V1 Scope

포함

- 순자산
- 자산 비중
- 목표 진행률
- 투자 현황
- 이번 달 소비
- Recommendation
- Widget Navigation

제외

- 예산(Budget)
- Widget 편집
- 사용자 지정 Dashboard
- AI Recommendation

---

# Future Features

Version 1.2

- 월간 리포트
- 소비 분석

Version 2

- Widget 커스터마이징
- AI Recommendation

Version 3

- Mobile Companion Dashboard

---

# Definition of Done

- Net Worth Widget
- Asset Allocation Widget
- Goal Widget
- Investment Widget
- Ledger Widget
- Recommendation Widget
- Navigation
- Empty State
- Desktop Layout

---

# Figma AI Prompt

Design a modern desktop dashboard for a personal finance application called Atlas.

Style

- Professional
- Minimal
- White background
- Soft shadows
- Rounded cards (16px)
- 8px spacing system
- Financial dashboard
- Desktop (1440px)

Requirements

- Dashboard is the Home screen.
- Six widgets only.
- Large Net Worth widget.
- Asset Allocation with Purpose / Account toggle.
- Goal progress widget.
- Investment summary widget.
- Monthly spending widget.
- Recommendation widget.
- Widget-based navigation.
- No sidebar navigation.
- Prioritize readability over decoration.
- Dashboard should fit within one screen without excessive scrolling.

---

# Review Checklist

- [ ] Dashboard가 Home 역할을 하는가?
- [ ] Dashboard에서 수정 기능이 없는가?
- [ ] 모든 Widget가 하나의 질문에 답하는가?
- [ ] Observe → Understand → Act 흐름을 만족하는가?
- [ ] Recommendation이 Current → Reason → Recommendation → Action 구조를 따르는가?
- [ ] Dashboard가 1~1.5 화면 안에서 끝나는가?
- [ ] Desktop First 원칙을 따르는가?
- [ ] V1 범위를 벗어나지 않는가?

---

# Notes

Dashboard는 Atlas의 핵심 화면이다.

사용자는 Dashboard를 통해 현재 상태를 이해하고,
필요한 화면으로 이동하여 관리 작업을 수행한다.

Dashboard는 정보를 입력하는 화면이 아니라,
의사결정을 돕는 화면이다.