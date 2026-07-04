# Goal Page Specification

Version: 3.0

Status: Architecture Freeze Candidate

Owner: Project Atlas

Display Name: 목표

Related Documents

- 00_StyleGuide.md
- 01_DesignSystem.md
- 02_Component.md
- 03_Widget.md
- 04_Dashboard.md
- 05_Purpose.md
- 06_Asset.md
- 07_Investment.md
- ../03_Architecture/01_DomainModel.md
- ../01_Product/01_Vision.md
- ../01_Product/02_RuleBook.md

---

# Purpose

Goal은 사용자의 재무 목표를 관리하는 화면이다.

Goal은 돈을 관리하지 않는다.

Goal은 Purpose에 목표를 부여하는 역할을 한다.

Purpose는 Goal 없이도 존재할 수 있다.

---

# Design Philosophy

Goal은 계획(Planning)이다.

Asset와 Investment는 현재를 관리한다.

Goal은 미래를 관리한다.

Atlas는 Goal보다 Purpose를 중심으로 동작한다.

---

# User Question

사용자는 이 화면에서 다음 질문에 답할 수 있어야 한다.

- 나는 무엇을 이루고 싶은가?
- 각 목표는 얼마나 진행되었는가?
- 어떤 Purpose가 목표와 연결되어 있는가?
- 목표 달성까지 얼마나 남았는가?

---

# Screen Responsibilities

Goal은 다음 기능을 담당한다.

- Goal 조회
- Goal 생성
- Goal 수정
- Goal 삭제
- Purpose 연결
- Progress 조회

Goal은 Asset와 Investment를 직접 관리하지 않는다.

---

# Screen Structure

Header

↓

Summary

↓

Goal List

↓

Detail Panel

---

# Summary

표시 정보

- Goal 개수
- 진행 중 Goal
- 완료 Goal
- 평균 달성률

읽기 전용이다.

---

# Goal List

Goal은 Card 형태로 표시한다.

각 Card는

- Goal 이름
- 목표 금액
- 현재 금액
- 달성률
- 목표 날짜
- 연결된 Purpose 수

를 표시한다.

---

# Detail Panel

표시

- Goal 이름
- 목표 금액
- 현재 금액
- 달성률
- 목표 날짜
- 연결된 Purpose
- 예상 완료일(Optional)
- 메모

---

# Available Actions

- Goal 수정
- Purpose 연결
- Purpose 연결 해제

Goal은 Asset나 Investment를 직접 수정하지 않는다.

---

# Goal Registration

필수 입력

- Goal 이름
- 목표 금액

선택 입력

- 목표 날짜
- 메모
- 연결할 Purpose

Goal은 Purpose 없이 생성할 수 있다.

Purpose 연결은 언제든 가능하다.

---

# Purpose Connection

Goal은 하나 이상의 Purpose를 연결할 수 있다.

Purpose는 하나의 Goal만 연결할 수 있다.

Purpose 선택은 기존 목록에서 수행한다.

새 Purpose가 필요하면

Purpose 화면에서 생성한다.

---

# Progress Calculation

Goal 진행률은

연결된 Purpose의 총 자산을 기준으로 계산한다.

예)

목표

4억원

↓

연결된 Purpose

내집마련

↓

현재 자산

1억원

↓

진행률

25%

Goal은 Asset를 직접 계산하지 않는다.

Purpose를 통해 계산한다.

---

# Navigation

Dashboard

↓

Goal

↓

Purpose

↓

Dashboard

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

아직 목표가 없습니다.

↓

첫 번째 목표를 만들어보세요.

↓

[ 목표 만들기 ]

---

# Platform Strategy

## Desktop

모든 기능 지원

---

## Mobile (V3)

지원

- 조회
- 생성
- 수정

제한

- 복잡한 편집

---

# Business Rules

Rule 1

Goal은 Purpose 없이 생성할 수 있다.

---

Rule 2

Purpose 연결은 선택 사항이다.

---

Rule 3

Goal 진행률은 Purpose를 통해 계산한다.

---

Rule 4

Goal은 Asset를 직접 참조하지 않는다.

---

Rule 5

Goal은 Investment를 직접 참조하지 않는다.

---

Rule 6

Goal 삭제는 연결된 Purpose가 있어도 가능하다.

삭제 시 Purpose와의 연결만 해제된다.

---

# Data Model

Goal

- id
- name
- targetAmount
- targetDate
- memo
- createdAt
- updatedAt

---

# API

GET /goals

POST /goals

PUT /goals/{id}

DELETE /goals/{id}

POST /goals/{id}/purposes

DELETE /goals/{id}/purposes/{purposeId}

---

# V1 Scope

포함

- Goal CRUD
- Purpose 연결
- Progress 조회

제외

- Milestone
- 자동 목표 추천
- AI 계획
- 목표 템플릿

---

# Future Features

## Version 1.2

- 예상 달성일
- 목표 알림
- 진행률 차트

## Version 2

- Milestone
- 목표 템플릿
- AI 추천

## Version 3

- 공유 Goal
- 가족 Goal
- 협업 Goal

---

# Definition of Done

- Goal CRUD 구현
- Purpose 연결 구현
- Progress 계산
- Dashboard 연동

---

# Figma AI Prompt

Design a desktop financial goal management page for Atlas.

Requirements

- Professional finance application
- Card-based layout
- Goal cards
- Progress visualization
- Purpose connection
- Detail panel
- White background
- Rounded cards (16px)
- Desktop 1440px
- Consistent with Atlas Design System

---

# Review Checklist

- [ ] Goal이 Planning 역할만 수행하는가?
- [ ] Goal이 Purpose를 참조하는가?
- [ ] Goal이 Asset를 직접 참조하지 않는가?
- [ ] Goal이 Investment를 직접 참조하지 않는가?
- [ ] Dashboard와 일관성이 있는가?
- [ ] DomainModel과 일치하는가?

---

# Notes

Goal은 Atlas의 중심이 아니다.

Purpose가 Atlas의 중심이다.

Goal은 Purpose에 목표를 부여하는 Planning Domain이다.

현재(Current)는 Asset와 Investment가 관리한다.

미래(Future)는 Goal이 관리한다.