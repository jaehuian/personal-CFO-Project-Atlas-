# Investment Page Specification

Version: 1.0

Status: Draft

Owner: Project Atlas

Related Documents

- 01_Vision.md
- 02_RuleBook.md
- 03_UserFlow.md
- 05_Asset.md
- 01_DesignSystem.md
- 02_Component.md
- 03_Widget.md

---

# Purpose

Investment 화면은 사용자의 모든 투자 자산을 관리하는 화면이다.

투자의 현재 상태를 확인하고, 종목을 관리하며, 목적(Purpose)을 관리할 수 있다.

Dashboard는 Investment 화면의 정보를 요약하여 보여준다.

---

# Goals

사용자는 이 화면에서 다음 질문에 답할 수 있어야 한다.

- 현재 얼마를 투자하고 있는가?
- 어떤 상품에 투자하고 있는가?
- 투자 비중은 어떻게 구성되어 있는가?
- 수익률은 어떤가?
- 어떤 목적을 위한 투자인가?

---

# Screen Layout

```

Header

↓

Investment Summary

↓

Investment Allocation

↓

View Toggle

↓

Investment List

↓

Investment Detail

```

---

# Wireframe

```

┌──────────────────────────────────────────────────────────────┐
│ ← Dashboard                              Investment          │
├──────────────────────────────────────────────────────────────┤

총 투자금액

34,250,000원

평가손익

+3,520,000원 (+11.46%)

───────────────────────────────────────────────────────────────

○ Portfolio

● Investment Type

───────────────────────────────────────────────────────────────

          ( Donut Chart )

───────────────────────────────────────────────────────────────

ETF

18,500,000원

53%

>

───────────────────────────────────────────────────────────────

채권

9,200,000원

27%

>

───────────────────────────────────────────────────────────────

코인

6,550,000원

20%

>

```

---

# View Modes

Investment 화면은 두 가지 보기 방식을 제공한다.

## Portfolio View (Default)

Purpose(목적) 기준으로 투자를 관리한다.

예시

```

장기투자

↓

QQQ

↓

VOO

↓

SCHD

────────────────

내집마련

↓

채권 ETF

↓

금 ETF

```

Portfolio Card에는 다음 정보를 표시한다.

- Portfolio 이름
- 총 평가금액
- 총 손익
- 총 수익률
- 종목 개수

---

## Investment Type View

투자 상품 종류별로 관리한다.

예시

```

ETF

↓

QQQ

↓

VOO

↓

SCHD

────────────────

채권

↓

국채

↓

회사채

────────────────

코인

↓

BTC

↓

ETH

```

종목 오른쪽에는 항상 Purpose Badge를 표시한다.

예시

```

QQQ

₩5,200,000

+12%

🏠 내집마련

```

---

# Investment Summary Widget

표시 정보

- 총 투자금액
- 총 평가손익
- 총 수익률
- 투자 상품 수

클릭 없음

---

# Investment Allocation Widget

도넛 차트

보기 기준

- Portfolio
- Investment Type

Toggle 변경 시 자동 갱신

---

# Investment List

Portfolio View

↓

Portfolio Card

↓

Investment Item

Investment Type View

↓

Investment Type Card

↓

Investment Item

---

# Investment Item

각 투자 종목에는 다음 정보를 표시한다.

- 종목명
- 티커(Symbol)
- 평가금액
- 매수금액
- 평가손익
- 수익률
- 보유수량
- 평균단가
- Purpose Badge

---

# Investment Detail

종목을 선택하면 상세 화면으로 이동한다.

표시 정보

- 종목 기본 정보
- 투자 목적
- 평가금액
- 매수금액
- 손익
- 수익률
- 거래내역
- 메모

---

# Purpose Management

Investment 화면에서도 Purpose를 변경할 수 있다.

예시

```

QQQ

↓

Purpose

🏠 내집마련

↓

▼

📈 장기투자

↓

저장

```

저장 즉시

- Dashboard
- Asset
- Goal
- Portfolio

자동 반영

---

# Investment Categories

Version 1 지원

- ETF
- 국내주식
- 해외주식
- 채권
- 코인
- 금
- 현금성 투자

향후 추가

- 리츠
- 펀드
- 외화
- 원자재

---

# Account Information

투자 종목은 반드시 하나의 계좌를 가진다.

예시

QQQ

↓

한국투자 ISA

↓

장기투자

---

# Interaction

Hover

Card Shadow

Click

Investment Detail

Toggle

Portfolio ↔ Investment Type

Purpose Badge

클릭 시 변경 가능

---

# Empty State

등록된 투자 자산이 없습니다.

↓

[ 투자 등록 ]

---

# Loading

Skeleton 사용

---

# Required Data

Investment ID

Account

Purpose

Category

Ticker

Name

Quantity

Average Price

Current Price

Market Value

Cost Basis

Profit

Return Rate

Currency

Updated At

---

# Database Requirements

Entities

Investment

InvestmentCategory

Portfolio

Purpose

Account

InvestmentHistory

---

# API Requirements

GET /investments

GET /investment/{id}

POST /investment

PUT /investment

DELETE /investment

PATCH /investment/{id}/purpose

GET /portfolio

---

# Validation Rules

모든 투자 자산은

- 계좌
- Purpose
- Category
- 평가금액

을 가져야 한다.

평가금액은 0 이상이어야 한다.

Ticker는 중복될 수 있다.

(예: 서로 다른 계좌에서 동일 ETF 보유)

---

# V1 Scope

포함

- 투자 등록
- 수정
- 삭제
- Purpose 변경
- Portfolio View
- Investment Type View
- 투자 비중
- 평가손익

제외

- 리밸런싱
- 배당 관리
- 자동 거래내역
- API 연동
- 자동 시세 갱신

---

# Future Features

- 리밸런싱 추천
- 목표 비중 설정
- 배당금 관리
- 배당 캘린더
- 증권 API 연동
- 자동 시세 업데이트
- 자동매매 연동
- AI 투자 분석

---

# Definition of Done

완료 조건

- Portfolio View 구현
- Investment Type View 구현
- Toggle 구현
- Investment Summary Widget 구현
- Allocation Widget 구현
- Purpose 변경 구현
- Investment Detail 구현
- Dashboard 연동

---

# Figma AI Prompt

Design a modern desktop investment management page for Atlas.

Style

- Professional financial dashboard
- Minimal interface
- White background
- Rounded cards (16px)
- Soft shadows
- 8px spacing system

Requirements

- Large investment summary card
- Donut chart
- Toggle between Portfolio and Investment Type
- Card-based investment list
- Purpose badges on each investment
- Clean typography
- Desktop layout (1440px)
- Readability over decoration
- Consistent with Asset page

---

# Review Checklist

- [ ] Vision과 일치하는가?
- [ ] RuleBook을 따르는가?
- [ ] UserFlow와 연결되는가?
- [ ] Asset 화면과 일관성이 있는가?
- [ ] Figma AI가 이해할 수 있는가?
- [ ] Cursor가 구현 가능한가?
- [ ] V1 범위를 벗어나지 않는가?

---

# Notes

Investment 화면은 "투자를 어떻게 관리할 것인가"를 담당한다.

Asset 화면은 "돈이 어디에 있는가"를 보여주고,

Investment 화면은 "투자가 어떻게 구성되어 있는가"를 보여준다.

두 화면은 동일한 데이터를 사용하지만 서로 다른 관점을 제공한다.

## Mobile Support

조회

투자 등록

지원

Portfolio 관리

지원 안 함