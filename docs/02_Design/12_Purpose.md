# Purpose Page Specification

Version: 2.0

Status: Architecture Freeze Candidate

Owner: Project Atlas

Display Name: Purpose

Related Documents

- 00_StyleGuide.md
- 01_DesignSystem.md
- 02_Component.md
- 03_Widget.md
- 04_Dashboard.md
- ../03_Architecture/01_DomainModel.md
- ../01_Product/01_Vision.md
- ../01_Product/02_RuleBook.md

---

# Purpose

Purpose는 Atlas의 핵심 관리 화면이다.

Purpose는 돈의 "이유(Why)"를 정의한다.

모든 Asset와 Investment는 반드시 하나의 Purpose를 가진다.

Goal은 선택적으로 Purpose와 연결된다.

---

# Design Philosophy

Purpose는

돈을 어디에 보관하는지를 관리하는 화면이 아니다.

돈이 왜 존재하는지를 관리하는 화면이다.

Purpose는 Atlas에서 가장 중요한 Domain이다.

---

# User Question

사용자는 이 화면에서 다음 질문에 답할 수 있어야 한다.

- 나는 어떤 목적을 위해 돈을 관리하고 있는가?
- 각 Purpose에는 얼마나 많은 자산이 연결되어 있는가?
- Goal이 연결된 Purpose는 무엇인가?
- 관리되지 않는 Purpose는 있는가?

---

# Screen Responsibilities

Purpose는 다음 기능을 담당한다.

- Purpose 조회
- Purpose 생성
- Purpose 수정
- Purpose 삭제
- Goal 연결
- Goal 연결 해제

Purpose는 Asset와 Investment를 직접 수정하지 않는다.

---

# Screen Structure

Header

↓

Summary

↓

Purpose List

↓

Detail Panel

---

# Summary

표시 정보

- Purpose 개수
- Goal 연결 개수
- Goal 미연결 개수
- 총 연결 자산

Summary는 읽기 전용이다.

---

# Purpose List

Purpose는 Card 형태로 표시한다.

각 Card는 다음 정보를 표시한다.

- Purpose 이름
- 총 자산
- Asset 개수
- Investment 개수
- Goal 연결 여부
- Goal 진행률(Optional)

Goal이 없는 경우

진행률은 표시하지 않는다.

클릭 시 Detail Panel을 표시한다.

---

# Detail Panel

표시 정보

- Purpose 이름
- 설명
- Goal(Optional)
- 총 자산
- Asset 목록
- Investment 목록

---

# Available Actions

- Purpose 수정
- Goal 연결
- Goal 연결 해제
- Asset 화면으로 이동
- Investment 화면으로 이동

Purpose 삭제는 별도 Action으로 제공한다.

---

# Purpose Registration

필수 입력

- Purpose 이름

선택 입력

- 설명

Goal은 등록 시 연결하지 않는다.

필요한 경우 생성 후 연결한다.

---

# Goal Connection

사용자는 기존 Goal을 선택하여 연결할 수 있다.

또는

새 Goal을 생성한 뒤 연결할 수 있다.

Goal 연결은 언제든 변경할 수 있다.

---

# Delete Rules

Purpose는 다음 조건에서만 삭제할 수 있다.

- 연결된 Asset 없음
- 연결된 Investment 없음

삭제 시 확인 Dialog를 표시한다.

---

# Navigation

Dashboard

↓

Purpose

Purpose

↓

Asset

Purpose

↓

Investment

Purpose

↓

Goal

---

# Interaction

Hover

Card Shadow

Click

Detail 표시

자동 저장

저장 버튼은 사용하지 않는다.

---

# Empty State

아직 Purpose가 없습니다.

Purpose를 만들면 자산을 목적별로 관리할 수 있습니다.

[ Purpose 만들기 ]

---

# Platform Strategy

## Desktop

모든 기능 지원

---

## Mobile (V3)

지원

- 조회
- 생성
- 수정

제한

- 삭제
- 복잡한 관리

---

# Business Rules

Rule 1

Purpose는 Goal 없이 생성할 수 있다.

---

Rule 2

Goal은 선택적으로 연결된다.

---

Rule 3

모든 Asset는 반드시 하나의 Purpose를 가진다.

---

Rule 4

모든 Investment는 반드시 하나의 Purpose를 가진다.

---

Rule 5

Purpose 삭제 시 연결된 Asset와 Investment가 없어야 한다.

---

Rule 6

Purpose 이름은 중복을 허용하지 않는다.

---

# Data Model

Purpose

- id
- name
- description
- goalId (Nullable)
- createdAt
- updatedAt

---

# API

GET /purposes

POST /purposes

PUT /purposes/{id}

DELETE /purposes/{id}

POST /purposes/{id}/goal

DELETE /purposes/{id}/goal

---

# V1 Scope

포함

- Purpose CRUD
- Goal 연결
- Goal 연결 해제
- 연결된 Asset 조회
- 연결된 Investment 조회

제외

- 계층형 Purpose
- Template
- Merge
- Archive
- 색상
- 아이콘

---

# Future Features

## Version 1.2

- Purpose 정렬
- 즐겨찾기
- 사용 통계

---

## Version 2

- Template
- Merge
- Archive
- AI 추천 Purpose

---

## Version 3

- 계층형 Purpose
- 공유 Purpose
- Workspace 지원

---

# Definition of Done

- Purpose CRUD 구현
- Goal 연결 구현
- Goal 해제 구현
- Dashboard 연동
- Asset/Investment 연동

---

# Figma AI Prompt

Design a desktop purpose management page for Atlas.

Requirements

- Professional financial application
- Card-based layout
- Summary section
- Purpose cards
- Detail panel
- Goal progress (optional)
- White background
- Rounded cards (16px)
- Desktop 1440px
- Consistent with Atlas Design System

---

# Review Checklist

- [ ] Purpose가 독립적으로 관리되는가?
- [ ] Goal이 Optional인가?
- [ ] Asset/Investment가 Purpose를 참조하는가?
- [ ] Dashboard와 일관성이 있는가?
- [ ] Component System과 일치하는가?
- [ ] DomainModel과 일치하는가?

---

# Notes

Purpose는 Atlas의 핵심 Domain이다.

Goal은 "무엇을 이루고 싶은가"를 정의한다.

Purpose는 "왜 이 돈이 존재하는가"를 정의한다.

Asset는 "어디에 돈이 있는가"를 관리한다.

Investment는 "돈을 어떻게 운용하는가"를 관리한다.

Atlas는 이 네 가지를 Purpose를 중심으로 연결한다.