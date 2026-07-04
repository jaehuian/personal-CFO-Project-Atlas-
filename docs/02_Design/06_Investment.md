# Investment Page Specification

Version: 4.0

Status: Architecture Freeze Candidate

Owner: Project Atlas

Display Name: 투자

Related Documents

- 00_StyleGuide.md
- 01_DesignSystem.md
- 02_Component.md
- 03_Widget.md
- 04_Dashboard.md
- 05_Purpose.md
- 06_Asset.md
- ../03_Architecture/01_DomainModel.md
- ../01_Product/01_Vision.md
- ../01_Product/02_RuleBook.md

---

# Purpose

Investment는 사용자의 투자 자산을 관리하는 화면이다.

Atlas는 투자 상품을 중심으로 관리하지 않는다.

투자는 하나의 Purpose를 달성하기 위한 수단이다.

Purpose는 별도 화면에서 관리하며,

Investment는 Purpose를 선택하여 연결한다.

---

# Design Philosophy

Investment는

종목을 관리하는 화면이다.

Purpose를 생성하거나 수정하지 않는다.

Purpose는 투자의 이유이며,

Investment는 그 Purpose를 실현하는 수단이다.

---

# User Question

사용자는 이 화면에서 다음 질문에 답할 수 있어야 한다.

- 내 투자는 어떤 자금 목적을 위한 것인가?
- 투자 종류별 자산은 어떻게 구성되어 있는가?
- 자금 목적별 투자 비중은 적절한가?
- 어떤 계좌에서 운용되고 있는가?

---

# Screen Responsibilities

Investment는 다음 기능을 담당한다.

- Investment 조회
- Investment 등록
- Investment 수정
- Investment 삭제
- Purpose 선택
- Account 선택

담당하지 않는 기능

- Purpose CRUD
- Goal CRUD

---

# Screen Structure

Header

↓

Summary

↓

View Toggle

↓

Investment List

↓

Detail Panel

---

# Summary

표시 정보

- 총 평가금액
- 총 손익
- 총 수익률
- 종목 수

읽기 전용이다.

---

# View Toggle

Investment는 두 가지 관점을 제공한다.

## 자금 목적 View (Default)

자금 목적별로 투자 자산을 그룹화한다.

각 Card는

- 자금 목적
- 총 평가금액
- 투자 종목 수
- 투자 비중
- Goal 진행률(Optional)

Goal이 없는 경우

진행률은 표시하지 않는다.

---

## 투자 종류 View

투자 상품 기준으로 그룹화한다.

예)

- ETF
- 국내주식
- 해외주식
- 채권
- 금
- 코인

각 Card는

- 투자 종류
- 총 평가금액
- 비중
- 종목 수

사용자가 마지막으로 선택한 View를 저장한다.

---

# Detail Panel

## Purpose Detail

표시

- 자금 목적
- Goal(Optional)
- 연결된 Investment
- 총 평가금액
- 총 손익
- 총 수익률

Action

- [ 자금 목적 열기 ]

Purpose 수정은 Purpose 화면에서 수행한다.

---

## Investment Type Detail

표시

- 투자 종류
- 종목 목록
- 총 평가금액
- 총 비중

Action

- 종목 등록
- 종목 수정

---

# Investment Registration

필수 입력

- 종목명
- 투자 종류
- 수량
- 평균단가
- Purpose
- Account

선택 입력

- 메모

Purpose는 Select에서 선택한다.

등록 중 원하는 Purpose가 없다면

[ + 새 자금 목적 ]

버튼을 통해 Purpose 화면으로 이동한다.

등록 화면은 임시 저장 상태를 유지한다.

---

# Navigation

Dashboard

↓

Investment

↓

자금 목적

↓

Investment Detail

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

## 투자 자산 없음

아직 등록된 투자 자산이 없습니다.

↓

[ 투자 등록 ]

---

# Platform Strategy

## Desktop

모든 기능 지원

## Mobile (V3)

지원

- 조회
- 수정
- 투자 등록

제한

- 복잡한 편집

---

# Business Rules

Rule 1

모든 Investment는 반드시 하나의 Purpose를 가진다.

---

Rule 2

모든 Investment는 반드시 하나의 Account를 가진다.

---

Rule 3

Purpose는 Investment 화면에서 관리하지 않는다.

---

Rule 4

Purpose 변경은 Investment의 소속만 변경한다.

---

Rule 5

Goal 진행률은 연결된 Purpose를 통해 계산된다.

Investment는 Goal을 직접 참조하지 않는다.

---

# Data Model

Investment

- id
- symbol
- name
- investmentType
- quantity
- averagePrice
- currentPrice
- marketValue
- profitLoss
- returnRate
- purposeId
- accountId
- memo

---

# API

GET /investments

POST /investments

PUT /investments/{id}

DELETE /investments/{id}

---

# V1 Scope

포함

- 자금 목적 View
- 투자 종류 View
- Investment CRUD
- Purpose 선택
- Account 선택

제외

- Purpose CRUD
- Goal CRUD
- 증권사 API
- 자동 시세
- 자동 매매
- AI 분석
- 리밸런싱

---

# Future Features

## Version 1.2

- 투자 비중 분석
- 리밸런싱 제안
- 투자 이력

## Version 2

- 증권사 API
- 자동 시세
- 배당 관리
- 리스크 분석

## Version 3

- Mobile Companion

---

# Definition of Done

- Summary 구현
- 자금 목적 View 구현
- 투자 종류 View 구현
- Investment CRUD 구현
- Purpose 선택 구현
- Dashboard 연동

---

# Figma AI Prompt

Design a desktop investment management page for Atlas.

Requirements

- Professional financial application
- Purpose View (default)
- Investment Type View
- Summary section
- Investment cards
- Detail panel
- White background
- Rounded cards (16px)
- Desktop 1440px
- Consistent with Atlas Design System

---

# Review Checklist

- [ ] Investment가 Purpose를 참조만 하는가?
- [ ] Purpose CRUD가 제거되었는가?
- [ ] Goal을 직접 관리하지 않는가?
- [ ] 자금 목적 View가 기본 화면인가?
- [ ] 투자 종류 View가 유지되는가?
- [ ] Domain Model과 일치하는가?

---

# Notes

Investment는 투자 자산을 관리하는 화면이다.

자금 목적(Purpose)은 별도 화면에서 관리한다.

Investment는 Purpose를 선택하여 연결하고,

Account를 통해 실제 운용 계좌를 관리한다.