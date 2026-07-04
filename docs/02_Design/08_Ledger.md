# Ledger Page Specification

Version: 2.0

Status: Draft

Owner: Project Atlas

Display Name: 가계부

Related Documents

- 00_StyleGuide.md
- 01_DesignSystem.md
- 02_Component.md
- 03_Widget.md
- 04_Dashboard.md
- 05_Asset.md
- 06_Investment.md
- 07_Goal.md
- ../01_Product/01_Vision.md
- ../01_Product/02_RuleBook.md
- ../01_Product/03_UserFlow.md

---

# Purpose

Ledger는 사용자의 거래를 기록하는 화면이다.

Atlas는 거래를 정확하게 기록하고,

Dashboard가 이를 분석하여 사용자에게 보여준다.

Ledger는 기록을 담당하고,

분석은 담당하지 않는다.

---

# Design Philosophy

Ledger는

돈을 입력하는 화면이다.

사용자는 가능한 적은 입력으로

빠르게 거래를 기록할 수 있어야 한다.

---

# User Question

사용자는 이 화면에서 다음 질문에 답할 수 있어야 한다.

- 이번 달 어떤 거래를 했는가?
- 특정 거래를 수정하거나 삭제해야 하는가?
- 거래는 어느 계좌에서 발생했는가?

---

# Screen Responsibilities

Ledger는

- 거래 조회
- 거래 등록
- 거래 수정
- 거래 삭제

를 담당한다.

소비 분석이나 통계는 Dashboard에서 담당한다.

---

# Layout

```
Header

↓

Monthly Summary

↓

Filter

↓

Transaction List

↓

Transaction Detail
```

---

# Layout Structure

```
┌────────────────────────────────────────────┐

가계부

────────────────────────────────────────────

이번 달

수입 / 지출 / 이체

────────────────────────────────────────────

검색

필터

────────────────────────────────────────────

거래 목록

────────────────────────────────────────────

거래 상세

```

---

# Monthly Summary

표시 정보

- 이번 달 수입
- 이번 달 지출
- 이번 달 이체

Summary는 읽기 전용이다.

이체는 수입과 지출에 포함하지 않는다.

---

# Transaction List

거래 목록은 최신순으로 정렬한다.

각 거래는 다음 정보를 표시한다.

- 날짜
- 거래 유형
- 금액
- 카테고리
- 계좌
- 메모(있는 경우)

---

# Transaction Detail

거래를 선택하면 상세 정보를 표시한다.

표시 정보

- 날짜
- 거래 유형
- 금액
- 계좌
- 카테고리
- 결제수단
- 메모

---

# Transaction Registration

사용자는 거래를 등록할 수 있다.

필수 입력

- 거래 유형
- 날짜
- 금액
- 계좌
- 카테고리

선택 입력

- 결제수단
- 메모

---

# Transaction Types

Version 1은 세 가지 거래 유형을 지원한다.

## Income

수입

예)

- 월급
- 부업
- 금융
- 기타

---

## Expense

지출

예)

고정비

- 통신비
- 교육
- 구독
- 기타

소비

- 교통비
- 식비
- 생활비
- 문화여가
- 간식
- 경조사
- 의류/미용
- 의료/건강
- 운동
- 교육
- 반려동물
- 여행
- 금융
- 기타

---

## Transfer

이체

계좌 간 자산 이동

예)

생활비 계좌

↓

예금 계좌

↓

ISA

↓

연금저축

이체는

수입도 아니고

지출도 아니다.

---

# Payment Method

Version 1

- 신용카드
- 체크카드
- 현금/송금
- 기타

결제수단은 Expense에서만 사용한다.

---

# Filter

지원

- 기간
- 거래 유형
- 계좌
- 카테고리

검색

- 메모
- 거래명

---

# Sorting

기본

최신순

지원

- 오래된순
- 금액순

---

# Navigation Rules

Dashboard

↓

Ledger

Ledger

↓

Transaction Detail

Dashboard로 항상 복귀 가능해야 한다.

---

# Interaction

Hover

행 강조

Click

Detail 표시

Double Click

사용하지 않는다.

---

# Empty State

```
아직 거래 내역이 없습니다.

[ 거래 등록 ]
```

---

# Platform Strategy

## Desktop

모든 기능 지원

- 거래 CRUD
- 필터
- 검색

---

## Mobile (V3)

지원

- 빠른 거래 등록
- 거래 조회
- 간단한 수정

제한

- 대량 수정
- 복잡한 필터

---

# Data Requirements

Transaction

- id
- type
- date
- amount
- accountId
- categoryId
- paymentMethod
- memo
- createdAt
- updatedAt

---

# API Requirements

GET /transactions

POST /transactions

PUT /transactions/{id}

DELETE /transactions/{id}

---

# Validation Rules

모든 거래는

- 날짜
- 금액
- 계좌
- 거래 유형

을 가져야 한다.

금액은 0보다 커야 한다.

---

# V1 Categories

## Income

- 월급
- 부업
- 금융
- 기타

---

## Fixed Expense

- 통신비
- 교육
- 구독
- 기타

---

## Expense

- 교통비
- 식비
- 생활비
- 문화여가
- 간식
- 경조사
- 의류/미용
- 의료/건강
- 운동
- 교육
- 반려동물
- 여행
- 금융
- 기타

---

## Payment Method

- 신용카드
- 체크카드
- 현금/송금
- 기타

---

# V1 Scope

포함

- 거래 CRUD
- 필터
- 검색
- 월별 Summary
- 이체 관리

제외

- 예산(Budget)
- 반복 거래
- 영수증 OCR
- 자동 분류
- 소비 분석

---

# Future Features

## Version 1.2

- 소비 패턴 분석
- Insight
- 반복 거래

---

## Version 2

- OCR 영수증 등록
- 자동 카테고리 분류
- 배당
- 세금
- 환전

---

## Version 3

- Mobile Quick Add
- 음성 입력

---

# Definition of Done

- Transaction CRUD
- Monthly Summary
- Category System
- Transfer Rule
- Dashboard 연동

---

# Figma AI Prompt

Design a desktop ledger page for Atlas.

Requirements

- Professional finance application
- Table-first layout
- Fast transaction entry
- Monthly summary
- Transaction list
- Transaction detail panel
- White background
- Rounded cards
- Desktop 1440px
- Consistent with Atlas Design System

---

# Review Checklist

- [ ] 거래 입력이 빠른가?
- [ ] 이체가 수입/지출과 분리되는가?
- [ ] Dashboard와 역할이 명확히 구분되는가?
- [ ] 검색과 필터가 충분한가?
- [ ] One Screen One Question 원칙을 따르는가?
- [ ] Desktop First 원칙을 따르는가?
- [ ] V1 범위를 벗어나지 않는가?

---

# Notes

Ledger는 Atlas의 데이터 입력 화면이다.

정확한 기록은 좋은 분석의 시작이다.

Ledger는 거래를 기록하고,

Dashboard는 그 거래를 이해하도록 돕는다.