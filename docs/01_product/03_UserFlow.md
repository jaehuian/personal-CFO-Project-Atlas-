# Atlas User Flow

Version: 1.0

Status: Draft

Owner: Project Atlas

Related Documents

- 01_Vision.md
- 02_RuleBook.md
- README.md

---

# Purpose

이 문서는 Atlas에서 사용자가 자산을 관리하는 전체 흐름(User Journey)을 정의한다.

모든 화면 설계(UI/UX)는 본 문서를 기준으로 한다.

새로운 기능을 추가할 경우 먼저 User Flow를 검토한다.

---

# User Journey

Atlas에서 사용자는 아래 순서로 서비스를 이용한다.

```
Onboarding

↓

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

Dashboard
```

Dashboard는 항상 사용자의 시작점이며, 모든 관리가 끝난 후 다시 Dashboard로 돌아온다.

---

# User Flow Principles

Atlas는 화면보다 사용자의 행동을 중심으로 설계한다.

사용자는 다음 질문에 답하기 위해 Atlas를 실행한다.

- 지금 얼마를 가지고 있지?
- 내집마련은 얼마나 모였지?
- 이번 달 돈을 너무 많이 썼나?
- 지금 투자금을 더 넣어도 될까?

모든 화면은 이 질문 중 하나에 답해야 한다.

---

# First Launch

최초 실행

↓

환영 화면

↓

서비스 소개

↓

기본 정보 입력

↓

목표 설정

↓

기본 Purpose 생성

↓

Dashboard

---

# Onboarding

사용자가 입력하는 정보

- 이름(선택)
- 기준 통화
- 기본 목표
- 월급일
- 생활비 기준
- 비상금 기준
- 내집마련 목표
- 투자 여부

필수 입력은 최소화한다.

나머지는 언제든 변경 가능해야 한다.

---

# Dashboard Flow

Dashboard는 현재 상태를 보여주는 화면이다.

Dashboard에서는 수정하지 않는다.

사용자는 Widget을 클릭하여 각 화면으로 이동한다.

예)

```
Dashboard

↓

NetWorth Widget

↓

Asset
```

---

```
Dashboard

↓

Goal Widget

↓

Goal
```

---

```
Dashboard

↓

Investment Widget

↓

Investment
```

---

# Asset Flow

Asset에서는 자산을 관리한다.

```
Asset

↓

자산 추가

↓

계좌 선택

↓

목적 선택

↓

금액 입력

↓

저장

↓

Dashboard 자동 반영
```

---

자산 수정

```
Asset

↓

자산 선택

↓

목적 변경

↓

저장

↓

Dashboard 자동 반영
```

---

# Investment Flow

```
Investment

↓

투자 등록

↓

종목 선택

↓

계좌 선택

↓

목적 선택

↓

저장

↓

Dashboard 자동 반영
```

---

투자 수정

↓

평가금액 변경

↓

Dashboard 자동 계산

---

# Goal Flow

```
Goal

↓

목표 생성

↓

목표 금액 입력

↓

목표 날짜 입력

↓

저장
```

↓

Dashboard 자동 반영

---

목표 진행률은

목적(Purpose)이 같은 자산을 자동 합산한다.

사용자가 직접 계산하지 않는다.

---

# Ledger Flow

```
Ledger

↓

거래 등록

↓

수입

또는

지출

↓

카테고리 선택

↓

저장
```

↓

Dashboard 반영

↓

통계 반영

---

# Recommendation Flow

Dashboard

↓

Recommendation Widget

↓

관련 화면 이동

↓

사용자 수정

↓

Dashboard 업데이트

예)

생활비 계좌 잔액이 많습니다.

↓

예금으로 이동하세요.

↓

Asset

↓

목적 변경

↓

Dashboard

---

# Purpose Change Flow

Atlas의 핵심 기능

```
Asset

↓

자산 선택

↓

Purpose 변경

↓

저장

↓

Dashboard

↓

Goal

↓

Asset Allocation

↓

자동 갱신
```

사용자는 언제든 Purpose를 변경할 수 있다.

---

# Navigation Flow

Atlas는 메뉴 중심이 아니다.

Widget 중심으로 이동한다.

```
Dashboard

↓

Widget Click

↓

Page
```

모든 화면은 Dashboard로 돌아갈 수 있어야 한다.

---

# Error Flow

입력 오류

↓

원인 표시

↓

수정

↓

저장

에러 메시지는 사용자가 이해하기 쉬운 문장을 사용한다.

---

# Empty State Flow

데이터가 없는 경우

↓

안내 문구

↓

등록 버튼

↓

등록 화면

예)

"등록된 자산이 없습니다."

↓

[ 자산 추가 ]

---

# Future User Flow

향후 추가 예정

- 자동 거래내역 동기화
- 증권 API 연동
- AI 추천
- 소비 분석
- 목표 예측

Version 1에서는 포함하지 않는다.

---

# UX Principles

사용자는

생각하지 않아야 한다.

클릭 횟수는 최소화한다.

현재 위치를 쉽게 이해할 수 있어야 한다.

모든 주요 기능은 Dashboard에서 시작한다.

---

# Definition of Done

새로운 화면은

□ User Flow를 따른다.

□ Dashboard와 연결된다.

□ Purpose 구조를 유지한다.

□ RuleBook을 따른다.

---

# Version History

v1.0

Initial User Flow