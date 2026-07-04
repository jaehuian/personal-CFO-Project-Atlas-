# Asset API

Version: 1.0

Status: Architecture Freeze

Owner: Project Atlas

Resource: Asset

Base URL

/api/v1/assets

Related Documents

- README.md
- ../../01_DomainModel.md
- ../../02_Database.md
- ../../03_ERD.md
- ../../../02_Design/06_Asset.md

---

# Purpose

Asset Resource를 관리한다.

Asset는 사용자의 현금성 자산을 관리한다.

모든 Asset는 반드시 하나의 Purpose와 하나의 Account에 연결된다.

---

# Resource Rules

- 모든 Asset는 반드시 Purpose를 가진다.
- 모든 Asset는 반드시 Account를 가진다.
- Asset는 Goal을 직접 참조하지 않는다.
- Asset는 Investment와 독립적으로 관리된다.

---

# DTO

## AssetDto

```json
{
  "id": "UUID",
  "name": "생활비 통장",
  "assetType": "CHECKING",
  "marketValue": 3000000,
  "purposeId": "UUID",
  "accountId": "UUID",
  "memo": "월급 관리",
  "createdAt": "2026-07-04T00:00:00Z",
  "updatedAt": "2026-07-04T00:00:00Z"
}
```

---

## CreateAssetRequest

```json
{
  "name": "생활비 통장",
  "assetType": "CHECKING",
  "marketValue": 3000000,
  "purposeId": "UUID",
  "accountId": "UUID",
  "memo": "월급 관리"
}
```

---

## UpdateAssetRequest

```json
{
  "name": "생활비 통장",
  "assetType": "CHECKING",
  "marketValue": 3500000,
  "purposeId": "UUID",
  "accountId": "UUID",
  "memo": "수정"
}
```

---

# Validation

## name

- Required
- 1~100 Characters

---

## assetType

- Required
- AssetType Enum

---

## marketValue

- Required
- Decimal
- Minimum 0

---

## purposeId

- Required
- Must Exist

---

## accountId

- Required
- Must Exist

---

## memo

- Optional
- Max 1000 Characters

---

# Endpoints

## Get Asset List

GET

```
/api/v1/assets
```

Query

```
?page=1

&pageSize=20

?sort=name

?order=asc

?purposeId=UUID

?accountId=UUID

?assetType=CHECKING

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
    "name": "생활비 통장",
    "marketValue": 3000000
  }
]
```

---

## Get Asset Detail

GET

```
/api/v1/assets/{assetId}
```

Response

```
200 OK
```

```json
{
  "id": "...",
  "name": "생활비 통장",
  "assetType": "CHECKING",
  "marketValue": 3000000,
  "purposeId": "...",
  "accountId": "..."
}
```

---

## Create Asset

POST

```
/api/v1/assets
```

Request

```json
{
  "name": "생활비 통장",
  "assetType": "CHECKING",
  "marketValue": 3000000,
  "purposeId": "...",
  "accountId": "...",
  "memo": "월급 관리"
}
```

Response

```
201 Created
```

```json
{
  "id": "...",
  "name": "생활비 통장"
}
```

---

## Update Asset

PUT

```
/api/v1/assets/{assetId}
```

Request

```json
{
  "name": "생활비 통장",
  "assetType": "CHECKING",
  "marketValue": 3500000,
  "purposeId": "...",
  "accountId": "...",
  "memo": "수정"
}
```

Response

```
200 OK
```

---

## Delete Asset

DELETE

```
/api/v1/assets/{assetId}
```

Response

```
204 No Content
```

---

# Business Rules

Rule 1

모든 Asset는 반드시 하나의 Purpose를 가진다.

---

Rule 2

모든 Asset는 반드시 하나의 Account를 가진다.

---

Rule 3

Asset는 Goal을 직접 참조하지 않는다.

---

Rule 4

Purpose 변경은 Asset의 소속만 변경한다.

---

Rule 5

Asset 삭제는 다른 Resource에 영향을 주지 않는다.

---

# Error Codes

ASSET_NOT_FOUND

```
404
```

---

PURPOSE_NOT_FOUND

```
404
```

---

ACCOUNT_NOT_FOUND

```
404
```

---

VALIDATION_FAILED

```
400
```

---

INVALID_ASSET_TYPE

```
400
```

---

# Example Flow

## Create Asset

```
POST /assets

↓

201 Created
```

---

## Update Asset

```
PUT /assets/{id}

↓

200 OK
```

---

## Get Detail

```
GET /assets/{id}
```

↓

```json
{
  "name": "생활비 통장",
  "purposeId": "...",
  "accountId": "...",
  "marketValue": 3000000
}
```

---

# Cursor Generation Notes

## Controller

AssetController

---

## Service

AssetService

---

## Repository

AssetRepository

---

## DTO

- AssetDto
- CreateAssetRequest
- UpdateAssetRequest

---

## Validation

- Name Required
- Purpose Exists
- Account Exists
- MarketValue >= 0

---

# Future Expansion

## Version 2

- Open Banking Sync
- Asset History
- Asset Snapshot

---

## Version 2.2

- Asset Archive
- Asset Import

---

## Version 3

- Real-time Balance
- Institution API Sync

---

# Review Checklist

- [ ] Purpose를 반드시 참조하는가?
- [ ] Account를 반드시 참조하는가?
- [ ] Goal을 직접 참조하지 않는가?
- [ ] Database와 일치하는가?
- [ ] ERD와 일치하는가?
- [ ] Cursor가 바로 Controller를 생성할 수 있는가?

---

# Notes

Asset는 Atlas의 현금성 자산 Resource이다.

Asset는 Purpose를 기준으로 분류되고,

Account를 통해 실제 보관 위치를 관리한다.

Goal은 Asset가 아닌 Purpose를 통해 간접적으로 연결된다.