# Asset Page Specification

Version: 5.0

Status: Architecture Freeze Candidate

Owner: Project Atlas

Display Name: 자산

Related Documents

- 00_StyleGuide.md
- 01_DesignSystem.md
- 02_Component.md
- 03_Widget.md
- 04_Dashboard.md
- 05_Purpose.md
- ../03_Architecture/01_DomainModel.md
- ../01_Product/01_Vision.md
- ../01_Product/02_RuleBook.md

---

# Purpose

Asset는 사용자의 현금성 자산을 관리하는 화면이다.

Atlas는 자산을 단순히 계좌(Account)가 아닌
자금 목적(Purpose)과 함께 관리한다.

Purpose는 별도 화면에서 관리하며,
Asset는 Purpose를 선택하여 연결한다.

---

# Design Philosophy

Asset는 자산 관리 화면이다.

Purpose를 생성하거나 수정하지 않는다.

Account는 돈이 보관되는 위치이고,

Purpose는 돈이 존재하는 이유이다.

---

# User Question

사용자는 이 화면에서 다음 질문에 답할 수 있어야 한다.

- 내 자산은 어디에 있는가?
- 이 자산은 어떤 자금 목적을 위한 것인가?
- 목적별 자산은 얼마인가?
- 계좌별 자산은 얼마인가?

---

# Screen Responsibilities

Asset는 다음 기능을 담당한다.

- Asset 조회
- Asset 등록
- Asset 수정
- Asset 삭제
- Purpose 선택
- Account 선택

담당하지 않는 기능

- Purpose 생성
- Purpose 수정
- Purpose 삭제
- Goal 관리

---

# Screen Structure

Header

↓

Summary

↓

View Toggle

↓

Asset List

↓

Detail Panel

---

# Summary

표시 정보

- 총 자산
- 자산 개수
- 자금 목적 개수
- 계좌 개수

읽기 전용이다.

---

# View Toggle

Asset는 두 가지 관점을 제공한다.

## 자금 목적 View (Default)

자금 목적별로 자산을 그룹화한다.

각 Card는

- 자금 목적
- 총 자산
- 연결된 자산 수
- 연결된 투자 수
- 목표 진행률(Optional)

Goal이 연결되지 않은 경우
진행률은 표시하지 않는다.

---

## 계좌 View

계좌별로 자산을 그룹화한다.

각 Card는

- 계좌명
- 계좌 종류
- 총 자산
- 연결된 자금 목적 수

사용자가 마지막으로 선택한 View를 저장한다.

---

# Detail Panel

## 자금 목적 Detail

표시

- 자금 목적 이름
- 연결된 Goal(Optional)
- 총 자산
- 연결된 Asset
- 연결된 Investment

Action

- [ 자금 목적 열기 ]

Purpose 수정은 Purpose 화면에서 수행한다.

---

## Account Detail

표시

- 계좌명
- 금융기관
- 계좌 종류
- 총 자산
- 연결된 Asset 목록

Action

- 계좌 수정
- 계좌 비활성화

---

# Asset Registration

필수 입력

- 자산명
- 평가금액
- 자금 목적
- 계좌

선택 입력

- 메모

자금 목적은 Select에서 선택한다.

등록 중 원하는 자금 목적이 없다면

[ + 새 자금 목적 ]

버튼을 통해 Purpose 화면으로 이동한다.

등록 화면은 임시 저장 상태를 유지한다.

---

# Navigation

Dashboard

↓

Asset

↓

자금 목적

↓

계좌 Detail

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

## 자금 목적 없음

아직 자금 목적이 없습니다.

↓

[ 자금 목적 만들기 ]

---

## 자산 없음

아직 등록된 자산이 없습니다.

↓

[ 자산 등록 ]

---

# Platform Strategy

## Desktop

모든 기능 지원

## Mobile (V3)

지원

- 조회
- 수정
- 자산 등록

제한

- 복잡한 편집

---

# Business Rules

Rule 1

모든 Asset는 반드시 하나의 Purpose를 가진다.

---

Rule 2

모든 Asset는 반드시 하나의 Account를 가진다.

---

Rule 3

Purpose는 Asset 화면에서 관리하지 않는다.

---

Rule 4

Purpose 변경은 Asset의 소속만 변경한다.

---

Rule 5

Goal 진행률은 Purpose를 통해 계산된다.

Asset는 Goal을 직접 참조하지 않는다.

---

# Data Model

Asset

- id
- name
- marketValue
- purposeId
- accountId
- memo

---

# API

GET /assets

POST /assets

PUT /assets/{id}

DELETE /assets/{id}

---

# V1 Scope

포함

- 자금 목적 View
- 계좌 View
- Asset CRUD
- Purpose 선택
- Account 관리

제외

- Purpose CRUD
- Goal CRUD
- Open Banking
- 자동 시세 연동

---

# Future Features

## Version 1.2

- 자산 이동 이력
- Purpose 변경 이력

## Version 2

- Open Banking
- 자동 자산 동기화

## Version 3

- Mobile Companion

---

# Definition of Done

- Summary 구현
- 자금 목적 View 구현
- 계좌 View 구현
- Asset CRUD 구현
- Purpose 선택 구현
- Dashboard 연동

---

# Figma AI Prompt

Design a desktop asset management page for Atlas.

Requirements

- Professional finance application
- Purpose View (default)
- Account View
- Summary section
- Asset cards
- Detail panel
- White background
- Rounded cards (16px)
- Desktop 1440px
- Consistent with Atlas Design System

---

# Review Checklist

- [ ] Asset가 Purpose를 참조만 하는가?
- [ ] Purpose CRUD가 제거되었는가?
- [ ] Goal을 직접 관리하지 않는가?
- [ ] 자금 목적 View가 기본 화면인가?
- [ ] Domain Model과 일치하는가?
- [ ] Dashboard와 일관성이 있는가?

---

# Notes

Asset는 자산을 관리하는 화면이다.

자금 목적(Purpose)은 별도 화면에서 관리한다.

Asset는 Purpose를 선택하여 연결하고,

Account를 통해 실제 보관 위치를 관리한다.