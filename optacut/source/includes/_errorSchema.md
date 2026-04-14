# Error Schema Documentation

This document defines the standard error response structures used across different APIs.

---

## 🔹 1. Sales Order / Orders Error Schema

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

### Key Points

* Supports **multi-level nested validation**
* `errors` field allows recursive child errors
* Useful for **hierarchical payloads**

---

## 🔹 2. Factory Production Order Error Schema

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

### Key Points

* Same structure as Orders
* Maintained separately for **domain clarity**

---

## 🔹 3. Master Data Error Schema

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

### Key Points

* Flat structure (no nesting)
* Used for **simple CRUD validations**
* Lightweight and easy to parse

---

## 🔹 4. Batch API Error Schema

(Equipment, Machine, Machine Type)

Used for bulk operations where multiple records may fail.

### Structure

```json
[
  {
    "serialNo": 1,
    "field": "field1",
    "message": ["Test Message 1"],
    "rejectedValue": "test_val",
    "errors": null
  },
  {
    "serialNo": 2,
    "field": "field1",
    "message": ["Test Message 1"],
    "rejectedValue": "test_val",
    "errors": null
  }
]
```

### Key Points

* Each object represents **one record’s error**
* `serialNo` maps to input row/index
* Ideal for **bulk upload APIs**

---

## 🔹 Common Field Definitions

| Field         | Type        | Description                              |
|---------------|-------------|------------------------------------------|
| serialNo      | Integer     | Index of the record or nested element    |
| field         | String      | Field name where error occurred          |
| message       | String[]    | List of validation error messages        |
| currValue     | Any         | Current value in system (if applicable)  |
| rejectedValue | Any         | Invalid value provided in request        |
| errors        | List/Object | Nested child errors (recursive)          |

---

## 🔹 Design Notes

* Nested structure is **recursive** → supports unlimited depth
* `errors = null` → indicates no child errors
* `message` is always an array → supports multiple validations per field

---

## 🔹 Recommendation (Best Practice)

For consistency across APIs:

* Use **one unified schema**
* Keep `errors` optional for flat APIs
* Always return:

    * `field`
    * `message`
    * `rejectedValue`

---

## 🔹 Suggested Unified Schema (Optional Refactor)

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

---
