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
  "machineId": "string",
  "machineTypeId": "long",
  "brand": "string",
  "purchaseDate": "date",
  "price": "double",
  "lineId": "long",
  "currentLineId": "long",
  "desc": "string"
}
```

Schema of Machine entity

| Field            | Type   | Constraints | Description              |
|------------------|--------|-------------|--------------------------|
| id               | Number | Primary Key | Internal ID              |
| externalId       | String | Unique Key  | External ID              |
| machineId        | String | Required    | Machine Id/Asset Number  |
| machineTypeId    | Number | Required    | Machine Type Internal Id |
| extMachineTypeId | String |             | Machine Type External Id |
| brand            | String |             | Brand of Machine         |
| purchaseDate     | date   |             | Purchase date of Machine |
| price            | String |             | Price of Machine         |
| lineId           | String |             | Line of Machine          |
| currentLineId    | String |             | Current Line of Machine  |
| desc             | Text   |             | description for Machine  |
