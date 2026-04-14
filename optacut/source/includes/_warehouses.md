# Warehouses

## Get All Warehouses

```shell
curl "~/api/warehouses" \
  -H "Authorization: Bearer <access_token>"
```

> The above command returns list of all the warehouses. Refer `Pagination and Sort` and `Schema` Section for exact
> response structure

This endpoint retrieves all warehouses. It supports pagination, sort, search and filter

### HTTP Request

`GET ~/api/warehouses`

## Get a Specific Warehouse

```shell
curl "~/api/warehouses/1" \
  -H "Authorization: Bearer <access_token>"
```

> The above command returns JSON structured like this:

```json
{
  "id": 1,
  "name": "Warehouse 1",
  "desc": "Test Description"
}
```

This endpoint retrieves a specific warehouse.

### HTTP Request

`GET ~/api/warehouses/{warehouseId}`

### URL Parameters

| Parameter   | Description                         |
|-------------|-------------------------------------|
| warehouseId | The Id of the warehouse to retrieve |

## Create Warehouse

```shell
curl "~/api/warehouses" \
  -X POST \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <access_token>" \
  -d '<JSON Payload>'
```

This endpoint creates a warehouse.

### HTTP Request

`POST ~/api/warehouses`

### JSON Payload

<pre class="center-column">
{
    "id": 1000,
    "externalId": "W001",
    "name": "Warehouse 1",
    "desc": "Test Description"
}
</pre>

> The above command returns JSON structured like this:

```json
{
  "id": 1000,
  "externalId": "W001",
  "name": "Warehouse 1",
  "desc": "Test Description"
}
```

## Create Warehouse (Batch)

```shell
curl "~/api/warehouses/batch" \
  -X POST \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <access_token>" \
  -d '<JSON Payload>'
```

This endpoint creates a warehouse.

### HTTP Request

`POST ~/api/warehouses/batch`

### JSON Payload

<pre class="center-column">
[
{
    "id": 1000,
    "externalId": "W001",
    "name": "Warehouse 1",
    "desc": "Test Description"
},
{
    "id": 1001,
    "externalId": "W002",
    "name": "Warehouse 2",
    "desc": "Test Description"
}
]
</pre>

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1000,
    "externalId": "W001",
    "name": "Warehouse 1",
    "desc": "Test Description"
  },
  {
    "id": 1001,
    "externalId": "W002",
    "name": "Warehouse 2",
    "desc": "Test Description"
  }
]
```


## Update a Specific Warehouse

```shell
curl "~/api/warehouses/1" \
  -X PUT \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <access_token>" \
  -d '<JSON Payload>'
```

This endpoint updates an existing warehouse.

### HTTP Request

`PUT ~/api/warehouses/{warehouseId}`

| Parameter   | Description                       |
|-------------|-----------------------------------|
| warehouseId | The Id of the warehouse to update |

### JSON Payload

<pre class="center-column">
{
      "id": 1,
      "externalId": "W001",
      "name": "Warehouse 1-Updated",
      "desc": "Test Description"
}
</pre>

> The above command returns JSON structured like this:

```json
{
  "id": 1,
  "externalId": "W001",
  "name": "Warehouse 1-Updated",
  "desc": "Test Description"
}
```

## Delete a Specific Warehouse

```shell
curl "~/api/warehouses/1"
  -X DELETE
  -H "Authorization: Bearer <access_token>"
```

> The above command returns empty content with response status `204`

This endpoint deletes a specific warehouse.

### HTTP Request

`DELETE ~/api/warehouses/{warehouseId}`

### URL Parameters

| Parameter   | Description                       |
|-------------|-----------------------------------|
| warehouseId | The Id of the warehouse to delete |

## Schema - Warehouse

```json
{
  "id": "long",
  "externalId": "string",
  "name": "string",
  "desc": "string"
}
```

Schema of warehouse entity

| Field      | Type   | Constraints                            | Description               |
|------------|--------|----------------------------------------|---------------------------|
| id         | Number | Either ID or External ID is required   | Internal ID               |
| externalId | Number | Either ID or External ID is required   | External ID               |
| name       | String | Required                               | Name of Warehouse         |
| desc       | Text   |                                        | description for Warehouse |
