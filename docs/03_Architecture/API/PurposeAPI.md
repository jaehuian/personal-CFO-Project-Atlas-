# Purpose API

Version: 1.0

Status: Architecture Freeze

Owner: Project Atlas

Resource: Purpose

Base URL

/api/v1/purposes

Related Documents

- README.md
- ../../01_DomainModel.md
- ../../02_Database.md
- ../../03_ERD.md
- ../../../02_Design/05_Purpose.md

---

# Purpose

Purpose Resource를 관리한다.

Purpose는 Atlas의 핵심 Domain이며,

모든 Asset와 Investment는 반드시 하나의 Purpose를 가진다.

Goal은 선택적으로 연결된다.

---

# Resource Rules

Purpose는 Goal 없이 생성할 수 있다.

Purpose 이름은 중복될 수 없다.

Purpose는 Asset 또는 Investment가 연결되어 있으면 삭제할 수 없다.

---

# DTO

## PurposeDto

```json
{
  "id": "UUID",
  "name": "생활비",
  "description": "매월 사용하는 생활비",
  "goalId": "UUID | null",
  "createdAt": "2026-07-04T00:00:00Z",
  "updatedAt": "2026-07-04T00:00:00Z"
}
```

---

## CreatePurposeRequest

```json
{
  "name": "생활비",
  "description": "매월 사용하는 생활비"
}
```

---

## UpdatePurposeRequest

```json
{
  "name": "생활비",
  "description": "설명 수정"
}
```

---

## ConnectGoalRequest

```json
{
  "goalId": "UUID"
}
```

---

# Validation

## name

Required

1~100 Characters

Unique

---

## description

Optional

Max 1000 Characters

---

## goalId

Optional

Must Exist

---

# Endpoints

## Get Purpose List

GET

```
/api/v1/purposes
```

Query

```
?page=1

&pageSize=20

?sort=name

?order=asc

?q=생활
```

Response

```
200 OK
```

```json
[
  {
    "id": "...",
    "name": "생활비",
    "goalId": null
  }
]
```

---

## Get Purpose Detail

GET

```
/api/v1/purposes/{purposeId}
```

Response

```
200 OK
```

```json
{
  "id": "...",
  "name": "생활비",
  "description": "...",
  "goalId": null
}
```

---

## Create Purpose

POST

```
/api/v1/purposes
```

Request

```json
{
  "name": "생활비",
  "description": "매월 사용하는 생활비"
}
```

Response

```
201 Created
```

```json
{
  "id": "...",
  "name": "생활비"
}
```

---

## Update Purpose

PUT

```
/api/v1/purposes/{purposeId}
```

Request

```json
{
  "name": "생활비",
  "description": "수정"
}
```

Response

```
200 OK
```

---

## Delete Purpose

DELETE

```
/api/v1/purposes/{purposeId}
```

Response

```
204 No Content
```

---

## Connect Goal

POST

```
/api/v1/purposes/{purposeId}/goal
```

Request

```json
{
  "goalId": "UUID"
}
```

Response

```
200 OK
```

---

## Disconnect Goal

DELETE

```
/api/v1/purposes/{purposeId}/goal
```

Response

```
204 No Content
```

---

# Business Rules

Rule 1

Goal은 선택적으로 연결된다.

---

Rule 2

Goal을 변경하면 기존 Goal 연결은 자동 해제된다.

(V1 UI는 Purpose당 Goal 1개만 허용)

---

Rule 3

Asset와 Investment가 연결된 Purpose는 삭제할 수 없다.

---

Rule 4

Goal 삭제 시

Purpose.goalId는 NULL이 된다.

---

# Error Codes

PURPOSE_NOT_FOUND

```
404
```

---

GOAL_NOT_FOUND

```
404
```

---

DUPLICATED_NAME

```
409
```

---

RESOURCE_IN_USE

```
409
```

---

VALIDATION_FAILED

```
400
```

---

# Example Flow

## Create

```
POST /purposes

↓

201 Created
```

---

## Connect Goal

```
POST /purposes/{id}/goal

↓

200 OK
```

---

## Get Detail

```
GET /purposes/{id}
```

↓

```json
{
  "name": "내집마련",
  "goalId": "..."
}
```

---

# Cursor Generation Notes

Controller

PurposeController

---

Service

PurposeService

---

Repository

PurposeRepository

---

DTO

- PurposeDto
- CreatePurposeRequest
- UpdatePurposeRequest
- ConnectGoalRequest

---

Validation

- Name Required
- Name Unique
- Goal Exists

---

# Future Expansion

Version 2

- Purpose Archive
- Purpose Template

---

Version 2.2

- Purpose Merge
- Multi Goal Support

---

Version 3

- Shared Purpose
- Workspace Purpose

---

# Review Checklist

- [ ] Database와 일치하는가?
- [ ] ERD와 일치하는가?
- [ ] Goal이 Optional인가?
- [ ] Asset/Investment 삭제 정책과 일치하는가?
- [ ] DTO가 구현 가능한 수준인가?
- [ ] Cursor가 바로 Controller를 생성할 수 있는가?

---

# Notes

Purpose는 Atlas의 핵심 Domain이다.

모든 Asset와 Investment는 Purpose를 기준으로 연결된다.

Goal은 Purpose에 선택적으로 연결되며,

Purpose 자체는 Goal 없이도 독립적으로 존재할 수 있다.