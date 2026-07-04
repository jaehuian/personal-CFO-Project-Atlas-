# Atlas API Specification

Version: 1.0

Status: Architecture Freeze

Owner: Project Atlas

Related Documents

- ../01_DomainModel.md
- ../02_Database.md
- ../03_ERD.md

---

# Purpose

본 문서는 Atlas API의 공통 규칙을 정의한다.

각 Resource API는 본 문서를 기반으로 작성되며,
공통 규칙은 모든 API에 동일하게 적용된다.

API는 Domain Model을 구현하기 위한 계약(Contract)이다.

---

# API Philosophy

Atlas는 Domain Driven REST API를 사용한다.

API는 화면(Page)이 아니라 Domain(Resource)을 기준으로 설계한다.

예를 들어 Dashboard는 하나의 화면이지만,

Dashboard 전용 API는 존재하지 않는다.

Dashboard는 여러 Resource를 조합하여 구성한다.

---

# API Principles

## Resource First

모든 API는 Resource를 기준으로 작성한다.

예)

- Goal
- Purpose
- Institution
- Account
- Asset
- Investment
- Transaction
- Rule

---

## RESTful

HTTP Method의 의미를 따른다.

| Method | Purpose |
|---------|----------|
| GET | 조회 |
| POST | 생성 |
| PUT | 전체 수정 |
| PATCH | 부분 수정 |
| DELETE | 삭제 |

---

## Stateless

모든 요청은 독립적으로 처리한다.

Server는 Client 상태를 저장하지 않는다.

---

## Predictable

동일한 요청은 항상 동일한 결과를 반환해야 한다.

---

# URL Convention

기본 URL

```
/api/v1
```

예)

```
/api/v1/assets
```

---

Resource는 항상 복수형을 사용한다.

좋은 예

```
/assets
/goals
/purposes
```

좋지 않은 예

```
/asset
/getAssets
```

---

# API Structure

모든 Resource는 동일한 구조를 가진다.

```
Resource

↓

DTO

↓

Validation

↓

Endpoint

↓

Error

↓

Example
```

---

# Request Format

Request Body는 JSON을 사용한다.

예)

```json
{
  "name": "생활비 통장"
}
```

---

# Response Format

성공 응답은 Resource 자체를 반환한다.

예)

```json
{
  "id": "...",
  "name": "...",
  "createdAt": "...",
  "updatedAt": "..."
}
```

---

Collection 조회

```json
[
  { ... },
  { ... }
]
```

---

# Error Response

모든 Error는 동일한 형식을 사용한다.

```json
{
  "code": "PURPOSE_NOT_FOUND",
  "message": "Purpose not found."
}
```

---

# Common Error Codes

Validation

- VALIDATION_FAILED
- INVALID_REQUEST

---

Authentication

- UNAUTHORIZED

---

Authorization

- FORBIDDEN

---

Resource

- GOAL_NOT_FOUND
- PURPOSE_NOT_FOUND
- ACCOUNT_NOT_FOUND
- ASSET_NOT_FOUND
- INVESTMENT_NOT_FOUND
- TRANSACTION_NOT_FOUND

---

Conflict

- DUPLICATED_NAME
- RESOURCE_IN_USE

---

Server

- INTERNAL_SERVER_ERROR

---

# HTTP Status Code

| Status | Meaning |
|---------|----------|
| 200 | Success |
| 201 | Created |
| 204 | No Content |
| 400 | Bad Request |
| 401 | Unauthorized |
| 403 | Forbidden |
| 404 | Not Found |
| 409 | Conflict |
| 500 | Internal Server Error |

---

# Pagination

List 조회는 Pagination을 지원한다.

Query

```
?page=1&pageSize=20
```

Response

```json
{
  "items": [],
  "page": 1,
  "pageSize": 20,
  "total": 120
}
```

---

# Sorting

모든 List API는 정렬을 지원한다.

예)

```
?sort=name
```

```
?sort=createdAt
```

```
?order=asc
```

```
?order=desc
```

---

# Filtering

필요한 Resource는 Filter를 지원한다.

예)

```
?purposeId=...
```

```
?accountId=...
```

```
?investmentType=ETF
```

---

# Search

검색은 q Parameter를 사용한다.

예)

```
?q=ETF
```

---

# Validation Rules

Validation은

Controller 이전에 수행한다.

Validation 실패 시

```
400 Bad Request
```

를 반환한다.

---

# Authentication

Version 1

로그인 기능 없음

Local User

---

Version 2

JWT

---

Version 3

OAuth

---

# Versioning

모든 API는 Version을 포함한다.

```
/api/v1
```

Version이 변경되어도

기존 Version은 유지한다.

---

# Naming Convention

## Resource

복수형

```
assets
```

---

## Parameter

camelCase

```
pageSize
```

---

## JSON Property

camelCase

```
createdAt
```

---

## Database

snake_case

```
created_at
```

---

# Resource Documents

- Goal.md
- Purpose.md
- Institution.md
- Account.md
- Asset.md
- Investment.md
- Transaction.md
- Rule.md

---

# Future Expansion

Version 2

- Batch API
- Import / Export
- Cursor Pagination

---

Version 2.2

- Template API
- Milestone API

---

Version 3

- Sync API
- Notification API
- Open Banking API

---

# Review Checklist

- [ ] RESTful API인가?
- [ ] Resource 중심인가?
- [ ] Domain Model과 일치하는가?
- [ ] Database와 일치하는가?
- [ ] ERD와 일치하는가?
- [ ] 모든 API가 공통 규칙을 따르는가?

---

# Notes

API는 UI를 위한 인터페이스가 아니다.

API는 Domain을 외부에 노출하는 계약(Contract)이다.

모든 Resource API는 본 문서의 규칙을 따른다.