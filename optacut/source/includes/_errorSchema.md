# Error Schema

This document defines the standardized error response formats used across all APIs to ensure consistency, clarity, and ease of debugging.

We provide two types of error responses based on the nature of the API operation:

 1. <b>Generic Error Response</b> - Used for standard API failures where a single request results in a single error.
 2. <b>Batch API Error Response</b> - Used for bulk operations where multiple records are processed, and each record may have independent validation errors.

## Generic Error Response (Common for All APIs)

This is the base error response returned for all API failures.

> Structure

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

> Sample Response

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

| Field      | Type     | Description                          |
|------------|----------|--------------------------------------|
| status     | Integer  | HTTP status code                     |
| code       | String   | Application-specific error code      |
| message    | String   | User Friendly Error description      |
| devMessage | String   | Developer Friendly Error description |
| moreInfo   | String   | More Information regarding error     |
| body       | String   | Error Body                           |

## Generic Batch API Error Response

Used for bulk APIs where multiple records can fail.

> Structure

```json
[
  {
    "serialNo": 1,
    "field": "field1",
    "message": ["Error message"],
    "currValue": "curr_value",
    "rejectedValue": "invalid_value",
    "errors": null
  }
]
```

> Sample Response

```json
[
  {
    "serialNo": 1,
    "field": "name",
    "message": ["Season name is required"],
    "currValue": null,
    "rejectedValue": null,
    "errors": null
  },
  {
    "serialNo": 2,
    "field": "name",
    "message": ["Season name is required"],
    "currValue": null,
    "rejectedValue": null,
    "errors": null
  }
]
```

### Key Points

* Each object represents one failed record
* `serialNo` maps to input index
* Used in bulk upload APIs

## Common Field Definitions

| Field         | Type        | Description                             |
|---------------|-------------|-----------------------------------------|
| serialNo      | Integer     | Index of the record or nested element   |
| field         | String      | Field name where error occurred         |
| message       | String[]    | List of validation error messages       |
| currValue     | Any         | Current value in system (if applicable) |
| rejectedValue | Any         | Invalid value provided in request       |
| errors        | List/Object | Nested child errors (recursive)         |

### Key Points

* Nested structure is recursive → supports unlimited depth
* `errors = null` → indicates no child errors
* `message` is always an array → supports multiple validations per field
