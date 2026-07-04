# Asset Page Specification

Version: 1.0

Status: Draft

Owner: Project Atlas

Related Documents

- 01_Vision.md
- 02_RuleBook.md
- 03_UserFlow.md
- 01_DesignSystem.md
- 02_Component.md
- 03_Widget.md

---

# Purpose

Asset 화면은 사용자의 모든 자산을 목적(Purpose) 또는 계좌(Account) 기준으로 관리하는 화면이다.

Atlas의 모든 자산 정보는 이 화면을 중심으로 관리된다.

Dashboard는 Asset 화면의 정보를 요약하여 보여준다.

---

# Goals

사용자는 이 화면에서 다음 질문에 답할 수 있어야 한다.

- 현재 내 자산은 얼마인가?
- 내 돈은 어디에 있는가?
- 어떤 목적을 위해 모으고 있는가?
- 자산 비중은 어떻게 구성되어 있는가?
- 어떤 계좌에 얼마가 있는가?

---

# Screen Layout

```
Header

↓

Summary

↓

Asset Allocation

↓

Purpose / Account Toggle

↓

Asset List

↓

Detail Drawer (Optional)
```

---

# Wireframe

```
┌──────────────────────────────────────────────────────┐
│ ← Dashboard                           Asset          │
├──────────────────────────────────────────────────────┤

총 순자산

82,350,000원

▲ +1,520,000 (이번 달)

───────────────────────────────────────────────────────

○ Purpose

● Account

───────────────────────────────────────────────────────

          ( Donut Chart )

───────────────────────────────────────────────────────

생활비

43%

35,000,000원

>

───────────────────────────────────────────────────────

내집마련

37%

30,000,000원

>

───────────────────────────────────────────────────────

장기투자

15%

12,000,000원

>

───────────────────────────────────────────────────────

노후준비

5%

5,000,000원

>

```

---

# View Mode

Asset 화면은 두 가지 보기 모드를 제공한다.

## Purpose View (Default)

기본 화면이다.

자산을 목적별로 그룹화한다.

예)

생활비

내집마련

장기투자

노후준비

---

## Account View

사용자가 Toggle을 변경하면 계좌 기준으로 표시한다.

예)

국민은행

한국투자증권

ISA

연금저축

코인원

바이낸스

---

# Asset Summary Widget

표시 정보

- 총 순자산
- 이번 달 증감
- 평가금액 기준

클릭 없음

---

# Asset Allocation Widget

도넛 차트

지원

- Purpose
- Account

Toggle에 따라 자동 변경

클릭 시 해당 그룹으로 스크롤 이동

---

# Asset List

Purpose View에서는

각 목적별 Card를 표시한다.

Card에는

- 목적명
- 총 금액
- 자산 비중
- 계좌 개수

를 표시한다.

---

Account View에서는

각 계좌 Card를 표시한다.

Card에는

- 계좌명
- 총 금액
- 자산 개수
- 목적 개수

를 표시한다.

---

# Asset Detail

Card를 클릭하면 상세 화면으로 이동한다.

예)

내집마련

↓

보유 자산 목록

↓

예금

↓

ETF

↓

채권

↓

코인

---

# Purpose Management

Purpose는 자유롭게 생성할 수 있다.

기본 Purpose는 삭제할 수 없다.

기본 Purpose

- 생활비
- 비상금
- 내집마련
- 장기투자
- 노후준비

사용자는

추가

수정

순서 변경

이 가능하다.

---

# Purpose Change

Atlas 핵심 기능

사용자는 언제든 자산의 Purpose를 변경할 수 있다.

예)

QQQ

↓

내집마련

↓

장기투자

저장

↓

Dashboard

↓

Goal

↓

Asset Allocation

자동 갱신

---

# Account Rules

계좌는 단순한 저장 위치이다.

예)

국민은행

↓

예금

↓

Purpose

↓

내집마련

---

같은 계좌 안의 자산도 서로 다른 Purpose를 가질 수 있다.

---

# Interaction

Hover

Card Shadow

Click

Detail Page

Toggle

Purpose ↔ Account

Animation

200ms 이하

---

# Empty State

등록된 자산이 없습니다.

↓

[ 자산 추가 ]

---

# Loading

Skeleton 사용

---

# Required Data

Asset

Account

Purpose

Market Value

Cost Basis

Currency

Updated At

---

# Database Requirements

Entities

Account

Asset

Purpose

AssetPurposeMapping

---

# API Requirements

GET /assets

GET /purposes

GET /accounts

PATCH /asset/{id}/purpose

POST /asset

PUT /asset

DELETE /asset

---

# Validation Rules

모든 자산은

- 계좌
- Purpose
- 평가금액

을 가져야 한다.

평가금액은 0 이상이다.

Purpose가 없으면 저장할 수 없다.

---

# Future Features

CSV Import

Open Banking

증권 API

자동 시세 업데이트

자동 거래내역

---

# Definition of Done

완료 조건

- Purpose View 구현
- Account View 구현
- Toggle 구현
- Purpose 변경 구현
- Summary Widget 구현
- Allocation Widget 구현
- Asset Detail 이동
- Dashboard 연동

---

# Figma AI Prompt

Design a modern desktop Asset Management page for a personal finance application called Atlas.

Style:
- Minimal
- Professional
- Financial dashboard
- White background
- Soft shadows
- Rounded cards (16px)
- 8px spacing system

Requirements:
- Large summary card showing Total Net Worth
- Donut chart with toggle (Purpose / Account)
- Card-based asset list
- Purpose is the default view
- Account view available through segmented toggle
- No sidebar navigation
- Dashboard-style clean interface
- Desktop width (1440px)
- Use neutral colors with blue as primary accent
- Prioritize readability over decoration

---

# Notes

이 화면은 Atlas의 데이터 중심 화면이다.

Dashboard는 이 화면의 요약이며,

Goal과 Investment 화면 역시 Asset 데이터를 참조한다.

## Mobile Support

V1

지원 안 함

V3

지원

모바일에서는

조회

자산 추가

간단한 수정

만 지원한다.

Purpose 관리

계좌 관리

Bulk 수정

지원하지 않는다.