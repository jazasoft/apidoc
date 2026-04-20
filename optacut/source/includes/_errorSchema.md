# Error Schema

This document defines the standardized error response formats used across all APIs to ensure consistency, clarity, and ease of debugging.

We provide two types of error responses based on the nature of the API operation:

 1. <b>Generic Error Response</b> - Used for standard API failures.
 2. <b>Field Error Response</b> - Used to indicate specific errors at field level. This error reponse can be nested and hierarchy is as per payload hierarchy.  

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

## Field Error Response

Field level error response

> Structure

```json
[
  {
    "serialNo": 1,
    "field": "field1",
    "message": ["Error message"],
    "currValue": "curr_value",
    "rejectedValue": "invalid_value",
    "errors": [
      {
        "serialNo": 1,
        "field": "nestedField",
        "message": ["Error message"],
        "currValue": "curr_value",
        "rejectedValue": "invalid_value"
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
    "field": "poRef",
    "message": ["PO Reference is required"],
    "currValue": null,
    "rejectedValue": null,
    "errors": null
  },
  {
    "serialNo": 2,
    "field": "flowInfoList",
    "message": ["There are errors in FlowInfo"],
    "currValue": null,
    "rejectedValue": null,
    "errors": [
      {
        "serialNo": 1,
        "field": "style",
        "message": ["Style is required"],
        "currValue": null,
        "rejectedValue": null,
        "errors": null
      },
      {
        "serialNo": 2,
        "field": "style",
        "message": ["Style is required"],
        "currValue": null,
        "rejectedValue": null,
        "errors": null
      }
    ]
  }
]
```

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

* Nested structure is recursive → supports unlimited depth. Depth is upto depth of JSON Payload
* `errors = null` → indicates no child errors
* `message` is always an array → supports multiple validations per field
