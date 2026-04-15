# Suppliers

## Get All Suppliers

```shell
curl "~/api/suppliers" \
  -H "Authorization: Bearer <access_token>"
```

> The above command returns list of all the suppliers. Refer `Pagination and Sort` and `Schema` Section for exact
> response structure

This endpoint retrieves all suppliers. It supports pagination, sort, search and filter

### HTTP Request

`GET ~/api/suppliers`

## Get a Specific Supplier

```shell
curl "~/api/suppliers/1" \
  -H "Authorization: Bearer <access_token>"
```

> The above command returns JSON structured like this:

```json
{
  "id": 1,
  "name": "Monti",
  "desc": "Test Description"
}
```

This endpoint retrieves a specific supplier.

### HTTP Request

`GET ~/api/suppliers/{supplierId}`

### URL Parameters

| Parameter  | Description                        |
|------------|------------------------------------|
| supplierId | The Id of the supplier to retrieve |

## Create Supplier

```shell
curl "~/api/suppliers" \
  -X POST \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <access_token>" \
  -d '<JSON Payload>'
```

This endpoint creates a supplier.

### HTTP Request

`POST ~/api/suppliers`

### JSON Payload

<pre class="center-column">
{
    "id": 1000,
    "externalId": "S001", 
    "name": "Monti",
    "desc": "Test Description"
}
</pre>

> The above command returns JSON structured like this:

```json
{
  "id": 1000,
  "externalId": "S001",
  "name": "Monti",
  "desc": "Test Description"
}
```

## Create Supplier (Batch)

```shell
curl "~/api/suppliers/batch" \
  -X POST \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <access_token>" \
  -d '<JSON Payload>'
```

This endpoint creates a supplier.

### HTTP Request

`POST ~/api/suppliers/batch`

### JSON Payload

<pre class="center-column">
[
{
    "id": 1000,
    "externalId": "S001", 
    "name": "Monti",
    "desc": "Test Description"
},
{
    "id": 1001,
    "externalId": "S002", 
    "name": "Arvind",
    "desc": "Test Description"
}
]
</pre>

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1000,
    "externalId": "S001",
    "name": "Monti",
    "desc": "Test Description"
  },
  {
    "id": 1001,
    "externalId": "S002",
    "name": "Arvind",
    "desc": "Test Description"
  }
]
```

## Update a Specific Supplier

```shell
curl "~/api/suppliers/1" \
  -X PUT \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <access_token>" \
  -d '<JSON Payload>'
```

This endpoint updates an existing supplier.

### HTTP Request

`PUT ~/api/suppliers/{supplierId}`

| Parameter  | Description                      |
|------------|----------------------------------|
| supplierId | The Id of the supplier to update |

### JSON Payload

<pre class="center-column">
{
      "id": 1,
      "externalId": "S001", 
      "name": "Monti-Updated",
      "desc": "Test Description"
}
</pre>

> The above command returns JSON structured like this:

```json
{
  "id": 1,
  "externalId": "S001",
  "name": "Monti-Updated",
  "desc": "Test Description"
}
```

## Delete a Specific Supplier

```shell
curl "~/api/suppliers/1"
  -X DELETE
  -H "Authorization: Bearer <access_token>"
```

> The above command returns empty content with response status `204`

This endpoint deletes a specific supplier.

### HTTP Request

`DELETE ~/api/suppliers/{supplierId}`

### URL Parameters

| Parameter  | Description                      |
|------------|----------------------------------|
| supplierId | The Id of the supplier to delete |

## Schema - Supplier

```json
{
  "id": "long",
  "externalId": "string",
  "name": "string",
  "desc": "string"
}
```

Schema of Supplier entity

| Field      | Type   | Constraints                            | Description              |
|------------|--------|----------------------------------------|--------------------------|
| id         | Number | Either ID or External ID is required   | Internal ID              |
| externalId | Number | Either ID or External ID is required   | External ID              |
| name       | String | Required                               | Name of Supplier         |
| desc       | Text   |                                        | description for Supplier |
