# Atlas Domain Model

Version: 1.0

Status: Draft

Owner: Project Atlas

Related Documents

- ../01_Product/01_Vision.md
- ../01_Product/02_RuleBook.md
- ../02_Design/05_Asset.md
- ../02_Design/06_Investment.md
- ../02_Design/07_Goal.md
- ../02_Design/08_Ledger.md
- ../02_Design/09_MyRules.md

---

# Purpose

Domain Model은 Atlas를 구성하는 핵심 비즈니스 개념과
그 관계를 정의한다.

Database, API, State Management는
모두 본 문서를 기준으로 설계한다.

---

# Domain Philosophy

Atlas는 계좌 중심이 아닌
목적(Purpose) 중심으로 자산을 관리한다.

Purpose는 모든 자산 관리의 중심 엔티티이다.

---

# Domain Overview

```

Goal
↑
│
Purpose
│
├──────── Asset
│
├──────── Investment
│
└──────── Rule (Recommendation)

↓

Account

↓

Transaction

```

---

# Core Domains

Atlas는 아래 Domain으로 구성된다.

- Goal
- Purpose
- Account
- Asset
- Investment
- Transaction
- Rule

---

# Domain Description

## Goal

사용자의 재무 목표

예)

- 내집마련
- 비상금
- 노후준비

Goal은 하나 이상의 Purpose를 가질 수 있다.

---

## Purpose

Atlas의 핵심 Domain

Purpose는

"왜 이 돈이 존재하는가"

를 의미한다.

예)

- 생활비
- 내집마련
- 비상금
- 장기투자

Purpose는

- Asset
- Investment

와 연결된다.

---

## Account

실제 금융 계좌

예)

- 국민은행
- ISA
- 한국투자증권
- 연금저축

Account는 돈의 저장 위치이다.

---

## Asset

현금성 자산

예)

- 예금
- 적금
- CMA

Asset는

Purpose를 가진다.

Asset는

하나의 Account에 저장된다.

---

## Investment

투자 자산

예)

- ETF
- 주식
- 채권
- 금
- 코인

Investment는

Purpose를 가진다.

Investment는

하나의 Account에 보관된다.

---

## Transaction

모든 거래 기록

종류

- Income
- Expense
- Transfer

Transaction은

하나의 Account에서 발생한다.

---

## Rule

사용자의 관리 원칙

Rule은 Recommendation Engine에서 사용된다.

---

# Relationships

## Goal

1 : N

Purpose

---

## Purpose

1 : N

Asset

---

## Purpose

1 : N

Investment

---

## Account

1 : N

Asset

---

## Account

1 : N

Investment

---

## Account

1 : N

Transaction

---

## Rule

Recommendation Engine 참조

---

# Ownership

Goal

↓

Purpose

↓

Asset / Investment

↓

Account

↓

Transaction

---

# Aggregate

Goal Aggregate

- Goal
- Purpose

---

Asset Aggregate

- Asset
- Account

---

Investment Aggregate

- Investment
- Account

---

Ledger Aggregate

- Transaction
- Account

---

Recommendation Aggregate

- Rule

---

# Lifecycle

Goal 생성

↓

Purpose 생성

↓

Account 연결

↓

Asset 등록

↓

Investment 등록

↓

Transaction 기록

↓

Dashboard 반영

↓

Recommendation 생성

---

# Domain Rules

Goal 없이 Purpose를 생성할 수 없다.

Purpose 없이 Asset를 생성할 수 없다.

Purpose 없이 Investment를 생성할 수 없다.

Asset는 반드시 하나의 Account를 가진다.

Investment는 반드시 하나의 Account를 가진다.

Transaction은 반드시 하나의 Account를 가진다.

Rule은 Dashboard Recommendation에서만 사용된다.

---

# Version 1 Scope

Goal

Purpose

Account

Asset

Investment

Transaction

Rule

---

# Future Domains

Version 2

- Portfolio
- Institution
- ExchangeRate

Version 2.5

- Generic Goal
- Milestone

Version 3

- User
- Workspace
- Collaboration

---

# Review Checklist

- [ ] Purpose가 중심 Domain인가?
- [ ] 모든 Domain 관계가 명확한가?
- [ ] Dashboard 구조와 일치하는가?
- [ ] Rule이 Recommendation 전용인가?
- [ ] V1 범위를 벗어나지 않는가?

---

# Notes

Purpose는 Atlas의 핵심 Domain이다.

Goal은 방향을 정의한다.

Purpose는 이유를 정의한다.

Account는 위치를 정의한다.

Asset와 Investment는 가치를 저장한다.

Transaction은 변화를 기록한다.

Rule은 의사결정을 돕는다.