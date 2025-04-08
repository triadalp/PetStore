
# 🧪 API Test Cases – Swagger Petstore

## Table of Contents
- [USER](#user)
- [PET](#pet)
- [STORE](#store)

---



# ✅ API Test Case 

## 🐾 PET 

**Description:** Get a list of pets filtered by status (`available`, `pending`, `sold`)  
**Method:** GET  
**URL:** `{{base_URL}}/pet/findByStatus`  
**Request Title:** Find pets by status  
**ID:** TC_001

---

## 🔧 Request Parameters

| Type       | Key         | Value            | Description                     |
|------------|-------------|------------------|---------------------------------|
| Query      | status      | available        | Pet is available for adoption   |
| Query      | status      | pending          | Pending approval or processing  |
| Query      | status      | sold             | Already sold                    |

---

## ✅ Expected Result

- **Status code:** `200`
- **Content-Type:** `application/json`
- **Description:** Array of pet objects with the requested status
- **Sample object:**
```json
[
  {
    "id": 0,
    "category": {
      "id": 0,
      "name": "string"
    },
    "name": "doggie",
    "photoUrls": [
      "string"
    ],
    "tags": [
      {
        "id": 0,
        "name": "string"
      }
    ],
    "status": "available"
  }
]
```

---

## 📥 Actual Result

### 🔹 Subtest 1 — `status=available`
- **Status code:** 200  
- **Response contains:** array of pet objects with `status = "available"`  
- **Screenshot:** `screenshots/TC_001_200_available_test.png`  
- **Status:** ✅ Passed

---

### 🔹 Subtest 2 — `status=pending`
- **Status code:** 200  
- **Response contains:** array of pet objects with `status = "pending"`  
- **Screenshot:** `screenshots/TC_001_200_pending_test.png`  
- **Status:** ✅ Passed

---

### 🔹 Subtest 3 — `status=sold`
- **Status code:** 200  
- **Response contains:** array of pet objects with `status = "sold"`  
- **Screenshot:** `screenshots/TC_001_200_sold_test.png`  
- **Status:** ✅ Passed

---

## 🟢 Test Status

- ✅ Passed: Yes  
- 🧩 Coverage: All 3 status values tested (available, pending, sold)

---
❗ Negative Testing
🔻 Subtest 4 — status=true (Invalid Value)
Expected status: 400 Bad Request

Actual status: 200 OK ❌

Body: []

Screenshot: screenshots/invalid_status_true.png

Status: ❌ Failed

🔻 Subtest 5 — status=123 (Invalid Value - number)
Expected status: 400 Bad Request

Actual status: 200 OK ❌

Body: []

Screenshot: screenshots/invalid_status_123.png

Status: ❌ Failed

🔻 Subtest 6 — no status parameter
Expected status: 400 Bad Request

Actual status: 200 OK ❌

Body: []

Screenshot: screenshots/invalid_status_empty.png

Status: ❌ Failed

🟢 Final Test Status Summary
✅ Passed: 3/6

❌ Failed: 3/6

🧩 Coverage: Checked all valid values and edge cases

📌 Bug: API returns 200 OK even for invalid status values and empty parameter — does not match documentation
## 📝 Comments

Screenshots saved in the `/screenshots/` folder.


✅ API Test Case

## 🐾 PET – Add a new pet to the store

**Description:** Add a new pet using the POST method
**Method:** POST  
**URL:** `{{base_URL}}/petRequest`
**Request Title:** Add pet to store  
**ID:** TC_002

🔧 Request Body

Content-Type: application/json
Required: Yes ( * ) means required in Swagger

✍️ Example Request Body
{
  "id": 0,
  "category": {
    "id": 0,
    "name": "string"
  },
  "name": "doggie",
  "photoUrls": [
    "string"
  ],
  "tags": [
    {
      "id": 0,
      "name": "string"
    }
  ],
  "status": "available"
}

✅ Expected Result

Status code: 200 (Success)

Description: Pet is created and returned in the response

🗕 Actual Result

🔹 Subtest 1 — Valid request body

Status code: 200 ✅

Response: Pet created with auto-generated ID (e.g., 9223372036854776000)

Screenshot: screenshots/TC_002_200_create_pet.png

Status: ✅ Passed
