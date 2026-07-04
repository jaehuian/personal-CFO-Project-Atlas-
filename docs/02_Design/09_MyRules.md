# Management Principles Page Specification

Version: 2.0

Status: Draft

Owner: Project Atlas

Display Name: 관리 원칙

Related Documents

- 00_StyleGuide.md
- 01_DesignSystem.md
- 02_Component.md
- 03_Widget.md
- 04_Dashboard.md
- ../01_Product/01_Vision.md
- ../01_Product/02_RuleBook.md
- ../01_Product/03_UserFlow.md

---

# Purpose

Management Principles는

사용자의 자산관리 기준을 설정하는 화면이다.

Atlas는 사용자의 원칙을 기억하고,

Recommendation을 생성할 때 이를 우선적으로 사용한다.

Rule는 자동 실행되지 않는다.

---

# Design Philosophy

Management Principles는

설정 화면이 아니다.

Atlas에게

"나는 이렇게 돈을 관리한다."

를 알려주는 화면이다.

---

# User Question

사용자는 이 화면에서 다음 질문에 답할 수 있어야 한다.

- 나는 어떤 기준으로 돈을 관리하는가?
- Atlas는 어떤 기준으로 추천하는가?
- 현재 적용 중인 원칙은 무엇인가?

---

# Screen Responsibilities

Management Principles는

- Rule 조회
- Rule 활성화 / 비활성화
- Rule 값 수정

을 담당한다.

Rule 생성은 Version 2 이후 지원한다.

---

# Layout

```
Header

↓

Rule Summary

↓

Rule Category

↓

Rule List

↓

Rule Detail
```

---

# Layout Structure

```
┌────────────────────────────────────────────┐

관리 원칙

────────────────────────────────────────────

활성 Rule

12개

────────────────────────────────────────────

생활

투자

목표

기타

────────────────────────────────────────────

Rule List

────────────────────────────────────────────

Rule Detail

```

---

# Rule Summary

표시 정보

- 활성 Rule 개수
- 비활성 Rule 개수

Summary는 읽기 전용이다.

---

# Rule Categories

Version 1

생활

투자

목표

기타

카테고리는 좌측 또는 상단 Tab으로 제공한다.

---

# Rule List

각 Rule Card는 다음 정보를 표시한다.

- Rule 이름
- 설명
- 현재 값
- 활성 여부

클릭 시 Detail을 표시한다.

---

# Rule Detail

사용자는 다음 항목을 수정할 수 있다.

- 활성 여부 (ON/OFF)
- 기준 값

Rule 설명은 수정할 수 없다.

---

# Rule Templates

Version 1은 Template만 제공한다.

예시

---

생활계좌 최소 잔액

100만원

---

비상금 목표

500만원

---

월급 입금 계좌

생활계좌

---

내집마련 자산 우선

ON

---

목표 달성 후 투자 시작

OFF

---

투자 비중 유지

ON

---

# Rule Types

## Number

예)

생활계좌

100만원

---

## Boolean

예)

투자 비중 유지

ON

---

## Account

예)

월급 입금 계좌

생활계좌

---

## Purpose

예)

우선 목표

내집마련

---

# Navigation Rules

Dashboard

↓

Management Principles

Dashboard로 항상 복귀 가능해야 한다.

---

# Recommendation Rules

Recommendation은

Management Principles를 가장 우선적으로 사용한다.

Priority

Management Principles

↓

Goal

↓

Asset

↓

Investment

↓

Ledger

---

# Interaction

Hover

Card Shadow

Click

Detail 표시

Switch

즉시 반영

저장 버튼은 사용하지 않는다.

변경 사항은 자동 저장한다.

---

# Empty State

Version 1에서는 제공하지 않는다.

Template가 항상 존재한다.

---

# Platform Strategy

## Desktop

모든 기능 지원

- Rule 수정
- ON/OFF
- 값 변경

---

## Mobile (V3)

지원

- Rule 조회
- ON/OFF

제한

- 복잡한 수정

---

# Data Requirements

Rule

- id
- name
- description
- category
- type
- value
- enabled
- createdAt
- updatedAt

---

# API Requirements

GET /rules

PUT /rules/{id}

---

# Validation Rules

모든 Rule은

- 이름
- 타입
- 기본값

을 가진다.

Template 삭제는 지원하지 않는다.

---

# V1 Scope

포함

- Rule Template
- ON/OFF
- 값 수정
- 자동 저장

제외

- Rule 생성
- Rule 삭제
- 사용자 Template
- AI Rule 생성

---

# Future Features

## Version 1.2

- Rule 검색
- Rule 즐겨찾기
- Recommendation 근거 표시

---

## Version 2

- 사용자 Rule 생성
- Rule 그룹
- Rule Import / Export
- Rule 공유

---

## Version 3

- Mobile Rule Editor

---

# Definition of Done

- Rule Template
- Category
- Rule Detail
- 자동 저장
- Dashboard Recommendation 연동

---

# Figma AI Prompt

Design a desktop management principles page for Atlas.

Requirements

- Professional financial application
- Card-based layout
- Rule categories
- Rule list
- Rule detail
- Toggle switches
- Number input
- White background
- Rounded cards
- Desktop 1440px
- Consistent with Atlas Design System

---

# Review Checklist

- [ ] Template 기반인가?
- [ ] Rule 생성 기능이 없는가?
- [ ] Dashboard Recommendation과 연결되는가?
- [ ] 자동 저장을 사용하는가?
- [ ] One Screen One Question 원칙을 지키는가?
- [ ] Desktop First 원칙을 따르는가?
- [ ] V1 범위를 벗어나지 않는가?

---

# Notes

Management Principles는

Atlas의 Recommendation Engine이 참고하는 가장 중요한 사용자 데이터이다.

Atlas는 사용자의 원칙을 대신 만들지 않는다.

사용자가 선택한 원칙을 기억하고,

그 원칙을 기반으로 추천한다.