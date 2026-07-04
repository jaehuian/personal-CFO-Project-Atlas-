# Onboarding Page Specification

Version: 1.0

Status: Draft

Owner: Project Atlas

Display Name: 시작하기

Related Documents

- 00_StyleGuide.md
- 01_DesignSystem.md
- 02_Component.md
- 03_Widget.md
- 04_Dashboard.md
- 05_Asset.md
- 07_Goal.md
- 09_MyRules.md
- ../01_Product/01_Vision.md
- ../01_Product/02_RuleBook.md
- ../01_Product/03_UserFlow.md

---

# Purpose

Onboarding은 사용자가 Atlas를 사용할 수 있는 최소 환경을 만드는 과정이다.

Atlas의 목표는 모든 정보를 입력하는 것이 아니라,

Dashboard를 사용할 수 있는 상태를 만드는 것이다.

---

# Design Philosophy

Onboarding은 길면 안 된다.

사용자는 5분 안에 Dashboard를 사용할 수 있어야 한다.

필수 정보만 입력받고,

나머지는 나중에 입력하도록 설계한다.

---

# User Question

사용자는 이 과정에서 다음 질문에 답할 수 있어야 한다.

- 무엇부터 시작하면 되는가?
- 최소한 무엇을 입력해야 하는가?
- 언제 Dashboard를 사용할 수 있는가?

---

# Success Criteria

Onboarding이 완료되면 사용자는

- Dashboard를 사용할 수 있어야 한다.
- 첫 Goal이 생성되어 있어야 한다.
- 첫 Account가 생성되어 있어야 한다.

---

# Onboarding Structure

Atlas는 2단계 Onboarding을 제공한다.

```
Step 1

↓

Dashboard 사용 가능

↓

Step 2 (선택)

↓

완료
```

---

# Step 1 (Required)

목표

Dashboard 사용 가능 상태 만들기

---

## Screen 1

환영

```
Atlas에 오신 것을 환영합니다.

돈을 기록하는 것이 아니라,

목표를 관리하는 프로그램입니다.

[ 시작하기 ]
```

---

## Screen 2

Goal 생성

입력

- 목표 이름
- 목표 금액

선택

- 목표일

예)

내집마련

4억원

---

## Screen 3

생활 계좌 등록

입력

- 계좌명
- 계좌 종류
- 현재 금액

예)

국민은행

입출금

230만원

---

## Screen 4

완료

```
준비가 끝났습니다.

이제 Dashboard를 사용할 수 있습니다.

[ Dashboard ]
```

---

# Step 2 (Optional)

Dashboard 첫 진입 후 카드 형태로 제공한다.

```
Atlas를 더 나에게 맞게 만들어볼까요?

[ 관리 원칙 설정 ]

[ 나중에 ]
```

---

# Management Principles Setup

Template 기반

예)

생활계좌 최소 잔액

100만원

---

비상금

500만원

---

투자 비중 유지

ON

---

사용자는

ON/OFF와 값만 수정한다.

---

# Empty Dashboard

Step 1 이전에는 Dashboard를 표시하지 않는다.

Step 1 완료 후 Dashboard를 시작 화면으로 사용한다.

---

# Skip Policy

Step 1은 건너뛸 수 없다.

Step 2는 언제든 건너뛸 수 있다.

---

# Navigation Rules

```
Welcome

↓

Goal

↓

Account

↓

Dashboard

↓

Management Principles (Optional)
```

뒤로 가기는 지원한다.

Dashboard 이후에는 Onboarding으로 돌아가지 않는다.

---

# Interaction

Next 버튼은

필수 입력 완료 후 활성화된다.

자동 저장을 사용한다.

저장 버튼은 제공하지 않는다.

---

# Validation Rules

Goal

- 이름 필수
- 목표 금액 > 0

Account

- 이름 필수
- 계좌 종류 필수

---

# Empty State

Onboarding은 Empty State를 가지지 않는다.

---

# Platform Strategy

## Desktop

전체 Onboarding 제공

---

## Mobile (V3)

Step 1만 제공

Step 2는 Dashboard에서 진행

---

# V1 Scope

포함

- Welcome
- Goal 생성
- 첫 Account 생성
- Dashboard 이동
- 선택형 Management Principles

제외

- Open Banking
- 계좌 자동 등록
- AI 추천
- 사용자 맞춤 Onboarding

---

# Future Features

## Version 1.2

- 진행률 표시
- Onboarding 이어하기

---

## Version 2

- Open Banking 연동
- Goal Template
- 자동 데이터 입력

---

## Version 3

- Mobile 전용 Onboarding
- 음성 안내

---

# Definition of Done

- Welcome Screen
- Goal 생성
- 첫 Account 생성
- Dashboard 이동
- Optional Rule Setup

---

# Figma AI Prompt

Design a desktop onboarding flow for Atlas.

Requirements

- Clean and minimal
- Maximum 4 screens
- Step-by-step wizard
- White background
- Rounded cards
- Progress indicator
- Professional financial application
- Consistent with Atlas Design System

---

# Review Checklist

- [ ] 5분 안에 완료 가능한가?
- [ ] Dashboard를 사용할 수 있는 상태가 되는가?
- [ ] 필수 입력만 받는가?
- [ ] Goal과 Account가 생성되는가?
- [ ] Management Principles는 선택 사항인가?
- [ ] Desktop First 원칙을 따르는가?
- [ ] V1 범위를 벗어나지 않는가?

---

# Notes

Onboarding의 목적은

모든 데이터를 입력받는 것이 아니다.

사용자가 가능한 빨리 Dashboard를 사용할 수 있도록 돕는 것이다.

Dashboard는 Atlas의 시작점이며,

Onboarding은 그 시작점까지 안내하는 과정이다.