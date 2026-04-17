# Error Schema Documentation

This document defines the standard error response structures used across different APIs.

---

# 🔹 1. Generic Error Response (Common for All APIs)

This is the base error response returned for all API failures.

### Structure

```json
{
  "status": 400,
  "code": "BAD_REQUEST",
  "message": "user friendly message",
  "devMessage": "developer message",
  "moreInfo": "more information",
  "body": "error body"
}
```

### Sample Response

```json
{
  "status": 400,
  "code": "BAD_REQUEST",
  "message": "id or externalId is required for updating Department",
  "devMessage": "",
  "moreInfo": "",
  "body": ""
}
```

### Fields

| Field    | Type     | Description                     |
|----------|----------|---------------------------------|
| status   | Integer  | HTTP status code                |
| code     | String   | Application-specific error code |
| message  | String   | Error description               |

---

# 🔹 2. Generic Batch API Error Response

Used for bulk APIs where multiple records can fail.

### Structure

```json
[
  {
    "serialNo": 1,
    "field": "field1",
    "message": ["Error message"],
    "rejectedValue": "invalid_value",
    "errors": null
  }
]
```

### Sample Response

```json
[
  {
    "serialNo": 1,
    "field": "name",
    "message": ["Season name is required"],
    "rejectedValue": null,
    "errors": null
  },
  {
    "serialNo": 2,
    "field": "name",
    "message": ["Season name is required"],
    "rejectedValue": -5,
    "errors": null
  }
]
```

### Key Points

* Each object represents one failed record
* `serialNo` maps to input index
* Used in bulk upload APIs

---

# 🔹 3. Master Data Error Schema

(Customer, Season, Product, Supplier, etc.)

Used for simple entity validations.

### Structure

```json
[
  {
    "serialNo": null,
    "field": "field1",
    "message": ["Error Message"],
    "rejectedValue": null,
    "errors": null
  }
]
```

### Sample Response

```json
[
  {
    "serialNo": null,
    "field": "name",
    "message": ["Customer name is required"],
    "rejectedValue": "",
    "errors": null
  }
]
```

### Key Points

* Flat structure (no nesting)
* Used for simple CRUD validations
* Lightweight and easy to parse

---

# 🔹 4. Sales Order / Orders Error Schema

Used for deeply nested validation errors (e.g., flowInfoList, partList, sizeBreakupList).

### Structure

```json
[
  {
    "serialNo": 1,
    "field": "field1",
    "message": ["Error1", "Error2"],
    "currValue": null,
    "rejectedValue": null,
    "errors": [
      {
        "serialNo": 1,
        "field": "field1",
        "message": ["Error1", "Error2"],
        "currValue": null,
        "rejectedValue": null,
        "errors": [
          {
            "serialNo": 1,
            "field": "field1",
            "message": ["Error1", "Error2"],
            "currValue": null,
            "rejectedValue": null
          }
        ]
      }
    ]
  }
]
```

### Sample Response

```json
[
  {
    "serialNo": 1,
    "field": "flowInfoList",
    "message": ["FlowInfo has errors."],
    "currValue": null,
    "rejectedValue": null,
    "errors": [
      {
        "serialNo": 1,
        "field": "partList",
        "message": ["Part list has errors"],
        "currValue": null,
        "rejectedValue": null,
        "errors": [
          {
            "serialNo": 1,
            "field": "bomCu",
            "message": ["BOM consumption must be greater than 0"],
            "currValue": null,
            "rejectedValue": -1
          }
        ]
      }
    ]
  }
]
```

### Key Points

* Supports multi-level nested validation
* `errors` field allows recursive child errors
* Useful for hierarchical payloads

---

# 🔹 5. Factory Production Order Error Schema

Used for factory production-related APIs with similar nested structure.

### Structure

```json
[
  {
    "serialNo": 1,
    "field": "field1",
    "message": ["Error1", "Error2"],
    "currValue": null,
    "rejectedValue": null,
    "errors": [
      {
        "serialNo": 1,
        "field": "field1",
        "message": ["Error1", "Error2"],
        "currValue": null,
        "rejectedValue": null,
        "errors": [
          {
            "serialNo": 1,
            "field": "field1",
            "message": ["Error1", "Error2"],
            "currValue": null,
            "rejectedValue": null
          }
        ]
      }
    ]
  }
]
```

### Sample Response

```json
[
  {
    "serialNo": 1,
    "field": "flowInfoList",
    "message": ["FlowInfo has errors."],
    "currValue": null,
    "rejectedValue": null,
    "errors": [
      {
        "serialNo": 1,
        "field": "productId",
        "message": ["Product Id is required"],
        "currValue": null,
        "rejectedValue": null
      },
      {
        "serialNo": 2,
        "field": "sizeBreakupList",
        "message": ["There are errors for size breakup."],
        "errors": [
          {
            "serialNo": 1,
            "field": "size",
            "message": ["Size is required"],
            "currValue": null,
            "rejectedValue": null
          }
        ]
      }
    ]
  }
]
```

### Key Points

* Same structure as Orders
* Maintained separately for domain clarity

---

# 🔹 Common Field Definitions

| Field         | Type        | Description                             |
|---------------|-------------|-----------------------------------------|
| serialNo      | Integer     | Index of the record or nested element   |
| field         | String      | Field name where error occurred         |
| message       | String[]    | List of validation error messages       |
| currValue     | Any         | Current value in system (if applicable) |
| rejectedValue | Any         | Invalid value provided in request       |
| errors        | List/Object | Nested child errors (recursive)         |

---

# 🔹 Design Notes

* Nested structure is recursive → supports unlimited depth
* `errors = null` → indicates no child errors
* `message` is always an array → supports multiple validations per field

---

# 🔹 Recommendation (Best Practice)

* Use one unified schema across APIs
* Keep `errors` optional for flat APIs
* Always return:

  * `field`
  * `message`
  * `rejectedValue`

---

# 🔹 Suggested Unified Schema (Optional Refactor)

```json
{
  "serialNo": 1,
  "field": "string",
  "message": ["string"],
  "rejectedValue": "any",
  "currValue": "any",
  "errors": []
}
```
