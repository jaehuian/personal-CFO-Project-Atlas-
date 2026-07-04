# Atlas Database Specification

Version: 2.0

Status: Architecture Freeze

Owner: Project Atlas

Related Documents

- 01_DomainModel.md
- ../02_Design/04_Dashboard.md
- ../02_Design/05_Purpose.md
- ../02_Design/06_Asset.md
- ../02_Design/07_Investment.md
- ../02_Design/08_Goal.md
- ../02_Design/09_Ledger.md

---

# Purpose

본 문서는 Atlas V1의 Database를 정의한다.

Database는 Domain Model을 구현하기 위한 기술 설계이며,
API, State Management, Repository는 본 문서를 기준으로 구현한다.

---

# Database Philosophy

Atlas는 Account 중심 Database가 아니다.

Purpose 중심 Database이다.

모든 Asset와 Investment는 반드시 하나의 Purpose를 가진다.

Goal은 Purpose에 선택적으로 연결된다.

---

# Database Rules

## Primary Key

모든 PK는 UUID를 사용한다.

---

## Timestamp

모든 시간은 UTC로 저장한다.

모든 테이블은 아래 컬럼을 가진다.

- created_at
- updated_at

---

## Delete

V1은 Hard Delete를 사용한다.

Soft Delete는 V2 이후 도입한다.

---

## Naming Convention

Table

snake_case

Column

snake_case

Primary Key

id

Foreign Key

{table}_id

---

# Entity Overview

Core

- goal
- purpose
- institution
- account
- asset
- investment
- transaction
- rule

Future

- portfolio
- exchange_rate
- milestone
- goal_template
- purpose_template

---

# Enum Definitions

## institution_type

- BANK
- SECURITIES
- CARD
- CASH
- CRYPTO

---

## account_type

- CHECKING
- SAVINGS
- CMA
- ISA
- PENSION
- SECURITIES
- CASH
- CRYPTO

---

## asset_type

- CASH
- DEPOSIT
- SAVINGS
- CMA

---

## investment_type

- DOMESTIC_STOCK
- FOREIGN_STOCK
- ETF
- BOND
- GOLD
- CRYPTO

---

## transaction_type

- INCOME
- EXPENSE
- TRANSFER

---

## payment_method

- CREDIT_CARD
- CHECK_CARD
- CASH
- TRANSFER
- ETC

---

# Table Specification

---

## goal

재무 목표

| Column | Type | Null | Description |
|---------|------|------|-------------|
| id | UUID | ❌ | PK |
| name | VARCHAR(100) | ❌ | 목표명 |
| target_amount | DECIMAL(18,2) | ❌ | 목표 금액 |
| target_date | DATE | ✅ | 목표일 |
| memo | TEXT | ✅ | 메모 |
| created_at | TIMESTAMP | ❌ | 생성일 |
| updated_at | TIMESTAMP | ❌ | 수정일 |

Indexes

- PK_goal

Delete Policy

Purpose.goal_id → SET NULL

---

## purpose

자금 목적

| Column | Type | Null |
|---------|------|------|
| id | UUID | ❌ |
| name | VARCHAR(100) | ❌ |
| description | TEXT | ✅ |
| goal_id | UUID | ✅ |
| created_at | TIMESTAMP | ❌ |
| updated_at | TIMESTAMP | ❌ |

Indexes

- PK_purpose
- FK_goal
- UX_purpose_name

Delete Policy

Asset 또는 Investment가 존재하면 삭제 불가

---

## institution

금융기관 마스터

| Column | Type | Null |
|---------|------|------|
| id | UUID | ❌ |
| name | VARCHAR(100) | ❌ |
| type | institution_type | ❌ |
| logo | VARCHAR(255) | ✅ |
| is_active | BOOLEAN | ❌ |
| created_at | TIMESTAMP | ❌ |
| updated_at | TIMESTAMP | ❌ |

Indexes

- PK_institution
- UX_institution_name

Delete Policy

Account가 존재하면 삭제 불가

---

## account

금융 계좌

| Column | Type | Null |
|---------|------|------|
| id | UUID | ❌ |
| institution_id | UUID | ❌ |
| name | VARCHAR(100) | ❌ |
| account_type | account_type | ❌ |
| is_active | BOOLEAN | ❌ |
| created_at | TIMESTAMP | ❌ |
| updated_at | TIMESTAMP | ❌ |

Indexes

- PK_account
- FK_institution

Delete Policy

Asset 또는 Investment가 존재하면 삭제 불가

---

## asset

현금성 자산

| Column | Type | Null |
|---------|------|------|
| id | UUID | ❌ |
| name | VARCHAR(100) | ❌ |
| asset_type | asset_type | ❌ |
| market_value | DECIMAL(18,2) | ❌ |
| purpose_id | UUID | ❌ |
| account_id | UUID | ❌ |
| memo | TEXT | ✅ |
| created_at | TIMESTAMP | ❌ |
| updated_at | TIMESTAMP | ❌ |

Indexes

- PK_asset
- FK_purpose
- FK_account
- IX_asset_type

Delete Policy

Hard Delete

---

## investment

투자 자산

| Column | Type | Null |
|---------|------|------|
| id | UUID | ❌ |
| symbol | VARCHAR(50) | ❌ |
| name | VARCHAR(100) | ❌ |
| investment_type | investment_type | ❌ |
| quantity | DECIMAL(18,8) | ❌ |
| average_price | DECIMAL(18,2) | ❌ |
| current_price | DECIMAL(18,2) | ✅ |
| market_value | DECIMAL(18,2) | ❌ |
| profit_loss | DECIMAL(18,2) | ✅ |
| return_rate | DECIMAL(8,4) | ✅ |
| purpose_id | UUID | ❌ |
| account_id | UUID | ❌ |
| memo | TEXT | ✅ |
| created_at | TIMESTAMP | ❌ |
| updated_at | TIMESTAMP | ❌ |

Indexes

- PK_investment
- FK_purpose
- FK_account
- IX_symbol
- IX_investment_type

Delete Policy

Hard Delete

---

## transaction

가계부 거래

| Column | Type | Null |
|---------|------|------|
| id | UUID | ❌ |
| transaction_date | DATE | ❌ |
| transaction_type | transaction_type | ❌ |
| category | VARCHAR(50) | ❌ |
| payment_method | payment_method | ✅ |
| amount | DECIMAL(18,2) | ❌ |
| account_id | UUID | ❌ |
| memo | TEXT | ✅ |
| created_at | TIMESTAMP | ❌ |
| updated_at | TIMESTAMP | ❌ |

Indexes

- PK_transaction
- FK_account
- IX_transaction_date
- IX_category

Delete Policy

Hard Delete

---

## rule

관리 원칙

| Column | Type | Null |
|---------|------|------|
| id | UUID | ❌ |
| rule_key | VARCHAR(100) | ❌ |
| rule_value | TEXT | ❌ |
| created_at | TIMESTAMP | ❌ |
| updated_at | TIMESTAMP | ❌ |

Indexes

- PK_rule
- UX_rule_key

---

# Relationship

Goal (1)
    │
    │ Optional
    ▼
Purpose (N)
    │
    ├───────────────┐
    ▼               ▼
Asset            Investment
    │               │
    └──────┬────────┘
           ▼
        Account
           ▲
           │
     Institution

Account
    │
    ▼
Transaction

Rule

(Independent)

---

# Foreign Key Policy

Goal 삭제

→ Purpose.goal_id = NULL

Purpose 삭제

→ Asset / Investment 존재 시 삭제 불가

Institution 삭제

→ Account 존재 시 삭제 불가

Account 삭제

→ Asset / Investment 존재 시 삭제 불가

---

# Index Strategy

기본 Index

- 모든 PK

Foreign Key Index

- goal_id
- institution_id
- purpose_id
- account_id

조회 Index

- purpose.name
- investment.symbol
- transaction.transaction_date
- transaction.category

복합 Index는 실제 사용 패턴을 확인한 후 추가한다.

---

# Future Expansion

## Version 2

- Portfolio
- Exchange Rate
- Dividend

## Version 2.2

- Milestone
- Goal Template
- Purpose Template
- Archive

## Version 3

- Workspace
- Member
- Notification
- Open Banking

현재 구조는 V3까지 큰 Migration 없이 확장 가능하도록 설계한다.

---

# Review Checklist

- [ ] UUID 사용
- [ ] UTC Timestamp 사용
- [ ] Institution 분리
- [ ] Asset / Investment 분리
- [ ] Purpose 중심 구조
- [ ] Goal Optional
- [ ] Enum 정의 완료
- [ ] V2.2 확장 고려 완료

---

# Notes

Database는 Domain Model을 구현하기 위한 기술 설계이다.

Atlas는 Account 중심이 아닌 Purpose 중심으로 설계되며,

Purpose는 모든 자산과 투자의 기준이 되는 핵심 Domain이다.