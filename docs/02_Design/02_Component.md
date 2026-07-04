# Atlas Component System

Version: 2.0

Status: Architecture Freeze Candidate

Owner: Project Atlas

Related Documents

- 00_StyleGuide.md
- 01_DesignSystem.md
- 03_Widget.md

---

# Purpose

Component는 Atlas UI를 구성하는 가장 작은 재사용 단위이다.

모든 화면(Page)은 Component를 조합하여 구성한다.

Component는 비즈니스 로직을 가지지 않는다.

---

# Design Philosophy

Atlas는 Component First를 원칙으로 한다.

새로운 화면보다 새로운 Component를 먼저 설계한다.

Component는 하나의 책임만 가져야 한다.

---

# UI Hierarchy

Foundation

↓

Component

↓

Widget

↓

Page

---

# Component Rules

모든 Component는

- 재사용 가능해야 한다.
- 하나의 역할만 수행해야 한다.
- 독립적으로 테스트 가능해야 한다.
- Theme 변경에 영향을 받지 않아야 한다.

---

# Component Categories

Atlas는 아래 Component를 제공한다.

## Foundation Components

- Button
- Input
- Select
- Switch
- Checkbox
- Badge
- Tag
- Divider
- Icon

---

## Layout Components

- Card
- Section
- Panel
- Grid
- Stack
- Tabs

---

## Domain Components

- SummaryCard
- PurposeCard
- AssetCard
- AccountCard
- InvestmentCard
- GoalCard
- RecommendationCard
- RuleCard
- TransactionRow

---

## Feedback Components

- EmptyState
- Toast
- Dialog
- Tooltip

---

# Foundation Components

## Button

용도

사용자의 Action 수행

Variants

- Primary
- Secondary
- Ghost
- Danger

States

- Default
- Hover
- Active
- Disabled
- Loading

---

## Input

지원

- Text
- Number
- Currency
- Search

---

## Select

지원

- Single Select
- Multi Select (V2)

---

## Switch

ON/OFF

Rule

Boolean 값만 사용한다.

---

# Layout Components

## Card

모든 Domain Card의 부모 Component

공통 속성

- Radius 16px
- Padding 24px
- Border
- Hover Shadow

Card 자체는 데이터 의미를 가지지 않는다.

---

## Tabs

Purpose / Account

Purpose / Investment Type

등 View Toggle에서 사용한다.

---

# Domain Components

## SummaryCard

사용 화면

- Dashboard
- Asset
- Investment
- Goal
- Ledger

표시 정보

- Title
- Value
- Description (Optional)
- Trend (Optional)

---

## PurposeCard ⭐

Atlas의 핵심 Component

사용 화면

- Dashboard
- Purpose
- Asset
- Investment

표시

- Purpose 이름
- 총 자산
- Goal 진행률(Optional)
- Asset 수
- Investment 수

Action

Click

Purpose Detail 이동

---

## AssetCard

사용 화면

- Asset

표시

- 자산명
- 평가금액
- Purpose
- Account

---

## AccountCard

사용 화면

- Asset

표시

- 계좌명
- 종류
- 총 자산

---

## InvestmentCard

사용 화면

- Investment

표시

- 종목명
- 수익률
- 평가금액
- Purpose

---

## GoalCard

사용 화면

- Dashboard
- Goal

표시

- 목표명
- 진행률
- 목표금액
- 현재금액

---

## RecommendationCard

사용 화면

- Dashboard

표시

- 제목
- 설명
- 추천 이유
- Action

---

## RuleCard

사용 화면

- Management Principles

표시

- Rule 이름
- 값
- Switch

---

## TransactionRow

사용 화면

- Ledger

표시

- 날짜
- 금액
- 카테고리
- Account

---

# Feedback Components

## EmptyState

사용 화면

모든 화면

구성

- Icon
- Title
- Description
- Primary Button

---

## Dialog

사용

삭제 확인

주의 확인

---

## Toast

사용

저장 완료

삭제 완료

오류

---

# Component Composition

Component는 다른 Component를 포함하지 않는다.

Widget에서 Component를 조합한다.

예)

Purpose Widget

├── SummaryCard

├── PurposeCard

└── ProgressRing

---

# Naming Rules

컴포넌트 이름은

도메인 중심으로 작성한다.

좋은 예

- PurposeCard
- GoalCard
- AssetCard

나쁜 예

- BlueCard
- FinanceBox
- LargeCard

---

# Props Guidelines

모든 Component는

- 최소한의 Props만 가진다.
- 비즈니스 로직을 포함하지 않는다.
- Domain 객체를 직접 수정하지 않는다.

---

# Accessibility

모든 Component는

- Keyboard Navigation
- Focus
- Screen Reader

를 지원해야 한다.

---

# Platform Strategy

Desktop

모든 Component 지원

Mobile

동일한 Component 사용

Layout만 변경

---

# Version 1 Scope

포함

- Foundation
- Layout
- Domain
- Feedback

제외

- Animation
- Skeleton
- Chart Component
- AI Component

---

# Future Features

## Version 1.2

- Skeleton
- Statistic Card
- Timeline

## Version 2

- Drag & Drop
- Chart Component
- Smart Search

## Version 3

- Mobile Optimized Component
- Adaptive Layout

---

# Review Checklist

- [ ] Component가 하나의 역할만 가지는가?
- [ ] Widget와 역할이 구분되는가?
- [ ] Domain 중심 이름을 사용하는가?
- [ ] 재사용 가능한가?
- [ ] PurposeCard가 공통 Component인가?
- [ ] Dashboard와 연결되는가?

---

# Notes

Atlas는

Page First가 아니라

Component First를 따른다.

모든 화면은

Component를 조합하여 만들어진다.

Component는 Atlas UI의 가장 작은 재사용 단위이다.