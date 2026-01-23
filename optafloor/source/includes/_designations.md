# Designations

## Get All Designations

```shell
curl "~/v1/api/designations" \
  -H "Authorization: Bearer <access_token>"
```

> The above command returns list of all the designations. Refer `Pagination and Sort` and `Schema` Section for exact
> response structure

This endpoint retrieves all designations. It supports pagination, sort, search and filter

### HTTP Request

`GET ~/api/designations`

## Get a Specific Designation

```shell
curl "~/v1/api/designations/1" \
  -H "Authorization: Bearer <access_token>"
```

> The above command returns JSON structured like this:

```json
{
  "id": 100,
  "name": "Mechanic",
  "desc": ""
}
```

This endpoint retrieves a specific designation.

### HTTP Request

`GET ~/v1/api/designations/{designationId}`

### URL Parameters

| Parameter     | Description                           |
|---------------|---------------------------------------|
| designationId | The Id of the designation to retrieve |

## Create Designation

```shell
curl "~/v1/api/designations" \
  -X POST \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <access_token>" \
  -d '<JSON Payload>'
```

This endpoint creates a designation.

### HTTP Request

`POST ~/v1/api/designations`

### JSON Payload

<pre class="center-column">
{
  "id": 100,
  "externalId": "E123",
  "name": "Mechanic",  
  "desc": ""
}
</pre>

> The above command returns JSON structured like this:

```json
{
  "id": 100,
  "externalId": "E123",
  "name": "Mechanic",
  "desc": ""
}
```

## Update a Specific Designation

```shell
curl "~/v1/api/designations/1" \
  -X PUT \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <access_token>" \
  -d '<JSON Payload>'
```

This endpoint updates an existing designation.

### HTTP Request

`PUT ~/v1/api/designations/{designationId}`

| Parameter     | Description                         |
|---------------|-------------------------------------|
| designationId | The Id of the designation to update |

### JSON Payload

<pre class="center-column">
{
  "id": 100,
  "name": "Mechanic",  
  "desc": ""
}
</pre>

> The above command returns JSON structured like this:

```json
{
  "id": 100,
  "name": "Mechanic",
  "desc": ""
}
```

## Update a Specific Designation (Using External Id)

```shell
curl "~/v1/api/designations?externalId=E123" \
  -X PUT \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <access_token>" \
  -d '<JSON Payload>'
```

This endpoint updates an existing designation.

### HTTP Request

`PUT ~/v1/api/designations?externalId=<External ID>`

| Parameter  | Description                                  |
|------------|----------------------------------------------|
| externalId | The External Id of the designation to update |

### JSON Payload

<pre class="center-column">
{
  "externalId": "E123",
  "name": "Mechanic",  
  "desc": ""
}
</pre>

> The above command returns JSON structured like this:

```json
{
  "id": 100,
  "externalId": "E123",
  "name": "Mechanic",
  "desc": ""
}
```

## Delete a Specific Designation

```shell
curl "~/v1/api/designations/1"
  -X DELETE
  -H "Authorization: Bearer <access_token>"
```

> The above command returns empty content with response status `204`

This endpoint deletes a specific designation.

### HTTP Request

`DELETE ~/v1/api/designations/{designationId}`

### URL Parameters

| Parameter     | Description                         |
|---------------|-------------------------------------|
| designationId | The Id of the designation to delete |

## Schema - Designation

```json
{
  "id": "long",
  "name": "string",
  "desc": "string"
}
```

Schema of designation entity

| Field      | Type   | Constraints | Description                 |
|------------|--------|-------------|-----------------------------|
| id         | Number | Primary Key | Internal ID                 |
| externalId | Text   | Unique Key  | External ID                 |
| name       | String | Required    | Name of Designation         |
| desc       | Text   |             | description for Designation |
