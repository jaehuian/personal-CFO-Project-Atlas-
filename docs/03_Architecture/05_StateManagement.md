# Atlas State Management

Version: 1.0

Status: Architecture Freeze

Owner: Project Atlas

Related Documents

- 01_DomainModel.md
- 02_Database.md
- 03_ERD.md
- 04_API/
- 06_FolderStructure.md
- ../04_Technical/01_TechStack.md

---

# Purpose

본 문서는 Atlas의 상태 관리 전략을 정의한다.

모든 React Component는 본 문서의 규칙을 따른다.

Atlas는 상태를 목적에 따라 분리하여 관리한다.

---

# Design Philosophy

State는 한 곳에서만 관리한다.

동일한 데이터를 여러 Store에 저장하지 않는다.

Derived State는 계산으로 해결하고,

중복 저장하지 않는다.

---

# State Categories

Atlas는 총 5개의 State를 사용한다.

| State | Description | Tool |
|--------|-------------|------|
| Server State | API 데이터 | React Query |
| UI State | Dialog, Sidebar, Tab | Zustand |
| Form State | 입력값 | React Hook Form |
| Settings State | 사용자 설정 | Zustand + LocalStorage |
| Derived State | 계산 결과 | Selector |

---

# State Flow

```
API

↓

React Query

↓

Domain Store (Zustand)

↓

Component

↓

UI
```

---

# Server State

관리 대상

- Goal
- Purpose
- Institution
- Account
- Asset
- Investment
- Transaction
- Rule

Server State는 React Query가 관리한다.

직접 Zustand에 저장하지 않는다.

---

# UI State

관리 대상

- Sidebar
- Dialog
- Modal
- Drawer
- Selected Tab
- Detail Panel
- Toast

UI 상태는 Zustand가 관리한다.

---

# Form State

관리 대상

- Create Form
- Edit Form
- Validation
- Dirty State

React Hook Form을 사용한다.

입력 중인 데이터는 Store에 저장하지 않는다.

---

# Settings State

관리 대상

- Theme
- Language
- Currency
- Snapshot Day
- Dashboard Layout

LocalStorage에 저장한다.

앱 시작 시 자동으로 복원한다.

---

# Derived State

직접 저장하지 않는다.

필요 시 계산한다.

예)

- Total Asset
- Total Investment
- Net Worth
- Goal Progress
- Asset Allocation

---

# Store Structure

```
stores/

ui/

settings/

snapshot/
```

---

# UI Store

예)

```
uiStore

sidebarOpen

selectedTab

dialogOpen
```

---

# Settings Store

예)

```
settingsStore

theme

currency

snapshotDay

language
```

---

# Snapshot Store

Snapshot 생성 여부를 관리한다.

```
snapshotStore

lastSnapshotMonth

isCreating

needsSnapshot
```

실제 Snapshot 데이터는 Server State이다.

Store는 생성 상태만 관리한다.

---

# React Query

Query Key

```
goals

purposes

accounts

assets

investments

transactions

rules
```

예)

```
["assets"]

["asset", id]

["investments"]

["dashboard"]
```

---

# Cache Policy

일반 조회

5분

---

Dashboard

1분

---

Settings

Infinity

---

Snapshot

Manual Refresh

---

# Mutation Flow

```
Create

↓

API

↓

Success

↓

Invalidate Query

↓

Refetch

↓

UI Update
```

---

# Snapshot Engine

앱 시작 또는

Dashboard / Asset / Investment 화면 진입 시

SnapshotService.check()

를 실행한다.

조건

- Snapshot Day 경과
- 이번 달 Snapshot 없음

조건을 만족하면

Snapshot 생성 후 Query를 Refresh한다.

---

# Local Storage

저장 대상

- Theme
- Language
- Snapshot Day
- Sidebar Width
- Dashboard Layout

저장하지 않는 대상

- Asset
- Investment
- Transaction

---

# State Rules

Rule 1

Server State를 Zustand에 복사하지 않는다.

---

Rule 2

Derived State를 저장하지 않는다.

---

Rule 3

React Query를 Server State의 Single Source of Truth로 사용한다.

---

Rule 4

UI State와 Domain State를 혼합하지 않는다.

---

Rule 5

Form 입력값은 Form 내부에서만 관리한다.

---

# Future Expansion

Version 2

- Offline Cache
- Optimistic Update

Version 2.2

- Background Sync
- Snapshot Queue

Version 3

- Multi Device Sync
- Cloud Sync

---

# Review Checklist

- [ ] Server State가 분리되었는가?
- [ ] UI State가 분리되었는가?
- [ ] Form State가 분리되었는가?
- [ ] Derived State를 저장하지 않는가?
- [ ] Snapshot Engine과 연동되는가?
- [ ] React Query가 Server State를 관리하는가?

---

# Notes

Atlas는 상태를 목적에 따라 분리하여 관리한다.

각 State는 하나의 책임만 가지며,

동일한 데이터는 하나의 Source에서만 관리한다.