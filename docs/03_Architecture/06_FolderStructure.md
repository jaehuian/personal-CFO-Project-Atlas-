# Atlas Folder Structure

Version: 1.0

Status: Architecture Freeze

Owner: Project Atlas

Related Documents

- 01_DomainModel.md
- 02_Database.md
- 03_ERD.md
- 04_API/
- 05_StateManagement.md
- ../04_Technical/01_TechStack.md

---

# Purpose

본 문서는 Atlas 프로젝트의 폴더 구조를 정의한다.

Atlas는 Feature First Architecture를 사용한다.

모든 기능은 Domain 단위로 구성한다.

---

# Design Philosophy

Atlas는 Layer보다 Domain을 우선한다.

관련된 파일은 같은 Feature 안에 위치한다.

Feature 간 의존성은 최소화한다.

Shared는 공통 기능만 가진다.

---

# Root Structure

```
src
│
├── app
├── features
├── shared
├── layouts
├── assets
├── styles
├── routes
├── providers
├── types
└── utils
```

---

# App

```
app

App.tsx

main.tsx
```

앱 시작점

---

# Features

```
features

goal

purpose

asset

investment

ledger

rule

dashboard

settings
```

모든 Domain은 Feature 단위로 관리한다.

---

# Feature Structure

모든 Feature는 동일한 구조를 가진다.

```
asset

components

hooks

pages

services

api

types

utils

index.ts
```

---

# Components

Feature 내부에서만 사용하는 UI

예)

```
AssetCard

AssetForm

AssetTable
```

---

# Hooks

Feature 전용 Hook

예)

```
useAssets

useCreateAsset

useUpdateAsset
```

---

# Services

비즈니스 로직

예)

```
AssetService

SnapshotService
```

---

# API

React Query

API 호출

DTO

예)

```
assetApi.ts

assetQuery.ts

assetMutation.ts
```

---

# Types

Feature 전용 Type

예)

```
Asset

AssetDto

CreateAssetRequest
```

---

# Utils

Feature 내부 Helper

예)

```
assetCalculator

assetFormatter
```

---

# Shared

공통 기능

```
shared

components

hooks

services

api

constants

icons

types

utils
```

---

# Shared Components

예)

```
Button

Dialog

Input

Card

Table

Tabs
```

---

# Shared Hooks

예)

```
useDebounce

useLocalStorage

useMediaQuery
```

---

# Shared Services

예)

```
DateService

CurrencyService

NumberService
```

---

# Shared API

공통 API 기능

예)

```
httpClient

queryClient

apiError
```

---

# Layouts

```
MainLayout

DashboardLayout

SettingsLayout
```

---

# Providers

```
QueryProvider

ThemeProvider

RouterProvider
```

---

# Routes

```
AppRoutes

ProtectedRoute
```

---

# Types

프로젝트 공통 Type

```
ApiResponse

Pagination

SortOption
```

---

# Utils

프로젝트 공통 Utility

```
date

currency

number

validation
```

---

# Naming Convention

Folder

kebab-case

```
asset-history
```

---

Component

PascalCase

```
AssetCard.tsx
```

---

Hook

camelCase

```
useAssets.ts
```

---

Service

PascalCase

```
AssetService.ts
```

---

API

camelCase

```
assetApi.ts
```

---

Type

PascalCase

```
Asset.ts

AssetDto.ts
```

---

# Dependency Rule

Feature는 다른 Feature를 직접 참조하지 않는다.

가능한 경우

Shared를 통해 공통 기능을 사용한다.

---

좋은 예

```
Asset

↓

Shared Currency Formatter
```

---

좋지 않은 예

```
Asset

↓

Investment 내부 Component
```

---

# Import Rule

Feature 내부

상대 경로 허용

---

Feature 간

Alias 사용

예)

```
@shared

@features
```

---

# Future Expansion

Version 2

```
portfolio

notification
```

---

Version 2.2

```
template

snapshot
```

---

Version 3

```
workspace

sync

cloud
```

---

# Review Checklist

- [ ] Feature First 구조인가?
- [ ] Domain 단위로 분리되어 있는가?
- [ ] Feature 간 의존성이 최소화되어 있는가?
- [ ] Shared가 공통 기능만 가지는가?
- [ ] API와 State 구조가 일치하는가?

---

# Notes

Atlas는 Domain 중심 구조를 사용한다.

기능을 추가할 때는 새로운 Layer를 만드는 것이 아니라,

새로운 Feature를 추가한다.