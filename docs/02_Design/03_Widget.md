# Atlas Widget System

Version: 1.0

Status: Draft

Related Documents

- 01_DesignSystem.md
- 02_Component.md
- 04_Dashboard.md
- 05_Asset.md
- 06_Investment.md

---

# Purpose

Widget은 Atlas의 가장 작은 기능 단위이다.

모든 화면(Page)은 Widget을 조합하여 구성한다.

Widget은 특정 화면에 종속되지 않는다.

하나의 Widget은 하나의 역할만 수행한다.

---

# Widget Philosophy

Atlas는 Page 중심이 아니라 Widget 중심으로 설계한다.

Page는 Widget을 배치하는 공간이다.

Widget은 여러 화면에서 재사용될 수 있어야 한다.

---

# Widget Hierarchy

```

Primitive

↓

Component

↓

Widget

↓

Page

```

---

예시

```

Text

↓

Card

↓

NetWorth Widget

↓

Dashboard

```

---

# Widget Rules

모든 Widget은

- 독립적으로 동작한다.
- 하나의 목적만 가진다.
- 재사용 가능해야 한다.
- 다른 Widget에 의존하지 않는다.
- 상태(State)를 가진다.
- 클릭 가능한 경우 이동 위치를 정의한다.

---

# Widget Layout

모든 Widget은 다음 구조를 가진다.

```

Header

↓

Content

↓

Footer(Optional)

↓

Action(Optional)

```

---

# Widget Size

Widget는 크기를 가진다.

Small

Medium

Large

Full Width

모든 Widget은 반응형을 지원한다.

---

# Widget Categories

Atlas Widget은 다음과 같이 분류한다.

---

## Summary Widgets

현재 상태를 보여준다.

예)

- Net Worth
- Monthly Income
- Monthly Expense
- Investment Value

---

## Progress Widgets

목표 진행률을 보여준다.

예)

- Goal Progress
- House Progress
- Savings Progress
- Investment Progress

---

## Analysis Widgets

데이터를 분석한다.

예)

- Asset Allocation
- Monthly Report
- Expense Analysis
- Income Analysis

---

## Recommendation Widgets

다음 행동을 제안한다.

예)

- Recommendation
- Warning
- Opportunity

---

## Navigation Widgets

다른 화면으로 이동한다.

예)

- Quick Action
- Shortcut
- Favorite

---

## Financial Widgets

금융 정보를 표현한다.

예)

- Account Summary
- Investment Summary
- Portfolio
- Bond Summary

---

# Standard Widgets

Version 1에서 사용하는 Widget

---

## Net Worth Widget

목적

현재 순자산 표시

정보

- 순자산
- 증감액
- 증감률

Click

Asset 화면

---

## Asset Allocation Widget

목적

자산 비중 표시

지원

- 목적 기준
- 계좌 기준

Chart

Donut Chart

Click

Asset 화면

---

## Goal Progress Widget

목적

목표 달성률 표시

정보

- 목표 금액
- 현재 금액
- 진행률

Click

Goal 화면

---

## Recommendation Widget

목적

사용자가 지금 해야 할 행동 제안

예)

생활계좌 잔액이 많습니다.

↓

예금으로 이동하세요.

또는

ISA 추가 납입 가능합니다.

또는

이번 달 소비가 높습니다.

Click

관련 화면

---

## Monthly Summary Widget

이번 달 요약

수입

지출

저축

투자

---

## Investment Widget

투자 현황

ETF

채권

코인

평가금액

수익률

Click

Investment

---

## Recent Transaction Widget

최근 거래

최근 입출금

최근 투자

최근 소비

Click

Ledger

---

## Goal Widget

목표 카드

목표

현재

남은 금액

예상 달성일

---

## Quick Add Widget

빠른 등록

자산

투자

거래

---

# Widget State

Default

Loading

Empty

Success

Warning

Error

---

# Widget Interaction

Hover

약한 Shadow

Click

Page 이동

Loading

Skeleton

Animation

150~250ms

---

# Widget Communication

Widget은 직접 통신하지 않는다.

모든 데이터는 중앙 Store를 통해 전달한다.

예)

Asset Allocation Widget

↓

Global Store

↓

Investment Widget

---

# Widget Refresh

Widget은 개별적으로 새로고침 가능해야 한다.

Dashboard 전체를 새로고침하지 않는다.

---

# Widget Configuration

Widget은 설정을 가진다.

예)

Asset Allocation

보기 기준

● 목적

○ 계좌

---

Goal Widget

기간

1년

5년

전체

---

Investment Widget

보기

전체

ETF

채권

코인

---

# Widget Priority

Dashboard에서 중요도

1

Recommendation

2

Net Worth

3

Goal Progress

4

Asset Allocation

5

Investment

6

Monthly Summary

7

Recent Transaction

---

# Widget Naming

Widget 이름은

PascalCase

사용

예)

NetWorthWidget

RecommendationWidget

GoalWidget

InvestmentWidget

AssetAllocationWidget

---

# Widget Folder

```

widgets/

NetWorth/

AssetAllocation/

Recommendation/

Investment/

Goal/

MonthlySummary/

QuickAdd/

```

---

# Future Widgets

AI Report

Cash Flow

Tax Report

Retirement Forecast

Risk Analysis

Portfolio Score

Expense Prediction

Market News

---

# Widget Checklist

새 Widget을 만들기 전에

□ 하나의 역할만 수행하는가

□ 재사용 가능한가

□ 다른 Widget에 의존하지 않는가

□ Component만 사용했는가

□ Dashboard 외에서도 사용할 수 있는가

□ 클릭 동작이 정의되어 있는가

□ Empty 상태가 있는가

□ Loading 상태가 있는가

---

# Widget Design Principles

Widget은

예쁜 카드가 아니다.

Widget은

사용자의 하나의 질문에 답하는 기능이다.

예)

"나는 지금 얼마를 가지고 있지?"

↓

NetWorth Widget

"내집마련은 얼마나 진행됐지?"

↓

Goal Progress Widget

"다음에 뭘 해야 하지?"

↓

Recommendation Widget

---
## Platform Strategy
Widget는

Desktop에서는

Large Card

Mobile에서는

Compact Card

로 변경될 수 있다.

# Version History

v1.0

Initial Widget System