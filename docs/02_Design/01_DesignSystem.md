# Atlas Design System

Version: 1.1

Status: Draft

Owner: Project Atlas

Related Documents

- ../00_Common/01_Glossary.md
- ../01_Product/01_Vision.md
- ../01_Product/02_RuleBook.md
- ../01_Product/03_UserFlow.md
- 04_Dashboard.md

---

# Purpose

Design System은 Atlas의 모든 화면이 동일한 사용자 경험을 제공하도록 하는 기준이다.

모든 디자인, 컴포넌트, 위젯은 본 문서를 따른다.

---

# Design Philosophy

Atlas는 예쁜 프로그램보다 사용하기 쉬운 프로그램을 만든다.

디자인은 정보를 꾸미기 위한 것이 아니라,

사용자가 더 빠르게 의사결정을 내릴 수 있도록 돕기 위한 것이다.

---

# UX Principles

## Decision Surface

모든 화면은 사용자의 의사결정을 돕는다.

---

## Dashboard First

Dashboard를 기준으로 모든 화면을 설계한다.

---

## One Screen One Question

한 화면은 하나의 질문만 해결한다.

예)

Asset

↓

"내 돈은 어디에 있는가?"

---

## Simplicity First

복잡한 설정보다

좋은 기본값을 제공한다.

---

## Progressive Disclosure

필요한 정보만 먼저 보여준다.

자세한 정보는 클릭 후 확인한다.

---

# Platform Strategy

Primary Platform

Desktop (Electron)

---

Secondary Platform

Mobile Companion (V3)

---

Desktop에서는 모든 기능을 제공한다.

Mobile에서는 조회와 빠른 입력 중심으로 제공한다.

---

# Information Hierarchy

정보는 다음 우선순위를 따른다.

Tier 1

현재 반드시 알아야 하는 정보

---

Tier 2

상황을 이해하기 위한 정보

---

Tier 3

참고 정보

Dashboard에는 Tier3 이하 정보를 최소화한다.

---

# Layout System

모든 화면은 Card 기반으로 구성한다.

```
Header

↓

Summary

↓

Main Content

↓

Detail
```

긴 스크롤을 지양한다.

---

# Grid System

Desktop

12 Columns

---

Max Width

1440px

---

Content Width

1200~1320px

---

Card Gap

24px

---

Section Gap

32px

---

# Spacing System

8px Grid System

사용 값

- 8
- 16
- 24
- 32
- 48
- 64

---

# Typography

Font

Pretendard

Fallback

Noto Sans KR

---

Heading

Bold

---

Body

Regular

---

Caption

Medium

---

숫자는 항상 동일한 정렬을 유지한다.

금액은 읽기 쉬운 크기로 표시한다.

---

# Color System

Primary

Atlas Blue

---

Success

Green

---

Warning

Orange

---

Danger

Red

---

Background

White

---

Surface

Light Gray

---

Color는 의미를 표현할 때만 사용한다.

장식용 색상은 사용하지 않는다.

---

# Radius

Cards

16px

---

Button

12px

---

Input

12px

---

Chip

999px

---

# Shadow

Card

Soft Shadow

---

Hover

Medium Shadow

---

Modal

Large Shadow

---

Shadow는 깊이를 표현하기 위해서만 사용한다.

---

# Motion

Animation

150~250ms

---

Hover

Fade

---

Page Transition

Minimal

---

과도한 애니메이션은 사용하지 않는다.

---

# Interaction

Hover

Shadow 증가

---

Click

Scale 없음

---

Focus

Outline 표시

---

Disabled

Opacity 감소

---

# Accessibility

Keyboard Navigation 지원

---

명확한 Focus 상태 제공

---

색상만으로 정보를 전달하지 않는다.

---

Contrast를 유지한다.

---

# Widget Rules

모든 Widget는

Question

↓

Primary KPI

↓

Secondary KPI

↓

Action

↓

Target

구조를 가진다.

---

Widget는 독립적으로 동작해야 한다.

---

# Card Rules

모든 주요 기능은 Card로 표현한다.

Card는 하나의 역할만 가진다.

Card 안에 Card를 중첩하지 않는다.

---

# Navigation Rules

메뉴보다 Widget Navigation을 우선한다.

Dashboard는 항상 시작점이다.

---

# Responsive Strategy

Desktop

Primary Experience

---

Tablet

Layout 축소

---

Mobile

Companion Experience

---

Responsive는

기능이 아니라 표현만 변경한다.

---

# Naming Rules

Component

PascalCase

예)

AssetCard

GoalWidget

DashboardHeader

---

Props

camelCase

예)

totalAsset

marketValue

goalProgress

---

CSS

Tailwind Utility 우선

---

# Design Tokens

Spacing

8px Grid

---

Radius

12 / 16

---

Shadow

Small

Medium

Large

---

Animation

200ms

---

# Review Checklist

- [ ] Desktop First를 따르는가?
- [ ] One Screen One Question을 만족하는가?
- [ ] Card 기반인가?
- [ ] Widget 구조를 따르는가?
- [ ] 긴 스크롤을 만들지 않는가?
- [ ] 정보 우선순위를 지키는가?
- [ ] Dashboard 철학과 일치하는가?
- [ ] Mobile Companion 전략을 고려했는가?

---

# Version History

## v1.1

- UX Principles 추가
- Dashboard First 추가
- Decision Surface 추가
- Widget Rules 추가
- Information Hierarchy 추가
- Responsive Strategy 추가
- Desktop First 전략 반영