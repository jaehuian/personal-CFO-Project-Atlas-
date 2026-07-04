# Atlas Rule Book

Version: 1.0

Status: Draft

Owner: Project Atlas

Related Documents

- 01_Vision.md
- 03_UserFlow.md
- 01_DesignSystem.md

---

# Purpose

이 문서는 Atlas가 자산을 관리하고 사용자에게 정보를 제공하는 모든 핵심 규칙(Business Rules)을 정의한다.

모든 기능은 본 문서의 규칙을 따른다.

새로운 기능을 추가할 때는 반드시 RuleBook을 먼저 검토한다.

---

# Rule Philosophy

Atlas는 데이터를 저장하는 프로그램이 아니다.

Atlas는 규칙(Rule)을 기반으로 사용자의 자산을 관리하는 프로그램이다.

모든 화면과 기능은 동일한 Rule을 공유한다.

---

# Core Rules

## Rule 01

모든 자산은 반드시 하나의 목적(Purpose)을 가진다.

허용되는 목적 예시

- 생활비
- 비상금
- 내집마련
- 장기투자
- 노후준비
- 기타

목적이 없는 자산은 존재할 수 없다.

---

## Rule 02

모든 자산은 하나의 계좌(Account)에 속한다.

예)

국민은행

신한은행

한국투자증권

코인원

바이낸스

ISA

연금저축

---

## Rule 03

하나의 계좌에는 여러 자산이 존재할 수 있다.

예)

한국투자 ISA

↓

QQQ

↓

금 ETF

↓

채권 ETF

---

## Rule 04

하나의 자산은 하나의 목적만 가진다.

동일한 자산을 여러 목적에 동시에 사용할 수 없다.

필요한 경우 사용자가 목적을 변경한다.

---

## Rule 05

목적은 언제든지 변경할 수 있다.

예)

QQQ

내집마련

↓

장기투자

↓

Dashboard와 Goal은 자동 갱신된다.

---

## Rule 06

모든 금액은 현재 평가금액(Market Value)을 기준으로 계산한다.

매수금액은 기록용으로만 사용한다.

순자산

목표 진행률

자산 비중

Dashboard

모두 평가금액 기준이다.

---

## Rule 07

원화(KRW)를 기준 통화로 사용한다.

외화 및 암호화폐는 실시간 환율을 적용하여 원화로 환산한다.

---

## Rule 08

Dashboard는 항상 요약 정보만 표시한다.

상세 정보는 각 화면에서 확인한다.

---

## Rule 09

같은 데이터는 한 곳에서만 관리한다.

중복 데이터를 저장하지 않는다.

모든 화면은 동일한 데이터를 참조한다.

---

## Rule 10

모든 추천(Action Recommendation)은 Rule을 기반으로 생성된다.

추천은 AI가 아니라 규칙을 먼저 따른다.

---

# Asset Rules

자산은 다음과 같이 분류한다.

입출금

예적금

투자

연금

기타

---

투자는

주식

ETF

채권

코인

현금성 자산

등으로 다시 분류할 수 있다.

---

# Goal Rules

모든 목표는

목표 금액

현재 금액

목표 날짜

를 가진다.

현재 금액은

목적이 같은 자산의 합계이다.

---

예)

내집마련

↓

예금

↓

채권

↓

ETF

↓

BTC

↓

자동 합산

---

# Investment Rules

투자는

평가금액

기준으로 관리한다.

매수금액은 손익 계산에만 사용한다.

---

# Dashboard Rules

Dashboard는

현재 상태를 보여주는 화면이다.

Dashboard에서 데이터를 수정하지 않는다.

모든 수정은 해당 화면에서 수행한다.

---

# Account Rules

계좌는 저장 위치이다.

계좌는 목적이 아니다.

목적은 언제든지 변경될 수 있다.

---

# Purpose Rules

Purpose는 Atlas의 가장 중요한 개념이다.

Purpose는 사용자의 의도를 의미한다.

예)

생활

내집마련

노후

장기투자

비상금

기타

Purpose는 자유롭게 생성 및 수정할 수 있다.

시스템 기본 Purpose는 삭제할 수 없다.

---

# Recommendation Rules

추천 기능은 다음 순서로 판단한다.

1. Rule 기반 판단

2. 사용자 설정(My Rules)

3. AI 분석 (향후)

---

# Data Rules

모든 데이터는 하나의 Source of Truth를 가진다.

화면마다 별도의 계산을 하지 않는다.

---

# Design Rules

디자인보다 이해하기 쉬운 정보 전달을 우선한다.

복잡한 기능은 단계적으로 제공한다.

---

# Future Rules

향후 추가 예정

- 자동 투자 Rule
- 소비 분석 Rule
- 목표 예측 Rule
- 리스크 분석 Rule
- AI Recommendation Rule

---

# Rule Priority

충돌 시 우선순위

1. Rule Book

2. User Rules

3. Application Settings

4. Default Values

---

# Definition of Done

새로운 기능은

□ RuleBook에 위배되지 않아야 한다.

□ 새로운 Rule이 필요하면 RuleBook을 먼저 수정한다.

□ UI보다 Rule이 우선한다.

---

# Version History

v1.0

Initial Rule Book