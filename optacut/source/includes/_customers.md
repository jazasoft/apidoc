# Customers

## Get All Customers

```shell
curl "~/api/customers" \
  -H "Authorization: Bearer <access_token>"
```

> The above command returns list of all the customers. Refer `Pagination and Sort` and `Schema` Section for exact
> response structure

This endpoint retrieves all customers. It supports pagination, sort, search and filter

### HTTP Request

`GET ~/api/customers`

## Get a Specific Customer

```shell
curl "~/api/customers/1" \
  -H "Authorization: Bearer <access_token>"
```

> The above command returns JSON structured like this:

```json
{
  "id": 1,
  "name": "GANT",
  "code": "GNT",
  "desc": "Test Description"
}
```

This endpoint retrieves a specific customer.

### HTTP Request

`GET ~/api/customers/{customerId}`

### URL Parameters

| Parameter  | Description                        |
|------------|------------------------------------|
| customerId | The Id of the customer to retrieve |

## Create Customer

```shell
curl "~/api/customers" \
  -X POST \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <access_token>" \
  -d '<JSON Payload>'
```

This endpoint creates a customer.

### HTTP Request

`POST ~/api/customers`

### JSON Payload

<pre class="center-column">
{
    "id": 1000,
    "externalId": "C001",
    "name": "GANT",
    "code": "GNT",
    "desc": "Test Description"
}
</pre>

> The above command returns JSON structured like this:

```json
{
  "id": 1000,
  "externalId": "C001",
  "name": "GANT",
  "code": "GNT",
  "desc": "Test Description"
}
```


## Create Customer (Batch)

```shell
curl "~/api/customers/batch" \
  -X POST \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <access_token>" \
  -d '<JSON Payload>'
```

This endpoint creates a customer.

### HTTP Request

`POST ~/api/customers/batch`

### JSON Payload

<pre class="center-column">
[
{
    "id": 1000,
    "externalId": "C001",
    "name": "GANT",
    "code": "GNT",
    "desc": "Test Description"
},
{
    "id": 1001,
    "externalId": "C002",
    "name": "Dressmann",
    "code": "DM",
    "desc": "Test Description2"
}
]
</pre>

> The above command returns JSON structured like this:

```json
[
  {
    "id": 4000,
    "externalId": "C001",
    "name": "GANT",
    "code": "GNT",
    "desc": "Test Description"
  },
  {
    "id": 4000,
    "externalId": "C002",
    "name": "Dressmann",
    "code": "DM",
    "desc": "Test Description2"
  }
]
```

## Update a Specific Customer

```shell
curl "~/api/customers/1" \
  -X PUT \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <access_token>" \
  -d '<JSON Payload>'
```

This endpoint updates an existing customer.

### HTTP Request

`PUT ~/api/customers/{customerId}`

| Parameter  | Description                      |
|------------|----------------------------------|
| customerId | The Id of the customer to update |

### JSON Payload

<pre class="center-column">
{
      "id": 1,
      "externalId": "C001",
      "name": "GANT-Updated",
      "code": "GNT",
      "desc": "Test Description"
}
</pre>

> The above command returns JSON structured like this:

```json
{
  "id": 1,
  "externalId": "C001",
  "name": "GANT-Updated",
  "code": "GNT",
  "desc": "Test Description"
}
```

## Delete a Specific Customer

```shell
curl "~/api/customers/1"
  -X DELETE
  -H "Authorization: Bearer <access_token>"
```

> The above command returns empty content with response status `204`

This endpoint deletes a specific customer.

### HTTP Request

`DELETE ~/api/customers/{customerId}`

### URL Parameters

| Parameter  | Description                      |
|------------|----------------------------------|
| customerId | The Id of the customer to delete |

## Schema - Customer

```json
{
  "id": "long",
  "externalId": "string",
  "name": "string",
  "code": "string",
  "desc": "string"
}
```

Schema of Customer entity

| Field      | Type      | Constraints                           | Description              |
|------------|-----------|---------------------------------------|--------------------------|
| id         | Number    | Either ID or External ID is required  | Internal ID              |
| externalId | Number    | Either ID or External ID is required  | External ID              |
| name       | String    | Required                              | Name of Customer         |
| code       | String    |                                       | Short code for Customer  |
| desc       | Text      |                                       | description for Customer |
