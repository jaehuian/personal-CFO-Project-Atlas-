# Atlas Domain Model

Version: 2.0

Status: Architecture Freeze Candidate

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

Domain Model은 Atlas의 핵심 비즈니스 개념과
그 관계를 정의한다.

Database, API, State Management는
본 문서를 기준으로 설계한다.

Domain Model은 Atlas의 Source of Truth이다.

---

# Domain Philosophy

Atlas는

계좌(Account) 중심이 아닌

목적(Purpose) 중심으로 자산을 관리한다.

Goal은 선택사항이다.

Purpose는 필수이다.

---

# Core Domain Structure

```

                    Goal (0..1)
                        ▲
                        │
                  (Optional)
                        │
                     Purpose
                 ┌────┴────┐
                 │         │
              Asset   Investment
                 │         │
                 └────┬────┘
                      │
                   Account
                      │
                Transaction

Rule
↓

Recommendation

```

---

# Core Domains

## Goal

사용자의 장기 재무 목표

예)

- 내집마련
- 비상금
- 노후준비

Goal은 선택적으로 Purpose와 연결된다.

Goal 없이도 Atlas는 정상 동작한다.

---

## Purpose ⭐

Atlas의 핵심 Domain

Purpose는

"왜 이 돈이 존재하는가"

를 의미한다.

예)

- 생활비
- 비상금
- 내집마련
- 장기투자

모든 Asset와 Investment는
반드시 하나의 Purpose를 가진다.

Goal 연결은 선택 사항이다.

---

## Account

실제 금융 계좌

예)

- 국민은행
- 신한은행
- ISA
- 연금저축
- 한국투자증권

Account는

돈이 보관되는 위치이다.

---

## Asset

현금성 자산

예)

- 예금
- 적금
- CMA

Asset는

반드시

- Purpose
- Account

를 가진다.

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

반드시

- Purpose
- Account

를 가진다.

---

## Transaction

모든 거래 기록

종류

- Income
- Expense
- Transfer

Transaction은

반드시 하나의 Account에서 발생한다.

Transaction은 Asset의 변화를 기록한다.

---

## Rule

사용자의 관리 원칙

Rule은

Recommendation Engine의 입력값이다.

Rule은

Asset를 직접 변경하지 않는다.

---

# Domain Relationships

## Goal

0..1

↓

Purpose

---

## Purpose

1

↓

N

Asset

---

## Purpose

1

↓

N

Investment

---

## Account

1

↓

N

Asset

---

## Account

1

↓

N

Investment

---

## Account

1

↓

N

Transaction

---

## Rule

↓

Recommendation Engine

---

# Business Rules

## Rule 1

Purpose는 Goal 없이 생성할 수 있다.

---

## Rule 2

Goal은 하나 이상의 Purpose와 연결될 수 있다.

---

## Rule 3

Purpose는 Goal 없이도 Dashboard에 표시된다.

---

## Rule 4

모든 Asset는

반드시 하나의 Purpose를 가진다.

---

## Rule 5

모든 Investment는

반드시 하나의 Purpose를 가진다.

---

## Rule 6

Account는

돈의 저장 위치이다.

Purpose와 독립적이다.

---

## Rule 7

Transaction은

Purpose를 직접 가지지 않는다.

Account를 통해 연결된다.

---

## Rule 8

Rule은

Recommendation에만 영향을 준다.

데이터를 자동 변경하지 않는다.

---

# Aggregate

Goal Aggregate

- Goal

---

Purpose Aggregate

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

Purpose 생성

↓

Goal 연결(Optional)

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

# Version 1 Scope

Domain

- Goal
- Purpose
- Account
- Asset
- Investment
- Transaction
- Rule

---

# Future Domains

Version 2

- Institution
- ExchangeRate
- Portfolio

Version 2.5

- Generic Goal
- Milestone

Version 3

- Workspace
- Collaboration

---

# Architecture Principles

Purpose는 Atlas의 중심 Domain이다.

Goal은 방향(Direction)을 정의한다.

Purpose는 이유(Intent)를 정의한다.

Account는 위치(Location)를 정의한다.

Asset와 Investment는 가치(Value)를 저장한다.

Transaction은 변화(Change)를 기록한다.

Rule은 판단(Judgement)을 돕는다.

---

# Review Checklist

- [ ] Purpose가 중심 Domain인가?
- [ ] Goal이 Optional인가?
- [ ] 모든 Asset가 Purpose를 가지는가?
- [ ] 모든 Investment가 Purpose를 가지는가?
- [ ] Dashboard 구조와 일치하는가?
- [ ] Database 설계가 가능한가?
- [ ] API 설계가 가능한가?

---

# Notes

Atlas는

Account 기반 프로그램이 아니다.

Goal 기반 프로그램도 아니다.

Atlas는

Purpose 중심의 개인 자산관리 플랫폼이다.