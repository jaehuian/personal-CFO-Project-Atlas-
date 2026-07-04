# Atlas Design System

Version: 1.0
Status: Draft
Owner: Project Atlas
Related Documents:
- README.md
- 02_Component.md
- 03_Widget.md

---

# Purpose

Atlas Design System은 Project Atlas에서 사용하는 UI/UX의 기준을 정의한다.

모든 화면은 본 문서의 규칙을 따른다.

새로운 화면이나 기능을 추가하더라도 기존 디자인 원칙을 유지하여 일관된 사용자 경험을 제공하는 것이 목적이다.

---

# Design Philosophy

Atlas는 화려한 UI보다 사용성을 우선한다.

디자인의 목적은 예쁜 화면이 아니라 사용자가 빠르게 현재 상태를 이해하고 다음 행동을 결정할 수 있도록 돕는 것이다.

우선순위

1. 정보 전달
2. 사용성
3. 일관성
4. 심미성

---

# UX Principles

## 1. Dashboard First

모든 사용은 Dashboard에서 시작한다.

Dashboard는 현재 상태만 보여준다.

상세 정보는 각 화면에서 확인한다.

---

## 2. One Screen, One Purpose

하나의 화면은 하나의 목적만 가진다.

예)

Dashboard → 현재 상태

Asset → 자산 관리

Investment → 투자 관리

Ledger → 가계부

Goal → 목표 관리

---

## 3. Card Based UI

Atlas는 모든 정보를 Card 형태로 표현한다.

예)

- 순자산 카드
- 목표 카드
- 추천 행동 카드
- 계좌 카드
- 투자 카드

Table 사용은 최소화한다.

---

## 4. Widget Based Design

모든 카드는 Widget이다.

Widget은 독립적으로 동작한다.

Widget은 다른 화면에서도 재사용 가능해야 한다.

예)

Net Worth Widget

↓

Dashboard

↓

Goal 화면

↓

Asset 화면

모두 사용 가능

---

## 5. Progressive Disclosure

처음에는 필요한 정보만 보여준다.

사용자가 클릭하면 상세 정보가 열린다.

예)

Dashboard

↓

생활비

↓

Asset Detail

↓

계좌 목록

---

## 6. Purpose First

Atlas는 계좌보다 목적을 먼저 보여준다.

목적 예시

- 생활비
- 내집마련
- 장기투자
- 노후준비

모든 자산은 목적을 가진다.

---

# Design Keywords

Atlas가 추구하는 디자인

Simple

Modern

Minimal

Professional

Financial

Reliable

Readable

---

# Color Philosophy

색상은 의미를 가진다.

Primary

Atlas Blue

↓

주요 액션

---

Success

Green

↓

목표 달성

수익

긍정 상태

---

Warning

Orange

↓

주의

예산 초과

---

Danger

Red

↓

손실

부족

위험

---

Neutral

Gray

↓

일반 정보

보조 정보

---

차트는 색보다 형태와 라벨을 우선한다.

---

# Typography

우선순위

Heading

↓

Section

↓

Body

↓

Caption

폰트는 읽기 쉬운 Sans-serif를 사용한다.

텍스트 크기는 최소 14px 이상을 유지한다.

---

# Radius

Atlas는 둥근 UI를 사용한다.

Card Radius

16px

Button Radius

12px

Input Radius

12px

Modal Radius

20px

---

# Spacing

기본 단위

8px Grid

Spacing

8

16

24

32

48

64

만 사용한다.

---

# Icons

Outline Style

일관된 두께

텍스트보다 먼저 보이면 안 된다.

아이콘은 보조 역할이다.

---

# Charts

기본 차트

Donut Chart

Bar Chart

Line Chart

Priority

Donut

>

Bar

>

Line

Pie Chart는 사용하지 않는다.

---

# Navigation

Atlas는 Sidebar를 사용하지 않는다.

모든 이동은

Widget

또는

Bottom Navigation

또는

Back

으로 이동한다.

메뉴는 최소화한다.

---

# Interaction

Hover

약한 그림자

Click

Scale 98%

Loading

Skeleton 사용

Animation

150~250ms

과한 Animation 금지

---

# Responsive

Desktop 우선

Tablet 지원

Mobile 지원

모든 Widget은 반응형이어야 한다.

---

# Accessibility

색상만으로 정보를 전달하지 않는다.

차트는 Label을 함께 제공한다.

버튼은 충분한 크기를 유지한다.

텍스트 대비를 유지한다.

---

# Design Rules

항상 Widget 사용

Card 기반 UI

정보 우선

여백 유지

복잡한 표 사용 금지

Popup 최소화

Modal 최소화

한 화면에 하나의 목적

---

# Definition of Good Design

좋은 화면은

예쁜 화면이 아니다.

좋은 화면은

사용자가 3초 안에

현재 상태를 이해할 수 있는 화면이다.

---

# Future Extensions

Dark Mode

Custom Theme

Widget Marketplace

Color Theme

User Theme

---

## Platform Strategy
Responsive Strategy

Desktop

Primary

Tablet

Secondary

Mobile

Companion App

# Version History

v1.0

Initial Design System