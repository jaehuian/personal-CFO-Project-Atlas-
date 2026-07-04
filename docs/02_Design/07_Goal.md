# Goal Page Specification

Version: 2.0

Status: Draft

Owner: Project Atlas

Related Documents

- 00_StyleGuide.md
- 01_DesignSystem.md
- 02_Component.md
- 03_Widget.md
- 04_Dashboard.md
- 05_Asset.md
- 06_Investment.md
- ../01_Product/01_Vision.md
- ../01_Product/02_RuleBook.md
- ../01_Product/03_UserFlow.md

---

# Purpose

Goal은 사용자의 재무 목표를 관리하는 화면이다.

Atlas의 모든 자산과 투자는 하나 이상의 Goal과 연결될 수 있으며,

Goal은 현재 진행 상태와 목표 달성 가능성을 사용자에게 제공한다.

---

# Design Philosophy

Goal은 단순히 목표 금액을 보여주는 화면이 아니다.

Goal은

"현재 계획이 잘 진행되고 있는가?"

를 판단하는 화면이다.

---

# User Question

사용자는 이 화면에서 다음 질문에 답할 수 있어야 한다.

- 목표까지 얼마나 남았는가?
- 현재 속도로 목표를 달성할 수 있는가?
- 어떤 자산이 목표에 연결되어 있는가?
- 목표를 위해 얼마를 더 모아야 하는가?

---

# Screen Responsibilities

Goal은

- 목표 조회
- 목표 생성
- 목표 수정
- 목표 삭제
- 연결된 Purpose 관리

를 담당한다.

Goal은

투자를 직접 관리하지 않는다.

---

# Layout

```
Header

↓

Summary

↓

Goal List

↓

Goal Detail
```

---

# Layout Structure

```
┌────────────────────────────────────────────┐

Goal

────────────────────────────────────────────

목표 수

대표 목표 진행률

────────────────────────────────────────────

Goal List

────────────────────────────────────────────

Goal Detail

```

---

# Summary

표시 정보

- 목표 개수
- 가장 가까운 목표
- 평균 진행률

Summary는 읽기 전용이다.

---

# Goal List

각 Goal Card는 다음 정보를 표시한다.

- 목표 이름
- 목표 금액
- 현재 금액
- 진행률
- 예상 달성일(선택)
- 상태

클릭 시

Goal Detail을 표시한다.

---

# Goal Detail

Goal Detail은 선택한 목표의 상세 정보를 표시한다.

표시 정보

- 목표 금액
- 현재 금액
- 남은 금액
- 연결된 Purpose
- 연결된 Asset
- 연결된 Investment
- 메모

---

# Goal Registration

사용자는 목표를 등록할 수 있다.

필수 입력

- 목표명
- 목표 금액

선택 입력

- 목표 날짜
- 메모

---

# Goal Status

모든 Goal은 상태를 가진다.

Planning

목표를 생성했지만 아직 자산이 연결되지 않음

---

In Progress

목표가 진행 중

---

Completed

목표 달성

---

Archived

보관

---

# Purpose Connection

Goal은 하나 이상의 Purpose와 연결될 수 있다.

예)

내집마련

↓

Purpose

내집마련

↓

Asset

예금

ETF

채권

---

# Progress Rules

진행률은

현재 금액

÷

목표 금액

으로 계산한다.

100%를 초과해도 그대로 표시한다.

---

# Navigation Rules

Dashboard

↓

Goal

Goal

↓

Goal Detail

Dashboard로 항상 복귀 가능해야 한다.

---

# Interaction

Hover

Card Shadow

Click

Goal Detail 표시

Double Click

사용하지 않는다.

---

# Empty State

```
아직 등록된 목표가 없습니다.

[ 목표 만들기 ]
```

---

# Platform Strategy

## Desktop

모든 기능 지원

- 생성
- 수정
- 삭제
- Purpose 연결

---

## Mobile (V3)

지원

- 조회
- 목표 생성
- 간단한 수정

제한

- 대량 수정
- 복잡한 연결 관리

---

# Data Requirements

Goal

- id
- name
- targetAmount
- currentAmount
- targetDate
- memo
- status
- createdAt
- updatedAt

---

Purpose

- id
- goalId

---

# API Requirements

GET /goals

POST /goals

PUT /goals/{id}

DELETE /goals/{id}

---

# Validation Rules

목표 금액은

0보다 커야 한다.

Goal 이름은 필수이다.

---

# V1 Scope

포함

- Goal CRUD
- 진행률
- Purpose 연결
- Goal Detail

제외

- 목표 시뮬레이션
- 목표 추천
- AI 분석
- 자동 계획 생성

---

# Future Features

Version 1.2

- 예상 달성일 계산
- 목표 우선순위
- 목표 히스토리

Version 2

- Goal Simulation
- AI Goal Planning
- 목표 달성 시나리오

Version 3

- Mobile Companion
- Goal Widget 확장

---

# Definition of Done

- Goal CRUD
- Progress 계산
- Purpose 연결
- Dashboard 연동

---

# Figma AI Prompt

Design a desktop goal management page for Atlas.

Requirements

- Professional financial dashboard
- Card-based layout
- Goal list on the left
- Goal detail on the right
- Progress visualization
- White background
- Rounded cards (16px)
- Desktop 1440px
- Consistent with Atlas Design System

---

# Review Checklist

- [ ] Goal 중심 설계를 따르는가?
- [ ] Progress 계산이 명확한가?
- [ ] Purpose와 연결되는가?
- [ ] Dashboard와 연결되는가?
- [ ] One Screen One Question 원칙을 지키는가?
- [ ] Desktop First 원칙을 따르는가?
- [ ] V1 범위를 벗어나지 않는가?

---

# Notes

Goal은 Atlas의 최종 목적지이다.

Asset는

돈이 어디에 있는지를 관리한다.

Investment는

돈이 어떻게 투자되고 있는지를 관리한다.

Goal은

그 돈이 왜 존재하는지를 관리한다.