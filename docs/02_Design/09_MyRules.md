# My Rules Page Specification

Version: 2.0

Status: Draft

Owner: Project Atlas

Related Documents

- 01_Vision.md
- 02_RuleBook.md
- 03_UserFlow.md
- 04_Dashboard.md
- 05_Asset.md
- 06_Investment.md
- 07_Goal.md
- 08_Ledger.md

---

# Purpose

My Rules는 사용자의 자산관리 원칙을 설정하는 화면이다.

Atlas는 사용자가 입력한 원칙을 기반으로 Dashboard에서 추천을 생성한다.

Version 1에서는 Rule를 자동 실행하지 않는다.

사용자가 직접 판단하고 실행할 수 있도록 돕는다.

---

# Goals

사용자는

"나는 돈을 이렇게 관리한다."

라는 자신의 기준을 쉽고 빠르게 설정할 수 있어야 한다.

---

# Design Philosophy

사용자는 Rule를 만들지 않는다.

사용자는 자신의 관리 기준을 설정한다.

Atlas는 그 기준을 이해하여 추천을 생성한다.

---

# Screen Layout

```
Header

↓

Rule Summary

↓

Template Gallery

↓

My Rules

↓

Rule Detail
```

---

# Wireframe

```
┌────────────────────────────────────────────────────────────┐
│ ← Dashboard                            나의 원칙          │
├────────────────────────────────────────────────────────────┤

현재 적용 중인 원칙

5개

────────────────────────────────────────────────────────────

새 원칙 추가

🏠 내집마련

💰 생활비

🛡 비상금

📈 투자

💾 저축

⚙ 직접 만들기

────────────────────────────────────────────────────────────

적용 중인 원칙

────────────────────────────────────────────

💰 생활비

100만원 유지

>

────────────────────────────────────────────

🛡 비상금

500만원 목표

>

────────────────────────────────────────────

🏠 내집마련

4억원 목표

>

```

---

# Rule Summary

표시 정보

- 적용 중인 원칙 개수
- 기본 원칙 개수
- 사용자 생성 원칙 개수

---

# Template Gallery

Version 1에서 제공하는 기본 템플릿

- 생활비 관리
- 비상금 관리
- 내집마련
- 투자 관리
- 저축 목표
- 직접 만들기

Template를 선택하면 바로 설정 화면으로 이동한다.

---

# Rule Templates

## 생활비 관리

질문

생활계좌에 얼마를 남겨두시겠습니까?

입력

금액

추천 예시

생활계좌 잔액이 목표보다 많습니다.

예금으로 이동하는 것을 추천합니다.

---

## 비상금 관리

질문

비상금을 얼마까지 모으시겠습니까?

입력

목표 금액

추천 예시

비상금이 목표보다 부족합니다.

---

## 내집마련

질문

내집마련 목표 금액은 얼마입니까?

입력

목표 금액

추천 예시

현재 목표의 58%를 달성했습니다.

---

## 저축 목표

질문

매달 얼마를 저축하고 싶습니까?

입력

월 목표 금액

추천 예시

이번 달 목표보다 적게 저축했습니다.

---

## 투자 관리

질문

현금 비중을 얼마나 유지하시겠습니까?

입력

목표 비율

추천 예시

현재 현금 비중이 목표보다 높습니다.

---

## 직접 만들기 (Advanced)

Version 1에서는

간단한 사용자 정의 Rule만 지원한다.

자동 실행은 지원하지 않는다.

---

# Rule Detail

각 원칙은 다음 정보를 가진다.

- 이름
- 설명
- 현재 설정값
- 마지막 수정일

수정

삭제

활성화

비활성화

지원

---

# Dashboard Connection

Dashboard Recommendation Widget은

My Rules를 우선적으로 참고한다.

예시

생활계좌

250만원

↓

생활비 Rule

100만원

↓

추천

150만원을 예금으로 이동하는 것을 추천합니다.

---

# Goal Connection

Goal 진행률 계산에는 영향을 주지 않는다.

추천 생성에만 사용한다.

---

# Asset Connection

Purpose 변경에는 영향을 주지 않는다.

추천 생성에만 사용한다.

---

# Investment Connection

Version 1에서는

추천만 생성한다.

자동 리밸런싱은 지원하지 않는다.

---

# Interaction

Hover

Card Shadow

Click

Rule Detail

Template

즉시 생성

---

# Empty State

아직 설정된 원칙이 없습니다.

기본 원칙을 추가해보세요.

[ 시작하기 ]

---

# Required Data

Rule ID

Template ID

Rule Name

Description

Target Value

Enabled

Created At

Updated At

---

# Database Requirements

Entities

RuleTemplate

UserRule

Recommendation

---

# API Requirements

GET /rule-templates

GET /my-rules

POST /my-rule

PUT /my-rule

DELETE /my-rule

---

# Validation Rules

Rule는 반드시

- 이름
- 목표값

을 가져야 한다.

목표값은 0 이상이어야 한다.

---

# V1 Scope

포함

- 템플릿 선택
- Rule 생성
- Rule 수정
- Rule 삭제
- Dashboard 추천 연결

제외

- 자동 실행
- AI Rule 생성
- Marketplace
- Rule 공유
- Script 방식 Rule

---

# Future Features

Version 1.2

- 추천 강도 설정
- Rule 우선순위

Version 2

- 사용자 정의 템플릿
- Rule 가져오기
- Rule 내보내기

Version 3

- AI Rule 추천
- Rule 자동 생성

---

# Platform Strategy

Desktop

모든 기능 지원

Mobile (V3)

조회

간단한 수정

지원

Template 생성

지원

고급 설정

지원하지 않음

---

# Definition of Done

- Rule Summary
- Template Gallery
- My Rules List
- Rule Detail
- CRUD
- Dashboard Recommendation 연동

---

# Figma AI Prompt

Design a desktop personal finance rule management page.

Style

- Minimal
- White background
- Rounded cards (16px)
- Card-based layout
- Clean typography
- Professional financial dashboard

Requirements

- Summary card
- Template gallery with large selectable cards
- Active rules list
- Rule detail page
- Consistent with Atlas Design System
- Desktop (1440px)

---

# Review Checklist

- [ ] Vision과 일치하는가?
- [ ] RuleBook과 연결되는가?
- [ ] Dashboard Recommendation과 연결되는가?
- [ ] Template 기반 UX인가?
- [ ] 일반 사용자도 쉽게 이해할 수 있는가?
- [ ] Cursor가 구현 가능한가?
- [ ] V1 범위를 벗어나지 않는가?

---

# Notes

My Rules는 Atlas의 핵심 차별화 기능이다.

사용자는 Rule를 작성하지 않는다.

사용자는 자신의 자산관리 기준을 설정한다.

Atlas는 이 기준을 기반으로 사용자가 더 좋은 의사결정을 할 수 있도록 추천을 제공한다.