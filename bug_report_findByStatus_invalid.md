
# 🐞 Bug Report

- **Bug ID:** BUG_001  
- **Module:** GET `/pet/findByStatus`  
- **Title:** API returns 200 OK for invalid `status` values and empty status query  
- **Severity:** Medium  
- **Priority:** Medium  
- **Reported by:** [your name or nickname]  
- **Environment:**  
  - API: Swagger Petstore  
  - Tool: Postman  
  - Base URL: `{{base_URL}}`  
  - Date: 2025-04-08

---

## 🔍 Description

The API endpoint `/pet/findByStatus` is supposed to return `400 Bad Request` when an invalid or missing `status` query parameter is provided. However, when tested with invalid values (`true`, `123`) and with no parameter at all, the response is `200 OK`, with an empty array in the body.

---

## 🔁 Steps to Reproduce

1. Send a GET request to `/pet/findByStatus?status=true`
2. Send a GET request to `/pet/findByStatus?status=123`
3. Send a GET request to `/pet/findByStatus` (no query param)

---

## ✅ Expected Result

- Response status: **400 Bad Request**
- Error message indicating invalid or missing `status` parameter

---

## ❌ Actual Result

- Response status: **200 OK**
- Response body: `[]` (empty array)

---

## 📷 Screenshots

- `screenshots/invalid_status_true.png`
- `screenshots/invalid_status_123.png`
- `screenshots/invalid_status_empty.png`

---

## 📌 Notes

- The [Swagger documentation](https://petstore.swagger.io/#/pet/findPetsByStatus) explicitly states that only `available`, `pending`, and `sold` are accepted.
- Any deviation should result in a `400 Bad Request`.
