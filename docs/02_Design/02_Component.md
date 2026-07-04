# Atlas Component System

Version: 1.0

Status: Draft

Related Documents

- 01_DesignSystem.md
- 03_Widget.md

---

# Purpose

Atlas에서 사용하는 모든 UI Component의 규칙을 정의한다.

모든 화면은 Component를 조합하여 구성한다.

새로운 UI를 만들기 전에 기존 Component를 먼저 사용한다.

Component는 재사용 가능해야 하며, 특정 화면에 종속되어서는 안 된다.

---

# Component Hierarchy

Atlas는 다음 계층 구조를 따른다.

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
Button

↓

Action Button

↓

Recommendation Widget

↓

Dashboard
```

---

# Design Principles

모든 Component는

- 재사용 가능해야 한다.
- 독립적으로 동작해야 한다.
- 상태(State)를 가져야 한다.
- 화면에 종속되면 안 된다.
- 하나의 역할만 수행한다.

---

# Primitive Components

Primitive는 가장 작은 UI 단위이다.

예)

Button

Input

Checkbox

Radio

Toggle

Chip

Badge

Divider

Avatar

Progress

Icon

Tooltip

Spinner

Skeleton

---

# Layout Components

레이아웃을 구성한다.

Container

Section

Stack

Grid

Row

Column

Spacer

Divider

Card Container

Scroll Area

---

# Surface Components

화면의 영역을 표현한다.

Card

Dialog

Modal

Bottom Sheet

Popover

Accordion

Tab

Collapse

Panel

---

# Navigation Components

Navigation을 담당한다.

Back Button

Tab

Segment Control

Breadcrumb

Bottom Navigation

Navigation Header

---

# Data Components

데이터를 표현한다.

Statistic Card

Value Card

Chart Card

Table

Timeline

Progress Card

Goal Card

Tag

Status Badge

---

# Input Components

사용자 입력

Text Input

Number Input

Currency Input

Date Picker

Select Box

Search

Toggle

Switch

Slider

---

# Feedback Components

사용자 피드백

Toast

Snackbar

Alert

Loading

Skeleton

Empty State

Confirmation Dialog

---

# Financial Components

Atlas 전용 Component

Account Card

Investment Card

Asset Card

Goal Card

Recommendation Card

Transaction Card

Budget Card

Portfolio Card

Rule Card

---

# Card Rules

Atlas는 Card 중심 UI를 사용한다.

Card는

제목

↓

내용

↓

보조 정보

↓

Action

구조를 가진다.

---

Card 예시

```
순자산

82,000,000원

▲ 2.3%

>

```

---

# Button Rules

Primary

가장 중요한 Action

Secondary

보조 Action

Ghost

텍스트 Action

Danger

삭제

Icon

아이콘 버튼

Floating Button은 사용하지 않는다.

---

# Input Rules

Label은 항상 표시한다.

Placeholder는 설명이 아니다.

Validation은 입력 즉시 수행한다.

에러 메시지는 Input 아래에 표시한다.

---

# Table Rules

가능하면 사용하지 않는다.

반드시 필요한 경우에만 사용한다.

모바일에서는 Card 형태로 변경한다.

---

# Chart Rules

기본

Donut

↓

Bar

↓

Line

차트에는 반드시

Label

Value

단위를 표시한다.

색상만으로 구분하지 않는다.

---

# Empty State

데이터가 없는 경우

아이콘

↓

설명

↓

Action Button

구조를 사용한다.

예)

아직 등록된 자산이 없습니다.

[ 자산 추가 ]

---

# Loading

Skeleton 우선

Spinner 최소화

---

# Component Naming

Component 이름은

PascalCase

사용

예)

NetWorthCard

GoalCard

AssetCard

RecommendationCard

InvestmentCard

---

# Folder Structure

```
components/

Button/

Card/

Input/

Charts/

Badge/

Layout/

Navigation/

Financial/

Feedback/
```

---

# Reuse Rules

새로운 Component를 만들기 전에

기존 Component를 검색한다.

같은 기능이면

수정한다.

복사하지 않는다.

---

# Component Checklist

새 Component를 만들기 전에 확인

□ 재사용 가능한가

□ 특정 화면에 종속되지 않는가

□ Widget에서도 사용할 수 있는가

□ 이름이 명확한가

□ 상태가 정의되어 있는가

□ Design System을 따르는가

---

# Component States

Button

Default

Hover

Pressed

Disabled

Loading

Success

Danger

---

Card

Default

Hover

Selected

Disabled

Loading

---

Input

Default

Focused

Typing

Error

Disabled

Success

---

# Future Components

Timeline

Heatmap

Calendar

AI Recommendation

Portfolio Allocation

Goal Progress

Consumption Analysis

Asset Flow

---

## Platform Strategy
Component는

Responsive를 지원해야 한다.

하지만

Desktop Layout과

Mobile Layout은

동일할 필요는 없다.

# Version History

v1.0

Initial Component System