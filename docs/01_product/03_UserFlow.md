# Atlas User Flow

Version: 1.1

Status: Draft

Owner: Project Atlas

Related Documents

- README.md
- 00_Common/01_Glossary.md
- 01_Vision.md
- 02_RuleBook.md

---

# Purpose

User Flow는 사용자가 Atlas를 사용하는 전체 흐름을 정의한다.

Atlas는 단순한 화면 이동이 아닌,

사용자의 의사결정 과정을 중심으로 설계한다.

모든 기능은 Dashboard를 중심으로 연결된다.

---

# Core User Journey

사용자는 항상 다음 순서로 Atlas를 사용한다.

```

Dashboard

↓

현재 상태 확인

↓

필요한 화면 이동

↓

정보 확인 또는 수정

↓

Dashboard 복귀

```

Dashboard는 시작점이며,

모든 작업의 종료 지점이다.

---

# Dashboard First

Atlas는 Dashboard 중심으로 동작한다.

Dashboard에서

현재 상태를 확인하고,

필요한 화면으로 이동한다.

Dashboard는

직접 데이터를 수정하지 않는다.

---

# Primary Navigation

Dashboard

↓

Asset

↓

Investment

↓

Goal

↓

Ledger

↓

Management Principles

각 화면은 Dashboard와 직접 연결된다.

화면 간 이동보다

Dashboard 복귀를 우선한다.

---

# Screen Responsibilities

## Dashboard

질문

현재 어떤 상태인가?

제공

- 자산 현황
- 투자 현황
- 목표 진행률
- 추천

---

## Asset

질문

내 돈은 어디에 있는가?

사용자는

Purpose

또는

Account

기준으로 자산을 확인한다.

---

## Investment

질문

내 투자는 어떤 상태인가?

사용자는

Portfolio

또는

Investment Type

기준으로 투자 자산을 관리한다.

---

## Goal

질문

목표까지 얼마나 남았는가?

사용자는

목표 진행률과

추천 행동을 확인한다.

---

## Ledger (가계부)

질문

이번 달 돈을 어떻게 사용했는가?

사용자는

거래를 기록하고 관리한다.

분석은 Dashboard가 담당한다.

---

## Management Principles

질문

나는 어떤 기준으로 돈을 관리하는가?

사용자는

자신의 자산관리 원칙을 설정한다.

---

# Dashboard Navigation

Dashboard Widget를 클릭하면

관련 화면으로 이동한다.

예시

순자산 Widget

↓

Asset

----------------

투자 Widget

↓

Investment

----------------

목표 Widget

↓

Goal

----------------

이번 달 소비

↓

Ledger

----------------

추천

↓

관련 화면

---

# Recommendation Flow

사용자의 관리 원칙

+

현재 데이터

↓

Recommendation Engine

↓

Dashboard

↓

사용자 판단

↓

관련 화면 이동

Atlas는 자동으로 실행하지 않는다.

---

# Data Flow

Ledger

↓

Asset

↓

Investment

↓

Goal

↓

Dashboard

↓

Recommendation

↓

User

데이터는 Dashboard를 향해 흐른다.

사용자는 Dashboard에서 다시 데이터를 탐색한다.

---

# First User Experience

최초 실행

↓

Onboarding

↓

Dashboard

↓

필요한 정보 등록

↓

Dashboard

Onboarding 이후

Dashboard를 Home으로 사용한다.

---

# Platform Strategy

## Desktop

모든 기능 제공

관리 중심

---

## Mobile (V3)

빠른 확인

간단한 입력

간단한 수정

Dashboard 중심

---

# Navigation Principles

Dashboard는 항상 첫 화면이다.

메뉴보다 Widget 이동을 우선한다.

사용자는

현재 상태를 보고

필요한 화면으로 이동한다.

각 화면은 하나의 역할만 가진다.

---

# User Questions

Atlas는 다음 질문에 답해야 한다.

Dashboard

"지금 내 상태는?"

----------------

Asset

"내 돈은 어디에 있지?"

----------------

Investment

"내 투자는 괜찮은가?"

----------------

Goal

"목표까지 얼마나 남았지?"

----------------

Ledger

"이번 달 얼마를 사용했지?"

----------------

Management Principles

"나는 어떤 기준으로 관리하지?"

---

# UX Rules

한 화면은

하나의 질문만 해결한다.

정보는 최소한으로 보여준다.

사용자는

생각보다 선택을 적게 한다.

추천은

Dashboard에서만 제공한다.

---

# Version History

## v1.1

- Dashboard First 구조 적용
- Recommendation Flow 추가
- Thinking Flow 중심으로 변경
- Platform Strategy 추가
- Navigation Principles 추가
- User Questions 추가