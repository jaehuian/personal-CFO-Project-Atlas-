# Atlas Widget System

Version: 1.1

Status: Draft

Owner: Project Atlas

Related Documents

- 00_StyleGuide.md
- 01_DesignSystem.md
- 02_Component.md
- 04_Dashboard.md

---

# Purpose

Widget는 Atlas의 핵심 기능 단위이다.

Page는 Widget를 조합하여 만들어지며,

Widget는 Component를 조합하여 만들어진다.

Page

↓

Widget

↓

Component

↓

Design Token

---

# Widget Philosophy

Widget는

하나의 질문(Question)에 답해야 한다.

질문이 두 개 이상이라면

Widget를 분리한다.

---

# Widget Contract

모든 Widget는 아래 구조를 가진다.

Question

↓

Primary KPI

↓

Secondary KPI (Optional)

↓

Insight (Optional)

↓

Action

↓

Target Page

---

# Widget Rules

Widget는

하나의 역할만 수행한다.

Widget는

독립적으로 재사용 가능해야 한다.

Widget는

Page를 알지 못한다.

Navigation은 부모(Page)가 처리한다.

---

# Widget Hierarchy

Component

↓

Widget

↓

Page

Widget는 Component를 포함하지만,

Page를 포함하지 않는다.

---

# Widget Priority

## High

사용자가 매일 확인하는 정보

예)

- Net Worth
- Recommendation

---

## Medium

자주 확인하는 정보

예)

- Goal
- Investment
- Asset Allocation

---

## Low

참고 정보

예)

- Monthly Spending
- Recent Transactions

---

# Standard Widget Structure

모든 Widget는 아래 레이아웃을 따른다.

```
Title

↓

Primary KPI

↓

Secondary KPI

↓

Action
```

복잡한 Widget도 이 구조를 유지한다.

---

# Widget List

## Net Worth Widget

Question

현재 내 자산은 얼마인가?

Primary KPI

순자산

Secondary KPI

이번 달 증감

Action

Asset 이동

Priority

High

Components

- Card
- Money
- Trend

---

## Recommendation Widget

Question

지금 무엇을 해야 하는가?

Primary KPI

추천 내용

Secondary KPI

추천 이유

Action

관련 화면 이동

Priority

High

Components

- Card
- Icon
- Button

---

## Asset Allocation Widget

Question

내 자산은 어떻게 구성되어 있는가?

Primary KPI

도넛 차트

Secondary KPI

Purpose / Account Toggle

Action

Asset 이동

Priority

Medium

Components

- Card
- Donut Chart
- Chip

---

## Goal Widget

Question

목표까지 얼마나 남았는가?

Primary KPI

진행률

Secondary KPI

현재 / 목표 금액

Action

Goal 이동

Priority

Medium

Components

- Card
- Goal Progress

---

## Investment Widget

Question

현재 투자는 어떤 상태인가?

Primary KPI

총 평가금액

Secondary KPI

총 수익률

Action

Investment 이동

Priority

Medium

Components

- Card
- Money
- Percentage

---

## Ledger Widget

Question

이번 달 얼마나 사용했는가?

Primary KPI

총 지출

Secondary KPI

지난달 대비

Action

Ledger 이동

Priority

Low

Components

- Card
- Money
- Trend

---

# Widget State

모든 Widget는 다음 상태를 가진다.

- Loading
- Empty
- Ready
- Error

---

# Empty State Rules

Widget는

"데이터가 없습니다."

를 표시하지 않는다.

항상 다음 행동(Action)을 함께 제공한다.

예)

계좌가 없습니다.

↓

[계좌 등록]

---

# Loading Rules

Skeleton 사용

Spinner 최소화

---

# Interaction Rules

Widget 전체를 클릭 가능하게 만든다.

Hover

↓

Shadow

↓

Pointer Cursor

Action Button이 있는 경우

Button이 우선한다.

---

# Navigation Rules

Widget는

Target Page만 가진다.

Page 이동은 Router가 처리한다.

Widget 내부에서 Navigation을 수행하지 않는다.

---

# Composition Rules

Widget는

Component를 조합하여 만든다.

Widget끼리는 중첩하지 않는다.

예)

NetWorth Widget

↓

Card

Money

Trend

Button

---

# Responsive Rules

Desktop

모든 정보 표시

Tablet

Secondary KPI 일부 축약

Mobile

Primary KPI 중심

Action 유지

기능은 동일하게 유지한다.

표현만 변경한다.

---

# Accessibility

Keyboard Navigation 지원

Focus Visible 지원

Screen Reader 지원

Widget Title을 항상 제공한다.

---

# Figma Rules

Widget는 하나의 Component Set으로 관리한다.

Variant

- State
- Size
- Theme (Future)

Auto Layout 사용

---

# React Rules

Widget는 독립 폴더를 가진다.

예)

widgets/

NetWorthWidget/

RecommendationWidget/

GoalWidget/

AssetAllocationWidget/

---

# Folder Structure

/widgets

NetWorthWidget

RecommendationWidget

GoalWidget

InvestmentWidget

LedgerWidget

AssetAllocationWidget

---

# Future Widgets

Version 1.2

- Monthly Report Widget
- Spending Analysis Widget

Version 2

- AI Recommendation Widget
- Simulation Widget

Version 3

- Mobile Quick Action Widget

---

# Review Checklist

- [ ] 하나의 질문에만 답하는가?
- [ ] Component만 조합하는가?
- [ ] Widget를 중첩하지 않는가?
- [ ] Dashboard 철학과 일치하는가?
- [ ] 독립적으로 재사용 가능한가?
- [ ] Navigation이 분리되어 있는가?
- [ ] Empty State가 Action을 제공하는가?

---

# Version History

## v1.1

- Widget Contract 추가
- Widget Priority 추가
- Insight 개념 추가
- Navigation Rule 추가
- Responsive Rule 추가
- Dashboard 구조와 통합