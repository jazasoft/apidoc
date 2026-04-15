# Tables

## Get All Tables

```shell
curl "~/api/tables" \
  -H "Authorization: Bearer <access_token>"
```

> The above command returns list of all the tables. Refer `Pagination and Sort` and `Schema` Table for exact
> response structure

This endpoint retrieves all tables. It supports pagination, sort, search and filter

### HTTP Request

`GET ~/api/tables`

## Get a Specific Table

```shell
curl "~/api/tables/1" \
  -H "Authorization: Bearer <access_token>"
```

> The above command returns JSON structured like this:

```json
{
  "id": 1,
  "name": "Table 1",
  "desc": "Test Description"
}
```

This endpoint retrieves a specific table.

### HTTP Request

`GET ~/api/tables/{tableId}`

### URL Parameters

| Parameter  | Description                     |
|------------|---------------------------------|
| tableId    | The Id of the table to retrieve |

## Create Table

```shell
curl "~/api/tables" \
  -X POST \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <access_token>" \
  -d '<JSON Payload>'
```

This endpoint creates a table.

### HTTP Request

`POST ~/api/tables`

### JSON Payload

<pre class="center-column">
{
    "id": 1000,
    "externalId": "T001",
    "name": "Table 1",
    "desc": "Test Description"
}
</pre>

> The above command returns JSON structured like this:

```json
{
  "id": 1000,
  "externalId": "T001",
  "name": "Table 1",
  "desc": "Test Description"
}
```

## Create Table (Batch)

```shell
curl "~/api/tables/batch" \
  -X POST \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <access_token>" \
  -d '<JSON Payload>'
```

This endpoint creates a table.

### HTTP Request

`POST ~/api/tables/batch`

### JSON Payload

<pre class="center-column">
[
{
    "id": 1000,
    "externalId": "T001",
    "name": "Table 1",
    "desc": "Test Description"
},
{
    "id": 1001,
    "externalId": "T001",
    "name": "Table 2",
    "desc": "Test Description"
}
]
</pre>

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1000,
    "externalId": "T001",
    "name": "Table 1",
    "desc": "Test Description"
  },
  {
    "id": 1001,
    "externalId": "T001",
    "name": "Table 2",
    "desc": "Test Description"
  }
]
```

## Update a Specific Table

```shell
curl "~/api/tables/1" \
  -X PUT \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <access_token>" \
  -d '<JSON Payload>'
```

This endpoint updates an existing table.

### HTTP Request

`PUT ~/api/tables/{tableId}`

| Parameter | Description                   |
|-----------|-------------------------------|
| tableId   | The Id of the table to update |

### JSON Payload

<pre class="center-column">
{
      "id": 1,
      "externalId": "T001",
      "name": "Table 1-Updated",
      "desc": "Test Description"
}
</pre>

> The above command returns JSON structured like this:

```json
{
  "id": 1,
  "externalId": "T001",
  "name": "Table 1-Updated",
  "desc": "Test Description"
}
```

## Delete a Specific Table

```shell
curl "~/api/tables/1"
  -X DELETE
  -H "Authorization: Bearer <access_token>"
```

> The above command returns empty content with response status `204`

This endpoint deletes a specific table.

### HTTP Request

`DELETE ~/api/tables/{tableId}`

### URL Parameters

| Parameter | Description                   |
|-----------|-------------------------------|
| tableId   | The Id of the table to delete |

## Schema - Table

```json
{
  "id": "long",
  "externalId": "string",
  "name": "string",
  "desc": "string"
}
```

Schema of table entity

| Field      | Type   | Constraints                            | Description           |
|------------|--------|----------------------------------------|-----------------------|
| id         | Number | Either ID or External ID is required   | Internal ID           |
| externalId | Number | Either ID or External ID is required   | External ID           |
| name       | String | Required                               | Name of Table         |
| desc       | Text   |                                        | description for Table |
