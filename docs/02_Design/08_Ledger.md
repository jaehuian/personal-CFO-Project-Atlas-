# Ledger Page Specification

Version: 1.0

Status: Draft

Owner: Project Atlas

Related Documents

- 01_Vision.md
- 02_RuleBook.md
- 03_UserFlow.md
- 05_Asset.md
- 06_Investment.md
- 07_Goal.md
- 01_DesignSystem.md
- 02_Component.md
- 03_Widget.md

---

# Purpose

Ledger(가계부)는 사용자의 모든 거래를 기록하고 관리하는 화면이다.

Atlas에서 발생하는 모든 돈의 이동은 Ledger를 통해 기록된다.

Ledger는 거래를 기록하는 역할을 담당하며, Dashboard는 Ledger 데이터를 분석하여 현재 상태와 추천을 제공한다.

---

# Goals

사용자는 이 화면에서 다음 질문에 답할 수 있어야 한다.

- 이번 달 얼마를 벌었는가?
- 이번 달 얼마를 사용했는가?
- 어디에 가장 많이 사용했는가?
- 거래 내역은 무엇인가?
- 거래를 빠르게 등록할 수 있는가?

---

# Screen Layout

```
Header

↓

Monthly Summary

↓

Filter

↓

Transaction List

↓

Floating Action Button (+)
```

---

# Wireframe

```
┌──────────────────────────────────────────────────────────────┐
│ ← Dashboard                                 가계부          │
├──────────────────────────────────────────────────────────────┤

2026년 7월

수입
2,300,000원

지출
1,120,000원

이체
800,000원

──────────────────────────────────────────────────────────────

[전체] [수입] [지출] [이체]

──────────────────────────────────────────────────────────────

7월 25일

🍽 식비

-15,000원

체크카드

────────────────────────────────────────────

💰 월급

+2,300,000원

국민은행

────────────────────────────────────────────

🔄 생활계좌 → 예금

800,000원

────────────────────────────────────────────

                    ＋
```

---

# Monthly Summary Widget

표시 정보

- 총 수입
- 총 지출
- 총 이체

이체는 지출에 포함하지 않는다.

---

# Transaction List

거래는 최신순으로 표시한다.

거래 정보

- 날짜
- 카테고리
- 금액
- 결제수단
- 메모 (있는 경우)
- 거래 유형

---

# Transaction Type

Version 1

- 수입
- 지출
- 이체

---

# Transaction Detail

거래를 클릭하면 상세 화면을 표시한다.

표시 정보

- 날짜
- 거래 유형
- 카테고리
- 금액
- 결제수단
- 계좌
- 메모

이체인 경우

- 출금 계좌
- 입금 계좌

를 함께 표시한다.

---

# Add Transaction

Floating Action Button 클릭

↓

거래 추가 화면

필수 입력

- 거래 유형
- 날짜
- 금액

유형별 입력

수입

- 카테고리
- 입금 계좌

지출

- 카테고리
- 결제수단
- 출금 계좌

이체

- 출금 계좌
- 입금 계좌

선택 입력

- 메모

---

# Income Categories

- 월급
- 부업
- 금융
- 기타

---

# Fixed Expense Categories

- 통신비
- 교육
- 구독
- 기타

---

# Variable Expense Categories

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

# Payment Methods

- 신용카드
- 체크카드
- 현금/송금
- 기타

---

# Transfer Rules

이체는

- 수입으로 계산하지 않는다.
- 지출로 계산하지 않는다.

이체는 자산의 위치만 변경한다.

예)

생활계좌

↓

예금

↓

ISA

↓

증권계좌

↓

비상금 계좌

---

# Filters

사용자는 거래를 필터링할 수 있다.

기본 제공

- 전체
- 수입
- 지출
- 이체

향후 추가

- 카테고리
- 계좌
- 결제수단
- 기간

---

# Search

Version 1

제공하지 않는다.

Version 2

거래 검색 지원

---

# Monthly Statistics

Version 1

간단한 요약만 제공

Version 2

카테고리별 통계

월별 비교

연간 비교

---

# Interaction

Hover

Card Shadow

Click

Transaction Detail

Floating Button

거래 등록

---

# Empty State

등록된 거래가 없습니다.

↓

[ 첫 거래 등록 ]

---

# Loading

Skeleton 사용

---

# Required Data

Transaction ID

Date

Type

Category

Amount

Payment Method

Account

Memo

Created At

Updated At

Transfer From (Optional)

Transfer To (Optional)

---

# Database Requirements

Entities

Transaction

Category

PaymentMethod

Account

Transfer

---

# API Requirements

GET /transactions

POST /transaction

PUT /transaction

DELETE /transaction

GET /categories

GET /payment-methods

---

# Validation Rules

모든 거래는

- 날짜
- 거래 유형
- 금액

을 가져야 한다.

지출은 반드시

- 카테고리
- 결제수단

을 가져야 한다.

이체는 반드시

- 출금 계좌
- 입금 계좌

를 가져야 한다.

---

# V1 Scope

포함

- 거래 등록
- 거래 수정
- 거래 삭제
- 월별 요약
- 거래 목록
- 수입/지출/이체 필터

제외

- 검색
- 통계 차트
- 자동 분류
- OCR
- 은행 연동

---

# Future Features

- 거래 검색
- 카테고리 관리
- 반복 거래
- 자동 거래 가져오기
- OCR 영수증 등록
- 소비 패턴 분석
- 예산 관리

---

# Definition of Done

완료 조건

- 월별 요약 구현
- 거래 목록 구현
- 거래 등록 구현
- 거래 수정 구현
- 거래 삭제 구현
- 이체 처리 구현
- Dashboard 연동

---

# Figma AI Prompt

Design a modern desktop household ledger page for Atlas.

Style

- Minimal
- Professional
- White background
- Rounded cards (16px)
- Soft shadows
- Financial dashboard style

Requirements

- Monthly summary card
- Transaction list
- Floating Add button
- Filter chips (All / Income / Expense / Transfer)
- Clean typography
- Desktop layout (1440px)
- Consistent with Asset, Investment and Goal pages

---

# Review Checklist

- [ ] Vision과 일치하는가?
- [ ] RuleBook을 따르는가?
- [ ] UserFlow와 연결되는가?
- [ ] 이체는 수입/지출과 분리되는가?
- [ ] Dashboard와 연결되는가?
- [ ] Cursor가 구현 가능한가?
- [ ] V1 범위를 벗어나지 않는가?

---

# Notes

Ledger는 거래를 기록하는 화면이다.

거래를 분석하고 추천하는 역할은 Dashboard가 담당한다.

Ledger는 빠른 입력과 정확한 기록을 최우선으로 설계한다.