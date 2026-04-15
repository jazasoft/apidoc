# Fabric Categories

## Get All Fabric Categories

```shell
curl "~/api/fabric-categories" \
  -H "Authorization: Bearer <access_token>"
```

> The above command returns list of all the fabricCategories. Refer `Pagination and Sort` and `Schema` Section for exact
> response structure

This endpoint retrieves all fabricCategories. It supports pagination, sort, search and filter

### HTTP Request

`GET ~/api/fabric-categories`

## Get a Specific Fabric Category

```shell
curl "~/api/fabric-categories/1" \
  -H "Authorization: Bearer <access_token>"
```

> The above command returns JSON structured like this:

```json
{
  "id": 1,
  "name": "Oxford",
  "desc": "Test Description"
}
```

This endpoint retrieves a specific fabricCategory.

### HTTP Request

`GET ~/api/fabric-categories/{fabricCategoryId}`

### URL Parameters

| Parameter        | Description                              |
|------------------|------------------------------------------|
| fabricCategoryId | The Id of the fabricCategory to retrieve |

## Create Fabric Category

```shell
curl "~/api/fabric-categories" \
  -X POST \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <access_token>" \
  -d '<JSON Payload>'
```

This endpoint creates a fabricCategory.

### HTTP Request

`POST ~/api/fabric-categories`

### JSON Payload

<pre class="center-column">
{
    "externalId": "FC001",
    "name": "Oxford",
    "desc": "Test Description"
}
</pre>

> The above command returns JSON structured like this:

```json
{
  "id": 1,
  "externalId": "FC001",
  "name": "Oxford",
  "desc": "Test Description"
}
```

## Update a Specific Fabric Category

```shell
curl "~/api/fabric-categories/1" \
  -X PUT \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <access_token>" \
  -d '<JSON Payload>'
```

This endpoint updates an existing fabricCategory.

### HTTP Request

`PUT ~/api/fabric-categories/{fabricCategoryId}`

| Parameter        | Description                            |
|------------------|----------------------------------------|
| fabricCategoryId | The Id of the fabricCategory to update |

### JSON Payload

<pre class="center-column">
{
      "id": 1,
      "externalId": "FC001",
      "name": "Oxford-Updated",
      "desc": "Test Description"
}
</pre>

> The above command returns JSON structured like this:

```json
{
  "id": 1,
  "externalId": "FC001",
  "name": "Oxford-Updated",
  "desc": "Test Description"
}
```

## Delete a Specific Fabric Category

```shell
curl "~/api/fabric-categories/1"
  -X DELETE
  -H "Authorization: Bearer <access_token>"
```

> The above command returns empty content with response status `204`

This endpoint deletes a specific fabricCategory.

### HTTP Request

`DELETE ~/api/fabric-categories/{fabricCategoryId}`

### URL Parameters

| Parameter        | Description                            |
|------------------|----------------------------------------|
| fabricCategoryId | The Id of the fabricCategory to delete |

## Schema - Fabric Category

```json
{
  "id": "long",
  "externalId": "string",
  "name": "string",
  "desc": "string"
}
```

Schema of Fabric Category entity

| Field      | Type   | Constraints                          | Description                     |
|------------|--------|--------------------------------------|---------------------------------|
| id         | Number | Either ID or External ID is required | Internal ID                     |
| externalId | Number | Either ID or External ID is required | External ID                     |
| name       | String | Required                             | Name of Fabric Category         |
| desc       | Text   |                                      | description for Fabric Category |
