# Goal Page Specification

Version: 1.0

Status: Draft

Owner: Project Atlas

Related Documents

- 01_Vision.md
- 02_RuleBook.md
- 03_UserFlow.md
- 05_Asset.md
- 06_Investment.md
- 01_DesignSystem.md
- 02_Component.md
- 03_Widget.md

---

# Purpose

Goal 화면은 사용자의 모든 재무 목표를 관리하는 화면이다.

목표 달성 현황을 보여주고,

목표를 구성하는 자산과 앞으로 필요한 행동을 확인할 수 있다.

Goal은 Atlas의 최종 목적지이며,

Asset와 Investment는 Goal을 위한 수단이다.

---

# Goals

사용자는 이 화면에서 다음 질문에 답할 수 있어야 한다.

- 목표까지 얼마나 남았는가?
- 지금 속도로 목표를 달성할 수 있는가?
- 어떤 자산이 목표를 구성하고 있는가?
- 얼마를 더 모아야 하는가?
- 다음에는 무엇을 해야 하는가?

---

# Screen Layout

```

Header

↓

Goal Summary

↓

Goal List

↓

Goal Detail

↓

Recommendation

```

---

# Wireframe

```

┌─────────────────────────────────────────────────────────────┐
│ ← Dashboard                                 Goal            │
├─────────────────────────────────────────────────────────────┤

목표 달성 현황

2 / 5

──────────────────────────────────────────────────────────────

🏠 내집 마련

57%

228,000,000 / 400,000,000

2031.12 목표

>

──────────────────────────────────────────────────────────────

📈 장기 투자

43%

21,500,000 / 50,000,000

>

──────────────────────────────────────────────────────────────

🛡 노후 준비

12%

>

```

---

# Goal Summary Widget

표시 정보

- 전체 목표 개수
- 달성 완료 목표
- 진행 중 목표

클릭 없음

---

# Goal Card

각 목표는 Card로 표시한다.

Card에는

- 목표 이름
- 아이콘
- 목표 금액
- 현재 금액
- 진행률
- 예상 달성일

을 표시한다.

---

# Goal Detail

Goal Card를 선택하면 상세 화면으로 이동한다.

상세 화면에는

- 목표 정보
- 진행률
- 목표 자산
- 부족 금액
- 추천 행동

을 표시한다.

---

# Goal Assets

목표는 Purpose가 같은 자산을 자동으로 합산한다.

예시

내집 마련

↓

국민은행 예금

↓

한국투자 ISA ETF

↓

채권

↓

BTC

↓

자동 합산

사용자가 직접 자산을 연결하지 않는다.

---

# Progress Calculation

진행률

=

현재 평가금액

÷

목표금액

×

100

모든 계산은 평가금액 기준이다.

---

# Estimated Completion

목표 달성 예상일은

현재 자산 증가 속도를 기반으로 계산한다.

Version 1에서는

단순 계산을 사용한다.

향후에는

AI 예측으로 변경 가능하다.

---

# Recommendation Widget

목표별 추천 행동을 표시한다.

예시

생활비 계좌 잔액이 많습니다.

↓

내집 마련 목표에 추가할 수 있습니다.

---

이번 달 목표 금액보다 적게 저축했습니다.

↓

추가 저축을 권장합니다.

---

# Goal Creation

사용자는 목표를 생성할 수 있다.

필수 정보

- 목표명
- 목표 금액
- 목표 날짜

선택

- 아이콘
- 색상
- 설명

---

# Goal Edit

수정 가능

- 목표명
- 금액
- 날짜
- 설명

목표 삭제

↓

확인 Dialog

↓

삭제

---

# Default Goals

Version 1

기본 제공

- 내집 마련
- 장기 투자
- 노후 준비

사용자는 자유롭게 추가 가능하다.

---

# Goal Status

진행 중

달성 완료

일시 중단

보관

---

# Interaction

Hover

Card Shadow

Click

Goal Detail

Animation

200ms 이하

---

# Empty State

등록된 목표가 없습니다.

↓

[ 목표 만들기 ]

---

# Loading

Skeleton 사용

---

# Required Data

Goal ID

Goal Name

Target Amount

Current Amount

Target Date

Purpose

Status

Created At

Updated At

---

# Database Requirements

Entities

Goal

Purpose

Asset

GoalHistory

---

# API Requirements

GET /goals

GET /goal/{id}

POST /goal

PUT /goal

DELETE /goal

---

# Validation Rules

모든 목표는

- 이름
- 목표금액

을 가져야 한다.

목표금액은

0보다 커야 한다.

---

# V1 Scope

포함

- 목표 생성
- 수정
- 삭제
- 진행률 계산
- Goal Card
- Goal Detail

제외

- AI 예측
- 자동 추천 개선
- 목표별 리포트
- 목표 달성 알림

---

# Future Features

- AI 예상 달성일
- 목표별 투자 추천
- 자동 리포트
- 목표 히스토리
- 여러 목표 비교

---

# Definition of Done

완료 조건

- Goal Summary 구현
- Goal List 구현
- Goal Detail 구현
- Progress 계산 구현
- Recommendation 연결
- Dashboard 연동

---

# Figma AI Prompt

Design a modern desktop financial goal management page.

Style

- Professional
- Minimal
- White background
- Card based UI
- Rounded cards
- Soft shadows

Requirements

- Goal summary card
- Goal progress cards
- Progress bar
- Recommendation card
- Goal detail page
- Consistent with Asset and Investment pages

---

# Review Checklist

- [ ] Vision과 일치하는가?
- [ ] RuleBook을 따르는가?
- [ ] UserFlow와 연결되는가?
- [ ] Goal은 Purpose 기반으로 계산되는가?
- [ ] Dashboard와 연결되는가?
- [ ] Cursor가 구현 가능한가?
- [ ] V1 범위를 벗어나지 않는가?

---

# Notes

Goal은 Atlas의 최종 목적지이다.

Asset와 Investment는 Goal을 달성하기 위한 수단이다.

사용자는 Goal 화면에서 자신의 현재 위치와 앞으로 해야 할 행동을 이해할 수 있어야 한다.