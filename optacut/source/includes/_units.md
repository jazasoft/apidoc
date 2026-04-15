# Units

## Get All Units

```shell
curl "~/api/units" \
  -H "Authorization: Bearer <access_token>"
```

> The above command returns list of all the units. Refer `Pagination and Sort` and `Schema` Unit for exact
> response structure

This endpoint retrieves all units. It supports pagination, sort, search and filter

### HTTP Request

`GET ~/api/units`

## Get a Specific Unit

```shell
curl "~/api/units/1" \
  -H "Authorization: Bearer <access_token>"
```

> The above command returns JSON structured like this:

```json
{
  "id": 1,
  "name": "Unit A49",
  "unitId": "A49",
  "desc": "Test Description"
}
```

This endpoint retrieves a specific unit.

### HTTP Request

`GET ~/api/units/{unitId}`

### URL Parameters

| Parameter | Description                    |
|-----------|--------------------------------|
| unitId    | The Id of the unit to retrieve |

## Create Unit

```shell
curl "~/api/units" \
  -X POST \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <access_token>" \
  -d '<JSON Payload>'
```

This endpoint creates a unit.

### HTTP Request

`POST ~/api/units`

### JSON Payload

<pre class="center-column">
{
    "id": 1000,
    "externalId": "U001",
    "name": "Unit A49",
    "unitId": "A49",
    "desc": "Test Description"
}
</pre>

> The above command returns JSON structured like this:

```json
{
  "id": 1000,
  "externalId": "U001",
  "name": "Unit A49",
  "unitId": "A49",
  "desc": "Test Description"
}
```

## Create Unit (Batch)

```shell
curl "~/api/units/batch" \
  -X POST \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <access_token>" \
  -d '<JSON Payload>'
```

This endpoint creates a unit.

### HTTP Request

`POST ~/api/units/batch`

### JSON Payload

<pre class="center-column">
[
{
    "id": 1000,
    "externalId": "U001",
    "name": "Unit A49",
    "unitId": "A49",
    "desc": "Test Description"
},
{
    "id": 1001,
    "externalId": "U002",
    "name": "Unit A50",
    "unitId": "A49",
    "desc": "Test Description"
}
]
</pre>

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1000,
    "externalId": "U001",
    "name": "Unit A49",
    "unitId": "A49",
    "desc": "Test Description"
  },
  {
    "id": 1001,
    "externalId": "U002",
    "name": "Unit A50",
    "unitId": "A49",
    "desc": "Test Description"
  }
]
```

## Update a Specific Unit

```shell
curl "~/api/units/1" \
  -X PUT \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <access_token>" \
  -d '<JSON Payload>'
```

This endpoint updates an existing unit.

### HTTP Request

`PUT ~/api/units/{unitId}`

| Parameter | Description                  |
|-----------|------------------------------|
| unitId    | The Id of the unit to update |

### JSON Payload

<pre class="center-column">
{
      "id": 1,
      "externalId": "U001",
      "name": "Unit A49-Updated",
      "unitId": "A49-Updated",
      "desc": "Test Description"
}
</pre>

> The above command returns JSON structured like this:

```json
{
  "id": 1,
  "externalId": "U001",
  "name": "A49-Updated",
  "unitId": "A49",
  "desc": "Test Description"
}
```

## Delete a Specific Unit

```shell
curl "~/api/units/1"
  -X DELETE
  -H "Authorization: Bearer <access_token>"
```

> The above command returns empty content with response status `204`

This endpoint deletes a specific unit.

### HTTP Request

`DELETE ~/api/units/{unitId}`

### URL Parameters

| Parameter | Description                  |
|-----------|------------------------------|
| unitId    | The Id of the unit to delete |

## Schema - Unit

```json
{
  "id": "long",
  "externalId": "string",
  "name": "string",
  "unitId": "string",
  "desc": "string"
}
```

Schema of unit entity

| Field      | Type   | Constraints                             | Description          |
|------------|--------|-----------------------------------------|----------------------|
| id         | Number | Either ID or External ID is required    | Internal ID          |
| externalId | Number | Either ID or External ID is required    | External ID          |
| name       | String | Required                                | Name of Unit         |
| unitId     | String | Required                                | Unit Id              |
| desc       | Text   |                                         | description for Unit |
