# Atlas Glossary

Version: 1.0

Status: Draft

Owner: Project Atlas

Related Documents

- README.md
- 01_Vision.md
- 02_RuleBook.md
- 03_UserFlow.md

---

# Purpose

이 문서는 Atlas 프로젝트에서 사용하는 모든 핵심 용어를 정의한다.

모든 문서, 디자인, 코드, 데이터베이스, API는 본 문서의 용어를 기준으로 작성한다.

새로운 용어를 추가하거나 기존 용어를 변경할 경우 반드시 본 문서를 먼저 수정한다.

---

# Naming Principles

Atlas는 하나의 개념에 하나의 용어만 사용한다.

동일한 개념을 여러 이름으로 표현하지 않는다.

예)

❌ Balance / Asset / Money

⭕ Asset

---

UI 용어와 개발 용어는 다를 수 있다.

그러나 의미는 반드시 동일해야 한다.

---

# Terminology

| Concept | UI | Document | Code | Description |
|----------|----|----------|------|-------------|
| Asset | 자산 | Asset | asset | 사용자가 보유한 모든 자산 |
| Account | 계좌 | Account | account | 자산이 보관되는 위치 |
| Purpose | 목적 | Purpose | purpose | 자산을 사용하는 목적 |
| Investment | 투자 | Investment | investment | 투자 자산 |
| Portfolio | 포트폴리오 | Portfolio | portfolio | 하나의 투자 목적 그룹 |
| Goal | 목표 | Goal | goal | 사용자가 달성하려는 목표 |
| Ledger | 가계부 | Ledger | ledger | 거래를 기록하는 화면 |
| Transaction | 거래 | Transaction | transaction | 하나의 거래 기록 |
| Category | 카테고리 | Category | category | 거래 분류 |
| Payment Method | 결제수단 | Payment Method | paymentMethod | 결제 방식 |
| Rule | 관리 원칙 | Management Principle | rule | 사용자의 자산관리 기준 |
| Recommendation | 추천 | Recommendation | recommendation | Atlas가 제안하는 행동 |
| Widget | 위젯 | Widget | widget | 화면의 기능 단위 |
| Component | 컴포넌트 | Component | component | UI 구성 요소 |
| Dashboard | 대시보드 | Dashboard | dashboard | 전체 상태를 요약하는 화면 |

---

# Purpose

Purpose는 Atlas의 가장 중요한 개념이다.

Purpose는 자산의 사용 목적을 의미한다.

예)

- 생활비
- 비상금
- 내집마련
- 장기투자
- 노후준비

모든 자산은 반드시 하나의 Purpose를 가진다.

---

# Account

Account는 자산이 보관되는 위치이다.

예)

- 국민은행
- 신한은행
- 한국투자증권
- ISA
- 연금저축
- 코인원
- 바이낸스

Account는 저장 위치일 뿐 목적이 아니다.

---

# Asset

Asset는 사용자가 보유한 모든 재산을 의미한다.

예)

- 예금
- ETF
- 주식
- 채권
- 코인
- 현금

Asset는 반드시

- Account
- Purpose

를 가진다.

---

# Investment

Investment는 투자 자산을 의미한다.

Version 1

- ETF
- 국내주식
- 해외주식
- 채권
- 코인
- 금

---

# Portfolio

Portfolio는 같은 Purpose를 가진 투자 자산의 그룹이다.

예)

장기투자

↓

QQQ

↓

VOO

↓

SCHD

---

# Goal

Goal은 사용자가 달성하려는 재무 목표이다.

Goal은 Purpose와 연결된다.

예)

내집마련

↓

Purpose

↓

관련 Asset 자동 합산

---

# Ledger

Ledger는 거래를 기록하는 화면이다.

UI에서는 "가계부"라는 이름을 사용한다.

Ledger는

- 수입
- 지출
- 이체

를 관리한다.

---

# Transaction

Transaction은 하나의 거래 기록이다.

Version 1

- Income
- Expense
- Transfer

Transfer는

수입도 지출도 아니다.

---

# Rule

Rule는 사용자의 자산관리 기준이다.

UI에서는 "관리 원칙"이라는 용어를 사용한다.

Rule는 자동 실행되지 않는다.

Dashboard Recommendation 생성에 사용된다.

---

# Recommendation

Recommendation은

Atlas가 사용자에게 제안하는 행동이다.

예)

생활계좌 잔액이 많습니다.

↓

예금으로 이동하는 것을 추천합니다.

Recommendation은 강제하지 않는다.

---

# Dashboard

Dashboard는

현재 상태를 요약하여 보여주는 화면이다.

Dashboard에서는

데이터를 직접 수정하지 않는다.

---

# Widget

Widget은 하나의 질문에 답하는 기능 단위이다.

예)

NetWorth Widget

↓

현재 자산은 얼마인가?

---

# Component

Component는 Widget을 구성하는 UI 요소이다.

Component는 재사용 가능해야 한다.

---

# Reserved Words

다음 용어는 Atlas에서 다른 의미로 사용하지 않는다.

- Asset
- Purpose
- Account
- Goal
- Portfolio
- Ledger
- Rule
- Recommendation
- Widget
- Component

---

# UI Naming Rules

사용자에게 보여지는 용어

| 화면 | 표시 이름 |
|------|-----------|
| Dashboard | 대시보드 |
| Asset | 자산 |
| Investment | 투자 |
| Goal | 목표 |
| Ledger | 가계부 |
| My Rules | 관리 원칙 |

---

# Code Naming Rules

모든 코드에서는 영어를 사용한다.

예)

AssetPage.tsx

InvestmentWidget.tsx

GoalCard.tsx

LedgerService.ts

RuleRepository.ts

---

# Database Naming Rules

Database는 camelCase를 사용한다.

예)

purposeId

accountId

marketValue

paymentMethod

createdAt

updatedAt

---

# API Naming Rules

RESTful API를 따른다.

예)

GET /assets

GET /goals

POST /transactions

PUT /accounts/{id}

DELETE /rules/{id}

---

# Version History

v1.0

Initial Glossary