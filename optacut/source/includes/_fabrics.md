# Fabrics

## Get All Fabrics

```shell
curl "~/api/fabrics" \
  -H "Authorization: Bearer <access_token>"
```

> The above command returns list of all the fabrics. Refer `Pagination and Sort` and `Schema` Section for exact response structure

This endpoint retrieves all fabrics. It supports pagination, sort, search and filter

### HTTP Request

`GET ~/api/fabrics`

## Get a Specific Fabric

```shell
curl "~/api/fabrics/1" \
  -H "Authorization: Bearer <access_token>"
```

> The above command returns JSON structured like this:

```json
{
  "id": 1,
  "itemCode": "HO/200",
  "supplierItemCode": "200",
  "articleName": "200",
  "classification": "Woven",
  "repeatLength": 2,
  "repeatWidth": 2,
  "construction": "Test construction",
  "content": "100% cotton",
  "width": 147.0,
  "gsm": null,
  "warpShrinkage": null,
  "weftShrinkage": null,
  "remarks": null,
  "fabricPatternId": 4,
  "fabricCategoryId": 5,
  "supplierIds": [10],
  "colorList": [
    { "id": 10, "color": "Black", "swatchImage": null },
    { "id": 11,"color": "White", "swatchImage": null }
  ]
}
```

This endpoint retrieves a specific fabric.

### HTTP Request

`GET ~/api/fabrics/{fabricId}`

### URL Parameters

| Parameter | Description                      |
|-----------|----------------------------------|
| fabricId  | The Id of the fabric to retrieve |

## Create Fabric

```shell
curl "~/api/fabrics" \
  -X POST \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <access_token>" \
  -d '<JSON Payload>'
```

This endpoint creates a fabric.

### HTTP Request

`POST ~/api/fabrics`

### JSON Payload

<pre class="center-column">
{
  "externalId": "F001",
  "itemCode": "IT-200",
  "itemDesc": "Test Description",
  "articleName": "ART-200",
  "classification": "Woven",
  "fabricCategoryId": 2,
  "fabricPatternId": 1,
  "construction": "4*4",
  "content": "100% Cotton",
  "repeatLength": 4,
  "repeatWidth": 4,
  "gsm": 1.2,
  "colorList": [
    {"color": "WHITE"},
    {"color": "BLACK"}
  ]
}
</pre>

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "externalId": "F001",
  "itemCode": "IT-200",
  "itemDesc": "Test Description",
  "articleName": "ART-200",
  "classification": "Woven",
  "fabricPatternId": 1,
  "fabricCategoryId": 2,
  "repeatLength": 4.0,
  "repeatWidth": 4.0,
  "construction": "4*4",
  "content": "100% Cotton",
  "gsm": 1.2,
  "colorList": [
    { "id": 2, "color": "WHITE" },
    { "id": 3, "color": "BLACK" }
  ]
}
```

## Update a Specific Fabric

```shell
curl "~/api/fabrics/1" \
  -X PUT \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <access_token>" \
  -d '<JSON Payload>'
```

This endpoint updates an existing fabric.

### HTTP Request

`PUT ~/api/fabrics/{fabricId}`

| Parameter | Description                    |
|-----------|--------------------------------|
| fabricId  | The Id of the fabric to update |

### JSON Payload

<pre class="center-column">
{
  "id": 2,
  "externalId": "F001",
  "itemCode": "IT-200-UPDATED",
  "itemDesc": "Test Description",
  "articleName": "ART-200",
  "classification": "Woven",
  "fabricPatternId": 1,
  "fabricCategoryId": 2,
  "repeatLength": 4.0,
  "repeatWidth": 4.0,
  "construction": "4*4",
  "content": "100% Cotton",
  "gsm": 1.2,
  "colorList": [
    { "id": 2, "color": "WHITE" },
    { "id": 3, "color": "BLACK" }
  ]
}
</pre>

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "externalId": "F001",
  "itemCode": "IT-200-UPDATED",
  "itemDesc": "Test Description",
  "articleName": "ART-200",
  "classification": "Woven",
  "fabricPatternId": 1,
  "fabricCategoryId": 2,
  "repeatLength": 4.0,
  "repeatWidth": 4.0,
  "construction": "4*4",
  "content": "100% Cotton",
  "gsm": 1.2,
  "colorList": [
    { "id": 2, "color": "WHITE" },
    { "id": 3, "color": "BLACK" }
  ]
}
```

## Delete  Fabric

```shell
curl "~/api/fabrics/{fabricId}"
  -X DELETE
  -H "Authorization: Bearer <access_token>"
```

> The above command returns empty content with response status `204`

This endpoint deletes a specific fabric.

### HTTP Request

`DELETE ~/api/fabrics/{fabricId}`

### URL Parameters

| Parameter | Description                    |
|-----------|--------------------------------|
| fabricId  | The Id of the fabric to delete |

## Schema - Fabric

```json
{
  "id": "long",
  "externalId": "string",
  "itemCode": "string",
  "supplierItemCode": "string",
  "articleName": "string",
  "classification": "string",
  "repeatLength": "float",
  "repeatWidth": "float",
  "construction": "string",
  "content": "string",
  "width": "float",
  "gsm": "float",
  "fabricPatternId": "long",
  "fabricCategoryId": "long",
  "colorList": [
    { "id": "long", "color": "string", "swatchImage": "string" }
  ]
}
```

This is schema of Fabric entity

**Fabric Table**

| Field            | Type   | Constraints                          | Description                                                     |
|------------------|--------|--------------------------------------|-----------------------------------------------------------------|
| id               | Number | Either ID or External ID is required | Internal ID                                                     |
| externalId       | Number | Either ID or External ID is required | External ID                                                     |
| itemCode         | String | Required                             | Item Code in ERP                                                |
| supplierItemCode | String |                                      | Item Code from Supplier                                         |
| articleName      | String |                                      | Article Name                                                    |
| classification   | String |                                      | Fabric classification. Values: (`Woven`,`Non-Woven`, `Knitted`) |
| fabricPatternId  | long   |                                      | Fabric Pattern Internal ID                                      |
| fabricCategoryId | long   |                                      | Fabric Category Internal ID                                     |
| repeatLength     | Float  |                                      | Repeat value length wise                                        |
| repeatWidth      | Float  |                                      | Repeat value width wise                                         |
| width            | Float  |                                      | Booking width                                                   |
| gsm              | Float  |                                      | GSM value (Gram per square meter), if available                 |

**Color Table**

| Field       | Type   | Constraints | Description           |
|-------------|--------|-------------|-----------------------|
| id          | Long   | Primary Key | Internal ID           |
| color       | String | Required    | Fabric color          |
| swatchImage | String |             | swatch image filename |


