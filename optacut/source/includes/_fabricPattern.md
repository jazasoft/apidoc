# Fabric Patterns

## Get All Fabric Patterns

```shell
curl "~/api/fabric-patterns" \
  -H "Authorization: Bearer <access_token>"
```

> The above command returns list of all the fabricCategories. Refer `Pagination and Sort` and `Schema` Section for exact
> response structure

This endpoint retrieves all fabric patterns. It supports pagination, sort, search and filter

### HTTP Request

`GET ~/api/fabric-patterns`

## Get a Specific Fabric Pattern

```shell
curl "~/api/fabric-patterns/1" \
  -H "Authorization: Bearer <access_token>"
```

> The above command returns JSON structured like this:

```json
{
  "id": 1,
  "name": "Checks",
  "desc": "Test Description"
}
```

This endpoint retrieves a specific fabricCategory.

### HTTP Request

`GET ~/api/fabric-patterns/{fabricPatternId}`

### URL Parameters

| Parameter       | Description                              |
|-----------------|------------------------------------------|
| fabricPatternId | The Id of the fabricCategory to retrieve |

## Create Fabric Pattern

```shell
curl "~/api/fabric-patterns" \
  -X POST \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <access_token>" \
  -d '<JSON Payload>'
```

This endpoint creates a fabricCategory.

### HTTP Request

`POST ~/api/fabric-patterns`

### JSON Payload

<pre class="center-column">
{
    "externalId": "FP001",
    "name": "Checks",
    "desc": "Test Description"
}
</pre>

> The above command returns JSON structured like this:

```json
{
  "id": 1,
  "externalId": "FP001",
  "name": "Checks",
  "desc": "Test Description"
}
```

## Update a Specific Fabric Pattern

```shell
curl "~/api/fabric-patterns/1" \
  -X PUT \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <access_token>" \
  -d '<JSON Payload>'
```

This endpoint updates an existing fabricCategory.

### HTTP Request

`PUT ~/api/fabric-patterns/{fabricPatternId}`

| Parameter       | Description                            |
|-----------------|----------------------------------------|
| fabricPatternId | The Id of the fabricCategory to update |

### JSON Payload

<pre class="center-column">
{
      "id": 1,
      "externalId": "FP001",
      "name": "Checks-Updated",
      "desc": "Test Description"
}
</pre>

> The above command returns JSON structured like this:

```json
{
  "id": 1,
  "externalId": "FP001",
  "name": "Checks-Updated",
  "desc": "Test Description"
}
```

## Delete a Specific Fabric Pattern

```shell
curl "~/api/fabric-patterns/1"
  -X DELETE
  -H "Authorization: Bearer <access_token>"
```

> The above command returns empty content with response status `204`

This endpoint deletes a specific fabricCategory.

### HTTP Request

`DELETE ~/api/fabric-patterns/{fabricPatternId}`

### URL Parameters

| Parameter       | Description                            |
|-----------------|----------------------------------------|
| fabricPatternId | The Id of the fabricCategory to delete |

## Schema - Fabric Pattern

```json
{
  "id": "long",
  "externalId": "string",
  "name": "string",
  "desc": "string"
}
```

Schema of Fabric Pattern entity

| Field      | Type   | Constraints                           | Description                    |
|------------|--------|---------------------------------------|--------------------------------|
| id         | Number | Either ID or External ID is required  | Internal ID                    |
| externalId | Number | Either ID or External ID is required  | External ID                    |
| name       | String | Required                              | Name of Fabric Pattern         |
| desc       | Text   |                                       | description for Fabric Pattern |
