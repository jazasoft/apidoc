# Departments

## Get All Departments

```shell
curl "~/api/departments" \
  -H "Authorization: Bearer <access_token>"
```

> The above command returns list of all the departments. Refer `Pagination and Sort` and `Schema` Section for exact
> response structure

This endpoint retrieves all departments. It supports pagination, sort, search and filter

### HTTP Request

`GET ~/api/departments`

## Get a Specific Department

```shell
curl "~/api/departments/1" \
  -H "Authorization: Bearer <access_token>"
```

> The above command returns JSON structured like this:

```json
{
  "id": 1,
  "name": "Sewing",
  "desc": "Test Description"
}
```

This endpoint retrieves a specific department.

### HTTP Request

`GET ~/api/departments/{departmentId}`

### URL Parameters

| Parameter    | Description                          |
|--------------|--------------------------------------|
| departmentId | The Id of the department to retrieve |

## Create Department

```shell
curl "~/api/departments" \
  -X POST \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <access_token>" \
  -d '<JSON Payload>'
```

This endpoint creates a department.

### HTTP Request

`POST ~/api/departments`

### JSON Payload

<pre class="center-column">
{
    "id": 1000,
    "externalId": "D001",
    "name": "Sewing",
    "desc": "Test Description"
}
</pre>

> The above command returns JSON structured like this:

```json
{
  "id": 1000,
  "externalId": "D001",
  "name": "Sewing",
  "desc": "Test Description"
}
```

## Create Department(Batch)

```shell
curl "~/api/departments/batch" \
  -X POST \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <access_token>" \
  -d '<JSON Payload>'
```

This endpoint creates a department.

### HTTP Request

`POST ~/api/departments/batch`

### JSON Payload

<pre class="center-column">
[
{
    "id": 1000,
    "externalId": "D001",
    "name": "Sewing",
    "desc": "Test Description"
},
{
    "id": 1001,
    "externalId": "D002",
    "name": "Finishing",
    "desc": "Test Description"
}
]
</pre>

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1000,
    "externalId": "D001",
    "name": "Sewing",
    "desc": "Test Description"
  },
  {
    "id": 1001,
    "externalId": "D002",
    "name": "Finishing",
    "desc": "Test Description"
  }
]
```

## Update a Specific Department

```shell
curl "~/api/departments/1" \
  -X PUT \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <access_token>" \
  -d '<JSON Payload>'
```

This endpoint updates an existing department.

### HTTP Request

`PUT ~/api/departments/{departmentId}`

| Parameter    | Description                        |
|--------------|------------------------------------|
| departmentId | The Id of the department to update |

### JSON Payload

<pre class="center-column">
{
      "id": 1,
      "externalId": "D001",
      "name": "Sewing-Updated",
      "desc": "Test Description"
}
</pre>

> The above command returns JSON structured like this:

```json
{
  "id": 1,
  "externalId": "D001",
  "name": "Sewing-Updated",
  "desc": "Test Description"
}
```

## Delete a Specific Department

```shell
curl "~/api/departments/1"
  -X DELETE
  -H "Authorization: Bearer <access_token>"
```

> The above command returns empty content with response status `204`

This endpoint deletes a specific department.

### HTTP Request

`DELETE ~/api/departments/{departmentId}`

### URL Parameters

| Parameter    | Description                        |
|--------------|------------------------------------|
| departmentId | The Id of the department to delete |

## Schema - Department

```json
{
  "id": "long",
  "externalId": "string",
  "name": "string",
  "desc": "string"
}
```

Schema of department entity

| Field      | Type      | Constraints                            | Description                |
|------------|-----------|----------------------------------------|----------------------------|
| id         | Number    | Either ID or External ID is required   | Internal ID                |
| externalId | Number    | Either ID or External ID is required   | External ID                |
| name       | String    | Required                               | Name of Department         |
| desc       | Text      |                                        | description for Department |
