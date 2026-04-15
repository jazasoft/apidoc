# Machines

## Get All Machines

```shell
curl "~/v1/api/machines" \
  -H "Authorization: Bearer <access_token>"
```

> The above command returns list of all the Machines. Refer `Pagination and Sort` and `Schema` Section for exact
> response structure

This endpoint retrieves all Machines. It supports pagination, sort, search and filter

### HTTP Request

`GET ~/api/machines`

## Get a Specific Machine

```shell
curl "~/v1/api/machines/1" \
  -H "Authorization: Bearer <access_token>"
```

> The above command returns JSON structured like this:

```json
{
  "id": 1000,
  "machineId": "JUKI-100",
  "machineTypeId": 1,
  "brand": "Juki",
  "purchaseDate": "2025-01-01",
  "price": 1230.23,
  "desc": "Test Description"
}
```

This endpoint retrieves a specific Machine.

### HTTP Request

`GET ~/v1/api/machines/{machineId}`

### URL Parameters

| Parameter | Description                       |
|-----------|-----------------------------------|
| machineId | The Id of the Machine to retrieve |

## Create Machine

```shell
curl "~/v1/api/machines" \
  -X POST \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <access_token>" \
  -d '<JSON Payload>'
```

This endpoint creates a Machine.

### HTTP Request

`POST ~/v1/api/machines`

### JSON Payload

<pre class="center-column">
{
  "id": 1000,
  "machineId": "JUKI-100",
  "machineTypeId": 1,
  "extMachineTypeId": "E100",
  "brand": "Juki",
  "purchaseDate": "2025-01-01",
  "price": 1230.23,
  "desc": "Test Description"
}
</pre>

> The above command returns JSON structured like this:

```json
{
  "id": 1000,
  "machineId": "JUKI-100",
  "machineTypeId": 1,
  "extMachineTypeId": "E100",
  "brand": "Juki",
  "purchaseDate": "2025-01-01",
  "price": 1230.23,
  "desc": "Test Description"
}
```

## Create Machine (Batch)

```shell
curl "~/v1/api/machines/batch" \
  -X POST \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <access_token>" \
  -d '<JSON Payload>'
```

This endpoint creates a buyers.

### HTTP Request

`POST ~/api/machines/batch`

### JSON Payload

<pre class="center-column">
[
    {
        "externalId": "E10010",
        "machineId": "JUKI-10010",
        "extMachineTypeId": "E100",
        "brand": "Juki",
        "purchaseDate": "2025-01-01",
        "price": 1230.23,
        "desc": "Test Description"
    },
    {
        "externalId": "E10011",
        "machineId": "JUKI-10011",
        "extMachineTypeId": "E100",
        "brand": "Juki",
        "purchaseDate": "2025-01-01",
        "price": 1230.23,
        "desc": "Test Description"
    },
    {
        "externalId": "E10012",
        "machineId": "JUKI-10012",
        "extMachineTypeId": "E100",
        "brand": "Juki",
        "purchaseDate": "2025-01-01",
        "price": 1230.23,
        "desc": "Test Description"
    }
]

</pre>

> The above command returns JSON structured like this:

```json
[
  {
    "externalId": "E10010",
    "id": null,
    "machineId": "JUKI-10010",
    "machineType": null,
    "line": null,
    "currentLine": null,
    "brand": "Juki",
    "purchaseDate": 1735689600000,
    "price": 1230.23,
    "desc": "Test Description",
    "machineTypeId": 1,
    "extMachineTypeId": "E100",
    "lineId": null,
    "departmentName": null,
    "currentLineId": null,
    "currentLineName": null,
    "lineName": null,
    "machineTypeName": null,
    "enabled": null,
    "createdById": null,
    "lastModifiedById": null
  },
  {
    "externalId": "E10011",
    "id": null,
    "machineId": "JUKI-10011",
    "machineType": null,
    "line": null,
    "currentLine": null,
    "brand": "Juki",
    "purchaseDate": 1735689600000,
    "price": 1230.23,
    "desc": "Test Description",
    "machineTypeId": 1,
    "extMachineTypeId": "E100",
    "lineId": null,
    "departmentName": null,
    "currentLineId": null,
    "currentLineName": null,
    "lineName": null,
    "machineTypeName": null,
    "enabled": null,
    "createdById": null,
    "lastModifiedById": null
  },
  {
    "externalId": "E10012",
    "id": 1010,
    "machineId": "JUKI-10012",
    "machineType": {
      "createdAt": 1755866088531,
      "modifiedAt": 1756106339035,
      "createdBy": "Ankita Dasgupta",
      "lastModifiedBy": "Avani Dipakkumar Nathani",
      "externalIds": null,
      "version": null,
      "externalId": null,
      "id": 1,
      "name": "Richpeace",
      "desc": null,
      "enabled": true,
      "createdById": 888,
      "lastModifiedById": 886,
      "isReferenced": false
    },
    "line": null,
    "currentLine": null,
    "brand": "Juki",
    "purchaseDate": 1735689600000,
    "price": 1230.23,
    "desc": "Test Description",
    "machineTypeId": 1,
    "extMachineTypeId": "E100",
    "lineId": null,
    "departmentName": null,
    "currentLineId": null,
    "currentLineName": null,
    "lineName": null,
    "machineTypeName": null,
    "enabled": true,
    "createdById": null,
    "lastModifiedById": null
  }
]

```

## Update a Specific Machine

```shell
curl "~/v1/api/machines/1" \
  -X PUT \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <access_token>" \
  -d '<JSON Payload>'
```

This endpoint updates an existing Machine.

### HTTP Request

`PUT ~/v1/api/machines/{machineId}`

| Parameter | Description                     |
|-----------|---------------------------------|
| machineId | The Id of the Machine to update |

### JSON Payload

<pre class="center-column">
  {
    "id": 1000,
    "machineId": "JUKI-100-Updated",
    "machineTypeId": 1,
    "extMachineTypeId": "E100",
    "brand": "Juki",
    "purchaseDate": "2025-01-01",
    "price": 1230.23,
    "desc": "Test Description"
  }
</pre>

> The above command returns JSON structured like this:

```json
  {
  "id": 1000,
  "machineId": "JUKI-100-Updated",
  "machineTypeId": 1,
  "extMachineTypeId": "E100",
  "brand": "Juki",
  "purchaseDate": "2025-01-01",
  "price": 1230.23,
  "desc": "Test Description"
}
```

## Update a Specific Machine (Using External Id)

```shell
curl "~/v1/api/machines?externalId=E200" \
  -X PUT \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <access_token>" \
  -d '<JSON Payload>'
```

This endpoint updates an existing Machine.

### HTTP Request

`PUT ~/v1/api/machines?externalId=<External ID>`

| Parameter | Description                              |
|-----------|------------------------------------------|
| externalId | The External Id of the Machine to update |

### JSON Payload

<pre class="center-column">
  { 
    "externalId": "E200"
    "machineId": "JUKI-100-Updated",
    "machineTypeId": 1,
    "extMachineTypeId": "E100",
    "brand": "Juki",
    "purchaseDate": "2025-01-01",
    "price": 1230.23,
    "desc": "Test Description"
  }
</pre>

> The above command returns JSON structured like this:

```json
  {
  "id": 1000,
  "externalId": "E200",
  "machineId": "JUKI-100-Updated",
  "machineTypeId": 1,
  "extMachineTypeId": "E100",
  "brand": "Juki",
  "purchaseDate": "2025-01-01",
  "price": 1230.23,
  "desc": "Test Description"
}
```

## Delete a Specific Machine

```shell
curl "~/v1/api/machines/1"
  -X DELETE
  -H "Authorization: Bearer <access_token>"
```

> The above command returns empty content with response status `204`

This endpoint deletes a specific Machine.

### HTTP Request

`DELETE ~/v1/api/machines/{machineId}`

### URL Parameters

| Parameter | Description                     |
|-----------|---------------------------------|
| machineId | The Id of the Machine to delete |

## Schema - Machine

```json
  {
  "id": "long",
  "externalId": "string",
  "machineId": "string",
  "externalMachineTypeId": "string",
  "machineTypeId": "long",
  "brand": "string",
  "purchaseDate": "date",
  "price": "double",
  "lineId": "long",
  "currentLineId": "long",
  "desc": "string"
}
```

## Schema - Error (Generic Error)

```json
{
  "status": 409,
  "code": 40900,
  "message": "Operation cannot be performed. Integrity Constraint violated.",
  "devMessage": "ERROR: null value in column \"machine_type_id\" of relation \"machine\" violates not-null constraint\n  Detail: Failing row contains (1011, 2026-04-14 16:38:24.526, 2026-04-14 16:38:24.526, SAP, SAP, JUKI-10088, null, Juki, 2025-01-01 00:00:00, 1230.23, null, Test Description, null, null, null, t, null, [{\"appId\":\"SAP\",\"externalId\":\"E100188\"}], null, null).",
  "moreInfo": ""
}
```

## Schema - Error (Field Error)

```json
[
  {
    "serialNo": 1,
    "field": "machineTypeId",
    "message": [
      "Required."
    ],
    "rejectedValue": null,
    "errors": null
  },
  {
    "serialNo": 2,
    "field": "machineId",
    "message": [
      "Required."
    ],
    "rejectedValue": null,
    "errors": null
  }
]
```


Schema of Machine entity

| Field            | Type   | Constraints | Description                                |
|------------------|--------|-------------|--------------------------------------------|
| id               | Number | Primary Key | Internal ID                                |
| externalId       | String | Unique Key  | External ID (For Integartion)              |
| machineId        | String | Required    | Machine Id/Asset Number                    |
| machineTypeId    | Number | Required    | Machine Type Internal Id                   |
| extMachineTypeId | String |             | Machine Type External Id (For Integration) |
| brand            | String |             | Brand of Machine                           |
| purchaseDate     | date   |             | Purchase date of Machine                   |
| price            | String |             | Price of Machine                           |
| lineId           | String |             | Line of Machine                            |
| currentLineId    | String |             | Current Line of Machine                    |
| desc             | Text   |             | description for Machine                    |
