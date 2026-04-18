# Master, Order and FPO Error Schema

This document includes <b>Error Structures</b> and <b>Sample Responses</b> for <b>Master(Customer, Supplier, Product, etc.), Order and FPO API's.</b>

## Master Data Error Schema

(Customer, Season, Product, Supplier, etc.)

Used for simple entity validations.

> Structure

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

> Sample Response

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

## Sales Order / Orders Error Schema

Used for deeply nested validation errors (e.g., flowInfoList, partList, sizeBreakupList).

> Structure

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

> Sample Response

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

## Factory Production Order Error Schema

Used for factory production order-related APIs with similar nested structure.

> Structure

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

> Sample Response

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