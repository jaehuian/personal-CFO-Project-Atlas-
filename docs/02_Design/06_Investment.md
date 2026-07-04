# Investment Page Specification

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
- ../01_Product/01_Vision.md
- ../01_Product/02_RuleBook.md
- ../01_Product/03_UserFlow.md

---

# Purpose

Investment는 사용자의 투자 자산을 관리하는 화면이다.

Atlas는 투자를 단순한 종목 목록이 아니라

사용자의 목표를 달성하기 위한 자산으로 관리한다.

사용자는 Purpose와 Investment Type 두 가지 관점에서 투자를 관리할 수 있다.

---

# Design Philosophy

Investment는

수익률을 자랑하는 화면이 아니다.

현재 투자 상태를 이해하고

투자 원칙을 지키고 있는지 확인하는 화면이다.

---

# User Question

사용자는 이 화면에서 다음 질문에 답할 수 있어야 한다.

- 내 투자는 어떤 상태인가?
- 투자 목적별 비중은 적절한가?
- 투자 종류별 비중은 적절한가?
- 어떤 종목을 보유하고 있는가?

---

# Screen Responsibilities

Investment는

- 투자 조회
- 투자 등록
- 투자 수정
- 투자 삭제
- 투자 목적 변경

을 담당한다.

Investment는

실제 매매를 수행하지 않는다.

---

# Layout

```
Header

↓

Summary

↓

View Toggle

↓

Investment List

↓

Detail
```

---

# Layout Structure

```
┌────────────────────────────────────────────┐

Investment

────────────────────────────────────────────

총 평가금액

총 수익률

────────────────────────────────────────────

[ Purpose ]   [ Investment Type ]

────────────────────────────────────────────

Investment List

────────────────────────────────────────────

Detail

```

---

# Summary

표시 정보

- 총 평가금액
- 총 수익률
- 투자 종목 수

Summary는 읽기 전용이다.

---

# View Toggle

사용자는 두 가지 방식으로 투자를 조회할 수 있다.

## Purpose View (Default)

투자 목적 기준으로 그룹화한다.

예)

- 내집마련
- 노후준비
- 장기투자
- 단기투자

각 카드에는

- 총 평가금액
- 수익률
- 포함 종목 수

를 표시한다.

---

## Investment Type View

투자 종류 기준으로 그룹화한다.

예)

- ETF
- 국내주식
- 해외주식
- 채권
- 금
- 코인

각 카드에는

- 총 평가금액
- 비중
- 종목 수

를 표시한다.

사용자가 마지막으로 선택한 View를 저장한다.

---

# Investment Detail

선택한 Purpose 또는 Investment Type의 상세 정보를 표시한다.

표시 정보

- 종목명
- 수량
- 평균단가
- 현재가
- 평가금액
- 평가손익
- 수익률
- 연결된 Purpose

---

# Investment Registration

사용자는 투자 자산을 등록할 수 있다.

필수 입력

- 종목명
- 투자 종류
- 계좌(Account)
- Purpose
- 수량
- 평균단가

선택 입력

- 메모

---

# Investment Management

사용자는

- 투자 수정
- 투자 삭제
- Purpose 변경

을 수행할 수 있다.

삭제 시

확인 절차를 제공한다.

---

# Navigation Rules

Dashboard

↓

Investment

Investment

↓

Investment Detail

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
아직 등록된 투자 자산이 없습니다.

[ 투자 등록 ]
```

---

# Platform Strategy

## Desktop

모든 기능 지원

- 등록
- 수정
- 삭제
- Purpose 변경

---

## Mobile (V3)

지원

- 조회
- 간단한 수정
- 투자 등록

제한

- 대량 수정
- 복잡한 관리

---

# Data Requirements

Investment

- id
- symbol
- name
- quantity
- averagePrice
- currentPrice
- marketValue
- profitLoss
- returnRate
- investmentType
- accountId
- purposeId
- memo
- createdAt
- updatedAt

---

# API Requirements

GET /investments

POST /investments

PUT /investments/{id}

DELETE /investments/{id}

---

# Validation Rules

모든 투자 자산은 반드시

- Account
- Purpose

를 가진다.

수량은 0보다 커야 한다.

평균단가는 0보다 커야 한다.

---

# V1 Scope

포함

- Purpose View
- Investment Type View
- Investment CRUD
- Purpose 변경

제외

- 자동 시세 조회
- 증권 API 연동
- 자동 매매
- 리밸런싱
- AI 투자 분석

---

# Future Features

## Version 1.2

- 투자 비중 분석
- 리밸런싱 제안
- 종목 메모

## Version 2

- 증권사 API 연동
- 자동 시세 업데이트
- 배당 관리
- 리스크 분석

## Version 3

- Mobile Companion
- 빠른 투자 등록

---

# Definition of Done

- Summary 구현
- Purpose View 구현
- Investment Type View 구현
- Investment CRUD 구현
- Dashboard 연동

---

# Figma AI Prompt

Design a desktop investment management page for Atlas.

Requirements

- Professional financial dashboard
- Card-based layout
- Purpose View as default
- Investment Type View toggle
- Summary section
- Investment detail panel
- White background
- Rounded cards (16px)
- Desktop 1440px
- Consistent with Atlas Design System

---

# Review Checklist

- [ ] Purpose 중심 설계를 따르는가?
- [ ] Investment Type View가 자연스러운가?
- [ ] Dashboard와 연결되는가?
- [ ] Toggle 구조가 직관적인가?
- [ ] 실제 매매 기능을 포함하지 않는가?
- [ ] One Screen One Question 원칙을 지키는가?
- [ ] Desktop First 원칙을 따르는가?
- [ ] V1 범위를 벗어나지 않는가?

---

# Notes

Investment는 투자를 기록하는 화면이 아니다.

Investment는

사용자의 투자 상태를 관리하는 화면이다.

Purpose는

'왜 투자하는가'

Investment Type은

'무엇에 투자하는가'

를 의미한다.

이 두 관점을 함께 제공하는 것이 Atlas Investment의 핵심이다.