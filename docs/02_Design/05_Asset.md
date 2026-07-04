# Asset Page Specification

Version: 2.0

Status: Draft

Owner: Project Atlas

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

Asset는 사용자가 보유한 모든 자산을 관리하는 화면이다.

Atlas는 자산을 단순히 "어디에 있는 돈"이 아니라

"무엇을 위한 돈(Purpose)"으로 관리한다.

사용자는 Purpose와 Account 두 가지 관점에서 자산을 관리할 수 있다.

---

# Design Philosophy

Asset는 계좌를 보여주는 화면이 아니다.

Asset는

"돈의 목적"

을 관리하는 화면이다.

Account는 저장 위치이며,

Purpose는 자산의 이유이다.

---

# User Question

사용자는 이 화면에서 다음 질문에 답할 수 있어야 한다.

- 내 돈은 어디에 있는가?
- 내 돈은 무엇을 위한 돈인가?
- 계좌별 자산은 얼마인가?
- 목적별 자산은 얼마인가?

---

# Screen Responsibilities

Asset는

- 자산 조회
- 자산 등록
- 자산 수정
- Purpose 변경
- Account 관리

를 담당한다.

Asset는

투자 분석이나 소비 분석을 담당하지 않는다.

---

# Layout

```
Header

↓

Summary

↓

View Toggle

↓

Asset List

↓

Detail
```

---

# Layout Structure

```
┌────────────────────────────────────────────┐

Asset

────────────────────────────────────────────

총 자산

82,350,000원

────────────────────────────────────────────

[ Purpose ]   [ Account ]

────────────────────────────────────────────

Asset List

────────────────────────────────────────────

Detail

```

---

# Summary

표시 정보

- 총 자산
- 계좌 수
- Purpose 수

Summary는 읽기 전용이다.

---

# View Toggle

사용자는 두 가지 방식으로 자산을 확인할 수 있다.

## Purpose View (Default)

추천 화면

사용 목적 기준으로 자산을 그룹화한다.

예)

- 생활비
- 비상금
- 내집마련
- 장기투자

---

## Account View

계좌 기준으로 자산을 그룹화한다.

예)

- 국민은행
- 신한은행
- 한국투자증권
- ISA
- 연금저축

---

사용자가 마지막으로 선택한 View를 저장한다.

---

# Purpose View

각 Purpose Card는 다음 정보를 표시한다.

- Purpose 이름
- 총 자산
- 진행률 (Goal이 연결된 경우)
- 포함된 Account 수

클릭 시

Purpose Detail 화면으로 이동한다.

---

# Account View

각 Account Card는 다음 정보를 표시한다.

- Account 이름
- Account 종류
- 총 자산
- 연결된 Purpose

클릭 시

Account Detail 화면으로 이동한다.

---

# Asset Detail

선택한 Purpose 또는 Account의 상세 정보를 표시한다.

표시 정보

- 자산 목록
- 평가금액
- 메모
- 연결된 Goal
- 연결된 Investment

---

# Asset Registration

사용자는 자산을 등록할 수 있다.

필수 입력

- 자산명
- 평가금액
- Account
- Purpose

선택 입력

- 메모

---

# Purpose Management

사용자는 자산의 Purpose를 변경할 수 있다.

Purpose 변경은

Goal 진행률에 즉시 반영된다.

---

# Account Management

사용자는

- 계좌 추가
- 계좌 수정
- 계좌 비활성화

를 수행할 수 있다.

계좌 삭제는 연결된 자산이 없는 경우에만 가능하다.

---

# Navigation Rules

Dashboard

↓

Asset

Asset

↓

Purpose Detail

Asset

↓

Account Detail

Dashboard로 항상 복귀 가능해야 한다.

---

# Interaction

Hover

Card Shadow

Click

Detail 표시

Double Click

사용하지 않는다.

---

# Empty State

```
아직 등록된 자산이 없습니다.

[ 자산 등록 ]
```

Purpose View와 Account View 모두 Empty State를 제공한다.

---

# Platform Strategy

## Desktop

모든 기능 지원

- 등록
- 수정
- Purpose 변경
- Account 관리

---

## Mobile (V3)

지원

- 조회
- 간단한 수정
- 자산 등록

제한

- Account 관리
- 대량 수정

---

# Data Requirements

Asset

- id
- name
- marketValue
- accountId
- purposeId
- memo
- createdAt
- updatedAt

---

Account

- id
- name
- type
- institution
- isActive

---

Purpose

- id
- name
- goalId

---

# API Requirements

GET /assets

POST /assets

PUT /assets/{id}

DELETE /assets/{id}

GET /accounts

POST /accounts

PUT /accounts/{id}

GET /purposes

---

# Validation Rules

모든 Asset는 반드시

- Account
- Purpose

를 가진다.

평가금액은 0 이상이어야 한다.

---

# V1 Scope

포함

- Purpose View
- Account View
- Asset CRUD
- Purpose 변경
- Account 관리

제외

- 자산 이력
- 자동 시세 반영
- Open Banking
- 증권 API 연동
- 자동 분류

---

# Future Features

Version 1.2

- 자산 증감 이력
- Account Archive
- Purpose 추천

Version 2

- 자동 계좌 동기화
- Open Banking
- 자산 시뮬레이션

Version 3

- Mobile Companion
- 빠른 자산 등록

---

# Definition of Done

- Summary 구현
- Purpose View 구현
- Account View 구현
- Asset CRUD 구현
- Purpose 변경 구현
- Dashboard 연동

---

# Figma AI Prompt

Design a desktop asset management page for Atlas.

Requirements

- Professional financial dashboard
- Card-based layout
- Purpose View as default
- Account View toggle
- Summary section
- Asset detail panel
- White background
- Rounded cards (16px)
- Desktop 1440px
- Consistent with Atlas Design System

---

# Review Checklist

- [ ] Purpose 중심으로 설계되었는가?
- [ ] Account와 Purpose 역할이 명확히 구분되는가?
- [ ] Dashboard와 자연스럽게 연결되는가?
- [ ] Toggle 구조가 직관적인가?
- [ ] One Screen One Question 원칙을 지키는가?
- [ ] Desktop First 원칙을 따르는가?
- [ ] V1 범위를 벗어나지 않는가?

---

# Notes

Asset는 Atlas의 핵심 데이터 관리 화면이다.

사용자는 자산을 계좌가 아니라 목적(Purpose) 중심으로 이해해야 한다.

Account는 저장 위치이고,

Purpose는 자산의 이유이다.