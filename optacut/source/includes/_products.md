# Products

## Get All Products

```shell
curl "~/api/products" \
  -H "Authorization: Bearer <access_token>"
```

> The above command returns list of all the products. Refer `Pagination and Sort` and `Schema` Section for exact
> response structure

This endpoint retrieves all products. It supports pagination, sort, search and filter

### HTTP Request

`GET ~/api/products`

## Get a Specific Product

```shell
curl "~/api/products/1" \
  -H "Authorization: Bearer <access_token>"
```

> The above command returns JSON structured like this:

```json
{
  "id": 1,
  "name": "Shirt",
  "isSet": false,
  "desc": "Test Description",
  "productList": []
}
```

This endpoint retrieves a specific product.

### HTTP Request

`GET ~/api/products/{productId}`

### URL Parameters

| Parameter | Description                       |
|-----------|-----------------------------------|
| productId | The Id of the product to retrieve |

## Create Product

```shell
curl "~/api/products" \
  -X POST \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <access_token>" \
  -d '<JSON Payload>'
```

This endpoint creates a product.

### HTTP Request

`POST ~/api/products`

### JSON Payload

<pre class="center-column">
{
    "id": 1000,
    "externalId": "P001",
    "name": "Shirt",
    "desc": "Test Description",
    "isSet": false,
    "productList": []
}
</pre>

> The above command returns JSON structured like this:

```json
{
  "id": 1,
  "externalId": "P001",
  "name": "Shirt",
  "isSet": false,
  "desc": "Test Description",
  "productList": []
}
```

## Create Product (Batch)

```shell
curl "~/api/products/batch" \
  -X POST \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <access_token>" \
  -d '<JSON Payload>'
```

This endpoint creates a product.

### HTTP Request

`POST ~/api/products/batch`

### JSON Payload

<pre class="center-column">
[
{
    "id": 1000,
    "externalId": "P001",
    "name": "Shirt",
    "desc": "Test Description",
    "isSet": false,
    "productList": []
},
{
    "id": 1001,
    "externalId": "P002",
    "name": "Trouser",
    "desc": "Test Description",
    "isSet": false,
    "productList": []
}
]
</pre>

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1000,
    "externalId": "P001",
    "name": "Shirt",
    "desc": "Test Description",
    "isSet": false,
    "productList": []
  },
  {
    "id": 1001,
    "externalId": "P002",
    "name": "Trouser",
    "desc": "Test Description",
    "isSet": false,
    "productList": []
  }
]
```

## Update a Specific Product

```shell
curl "~/api/products/1" \
  -X PUT \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <access_token>" \
  -d '<JSON Payload>'
```

This endpoint updates an existing product.

### HTTP Request

`PUT ~/api/products/{productId}`

| Parameter | Description                     |
|-----------|---------------------------------|
| productId | The Id of the product to update |

### JSON Payload

<pre class="center-column">
{
      "id": 1,
      "externalId": "P001",
      "name": "Shirt-Updated",
      "isSet": false,
      "desc": "Test Description",
      "productList": []
}
</pre>

> The above command returns JSON structured like this:

```json
{
  "id": 1,
  "externalId": "P001",
  "name": "Shirt-Updated",
  "isSet": false,
  "desc": "Test Description",
  "productList": []
}
```

## Delete a Specific Product

```shell
curl "~/api/products/1"
  -X DELETE
  -H "Authorization: Bearer <access_token>"
```

> The above command returns empty content with response status `204`

This endpoint deletes a specific product.

### HTTP Request

`DELETE ~/api/products/{productId}`

### URL Parameters

| Parameter | Description                     |
|-----------|---------------------------------|
| productId | The Id of the product to delete |

## Schema - Product

```json
{
  "id": "long",
  "externalId": "string",
  "name": "string",
  "isSet": "boolean",
  "desc": "string",
  "productList": "product[]"
}
```

Schema of product entity

| Field      | Type     | Constraints                           | Description                        |
|------------|----------|---------------------------------------|------------------------------------|
| id         | Number   | Either ID or External ID is required  | Internal ID                        |
| externalId | Number   | Either ID or External ID is required  | External ID                        |
| name       | String   | Required                              | Name of Product                    |
| isSet      | Boolean  |                                       | Whether product is set of products |
| desc       | Text     |                                       | description for Product            |
