# Atlas Component System

Version: 1.1

Status: Draft

Owner: Project Atlas

Related Documents

- 00_StyleGuide.md
- 01_DesignSystem.md
- 03_Widget.md
- 04_Dashboard.md

---

# Purpose

Component는 Atlas UI를 구성하는 가장 작은 재사용 가능한 단위이다.

모든 화면은 Component를 조합하여 만들어진다.

Page

↓

Widget

↓

Component

↓

Design Token

---

# Component Philosophy

Component는

한 가지 역할만 수행해야 한다.

하나의 Component가

두 가지 이상의 책임을 가지면 안 된다.

---

# Component Hierarchy

Foundation

↓

Basic Component

↓

Financial Component

↓

Layout Component

↓

Complex Component

↓

Widget

↓

Page

---

# Component Contract

모든 Component는 아래 구조를 따른다.

Purpose

↓

Props

↓

Variants

↓

States

↓

Interaction

↓

Accessibility

↓

Composition Rules

---

# Foundation

Foundation은 UI의 가장 기본 요소이다.

포함

- Color
- Typography
- Spacing
- Radius
- Shadow
- Motion

Foundation은 DesignSystem과 StyleGuide에서 관리한다.

---

# Basic Components

## Button

Purpose

사용자의 행동을 실행한다.

Variants

- Primary
- Secondary
- Ghost
- Danger

States

- Default
- Hover
- Focus
- Disabled
- Loading

Usage

- Primary Button은 한 화면에 최대 2개
- Danger Button은 삭제 기능에서만 사용

---

## Input

Purpose

사용자의 데이터를 입력받는다.

Variants

- Text
- Number
- Currency
- Percentage

States

- Empty
- Filled
- Error
- Disabled

Rule

Placeholder는 설명이 아니다.

Label은 항상 표시한다.

---

## Badge

Purpose

상태를 간단하게 표시한다.

Examples

- Active
- Disabled
- Completed

---

## Chip

Purpose

필터 또는 선택 상태를 표현한다.

Examples

- Purpose Toggle
- Account Toggle
- Investment Type

---

## Icon

Library

Lucide

Style

Outline

Rule

아이콘은 의미 전달을 위한 보조 요소이다.

---

# Financial Components

Atlas 전용 컴포넌트

---

## Money

Purpose

금액 표시

Props

- value
- currency
- showSign

States

- Positive
- Negative
- Zero

Rules

- 오른쪽 정렬
- 천 단위 구분
- 통화 기호 표시

Example

₩82,350,000

---

## Percentage

Purpose

비율 표시

States

- Positive
- Negative
- Neutral

Example

+12.35%

---

## Trend

Purpose

증감 표시

Elements

- Arrow
- Value

Examples

▲ +120만원

▼ -30만원

---

## Goal Progress

Purpose

목표 진행률 표시

Elements

- Progress Bar
- Percentage
- Current
- Target

---

## Purpose Badge

Purpose

자산의 사용 목적 표시

Examples

생활비

비상금

내집마련

장기투자

---

## Account Badge

Purpose

계좌 종류 표시

Examples

입출금

예금

ISA

연금저축

증권

---

# Layout Components

## Card

Purpose

하나의 정보를 담는다.

Rule

Card 안에 Card를 중첩하지 않는다.

---

## Section

Purpose

관련 Card를 그룹화한다.

---

## Divider

Purpose

정보를 구분한다.

---

## Header

Purpose

페이지 제목과 주요 Action을 제공한다.

---

## Container

Purpose

레이아웃 폭을 제한한다.

---

# Complex Components

복수의 Component를 조합한 컴포넌트

---

## NetWorthCard

구성

- Card
- Money
- Trend

---

## GoalCard

구성

- Card
- Goal Progress

---

## InvestmentCard

구성

- Card
- Money
- Percentage

---

## RecommendationCard

구성

- Card
- Icon
- Button

---

# Composition Rules

Component는 아래 방향으로만 조합할 수 있다.

Foundation

↓

Basic

↓

Financial

↓

Layout

↓

Complex

↓

Widget

↓

Page

역방향 참조는 금지한다.

---

# Component States

모든 Component는 가능한 경우 아래 상태를 지원한다.

- Default
- Hover
- Focus
- Disabled
- Loading
- Error

지원하지 않는 경우 명시한다.

---

# Accessibility

모든 Component는

- Keyboard Navigation
- Focus Visible
- Screen Reader

를 지원한다.

색상만으로 상태를 표현하지 않는다.

---

# Figma Rules

모든 Component는 Variant를 사용한다.

예시

Button

- Type
- Size
- State

Chip

- Selected
- Unselected

Money

- Positive
- Negative
- Neutral

---

# React Rules

Component는 하나의 파일로 관리한다.

예시

Button.tsx

Money.tsx

GoalProgress.tsx

RecommendationCard.tsx

---

# Naming Rules

Component

PascalCase

Props

camelCase

Boolean

isEnabled

hasValue

canEdit

---

# Folder Structure

/components

/ui

- Button
- Input
- Badge
- Chip
- Icon

/financial

- Money
- Percentage
- Trend
- GoalProgress
- PurposeBadge
- AccountBadge

/layout

- Card
- Container
- Header
- Section
- Divider

/complex

- NetWorthCard
- GoalCard
- InvestmentCard
- RecommendationCard

---

# Future Components

Version 1.2

- ChartCard
- BudgetCard
- MonthlyReportCard

Version 2

- AIRecommendationCard
- ScenarioCard
- SimulationCard

---

# Review Checklist

- [ ] 하나의 역할만 수행하는가?
- [ ] 재사용 가능한가?
- [ ] Widget에 종속되지 않는가?
- [ ] Accessibility를 지원하는가?
- [ ] Figma Variant로 표현 가능한가?
- [ ] React에서 독립 Component로 구현 가능한가?
- [ ] Composition Rule을 위반하지 않는가?

---

# Version History

## v1.0

- Initial Component System
- Financial Components 정의
- Component Contract 정의
- Composition Rules 정의