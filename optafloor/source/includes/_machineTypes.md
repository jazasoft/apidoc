# MachineTypes

## Get All MachineTypes

```shell
curl "~/v1/api/machineTypes" \
  -H "Authorization: Bearer <access_token>"
```

> The above command returns list of all the machineTypes. Refer `Pagination and Sort` and `Schema` Section for exact
> response structure

This endpoint retrieves all machineTypes. It supports pagination, sort, search and filter

### HTTP Request

`GET ~/api/machineTypes`

## Get a Specific MachineType

```shell
curl "~/v1/api/machineTypes/1" \
  -H "Authorization: Bearer <access_token>"
```

> The above command returns JSON structured like this:

```json
{
  "id": 1,
  "name": "SNLS",
  "desc": "Test Description"
}
```

This endpoint retrieves a specific machineType.

### HTTP Request

`GET ~/v1/api/machineTypes/{machineTypeId}`

### URL Parameters

| Parameter     | Description                           |
|---------------|---------------------------------------|
| machineTypeId | The Id of the machineType to retrieve |

## Create MachineType

```shell
curl "~/v1/api/machineTypes" \
  -X POST \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <access_token>" \
  -d '<JSON Payload>'
```

This endpoint creates a machineType.

### HTTP Request

`POST ~/v1/api/machineTypes`

### JSON Payload

<pre class="center-column">
{
    "id" : 1000,
    "name": "SNLS",
    "desc": "Test Description"
}
</pre>

> The above command returns JSON structured like this:

```json
{
  "id": 1000,
  "name": "SNLS",
  "desc": "Test Description"
}
```

## Update a Specific MachineType

```shell
curl "~/v1/api/machineTypes/1" \
  -X PUT \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <access_token>" \
  -d '<JSON Payload>'
```

This endpoint updates an existing machineType.

### HTTP Request

`PUT ~/v1/api/machineTypes/{machineTypeId}`

| Parameter     | Description                         |
|---------------|-------------------------------------|
| machineTypeId | The Id of the machineType to update |

### JSON Payload

<pre class="center-column">
{
      "id": 1,
      "name": "SNLS-Updated",
      "desc": "Test Description"
}
</pre>

> The above command returns JSON structured like this:

```json
{
  "id": 1,
  "name": "SNLS-Updated",
  "desc": "Test Description"
}
```

## Delete a Specific MachineType

```shell
curl "~/v1/api/machineTypes/1"
  -X DELETE
  -H "Authorization: Bearer <access_token>"
```

> The above command returns empty content with response status `204`

This endpoint deletes a specific machineType.

### HTTP Request

`DELETE ~/v1/api/machineTypes/{machineTypeId}`

### URL Parameters

| Parameter     | Description                         |
|---------------|-------------------------------------|
| machineTypeId | The Id of the machineType to delete |

## Schema - MachineType

```json
{
  "id": "long",
  "name": "string",
  "desc": "string"
}
```

Schema of machineType entity

| Field | Type   | Constraints | Description                 |
|-------|--------|-------------|-----------------------------|
| id    | Number | Primary Key | Internal ID                 |
| name  | String | Required    | Name of MachineType         |
| desc  | Text   |             | description for MachineType |
