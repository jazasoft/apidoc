# Orders

## Get All Orders

```shell
curl "~/api/orders" \
  -H "Authorization: Bearer <access_token>"
```

> The above command returns list of all the orders. Refer `Pagination and Sort` and `Schema` Section for exact response
> structure

This endpoint retrieves all orders. It supports pagination, sort, search and filter

### HTTP Request

`GET ~/api/orders`

## Get a Specific Order

```shell
curl "~/api/orders/1" \
  -H "Authorization: Bearer <access_token>"
```

> The above command returns JSON structured like this:

```json
{
  "id": 1,
  "customerId": 2,
  "seasonId": 1,
  "poRef": "T/100",
  "customerPoRef": "B/100",
  "desc": "Test description",
  "orderQty": 2000,
  "products": "Mens Formal Shirt-L/S",
  "styles": "A6",
  "flowInfoList": [
    {
      "id": 1,
      "flowRef": null,
      "delFlowRef": null,
      "customerFlowRef": null,
      "parentId": null,
      "serialNo": 2,
      "productId": 2,
      "ratio": null,
      "style": "A6",
      "styleNo": null,
      "fit": null,
      "color": "White",
      "groupDestination": false,
      "destination": "US",
      "exFactoryDate": 1685404800000,
      "delMode": "Air",
      "gender": "Male",
      "sleeveType": "FULL",
      "orderQty": 1000,
      "extra": 5.0,
      "shortShipPercent": 5.0,
      "styleImage": null,
      "state": "[{\"state\":\"New\"}]",
      "partList": [
        {
          "id": 10,
          "serial": null,
          "partName": "Shell",
          "placement": "Entire Body",
          "bomCu": 1.2,
          "uom": "meter"
        },
        {
          "id": 11,
          "serial": null,
          "partName": "Trim1",
          "placement": "Neckband",
          "bomCu": 0.1,
          "uom": "meter"
        }
      ],
      "sizeBreakupList": [
        {
          "id": 100,
          "serialNo": 1,
          "sizeGroup": "",
          "size": "30",
          "qty": 300
        },
        {
          "id": 101,
          "serialNo": 2,
          "sizeGroup": "",
          "size": "32",
          "qty": 400
        },
        {
          "id": 102,
          "serialNo": 3,
          "sizeGroup": "",
          "size": "34",
          "qty": 300
        }
      ]
    }
  ]
}
```

This endpoint retrieves a specific order.

### HTTP Request

`GET ~/api/orders/{orderId}`

### URL Parameters

| Parameter | Description                     |
|-----------|---------------------------------|
| orderId   | The Id of the order to retrieve |

## Create Order

```shell
curl "~/api/orders" \
  -X POST \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <access_token>" \
  -d '<JSON Payload>'
```

This endpoint creates an order.

### HTTP Request

`POST ~/api/orders`

### JSON Payload

<pre class="center-column">
{
    "externalId": "1000",
    "poRef": "J/102",
    "customerPoRef": "B/100",
    "customerId": 2,
    "seasonId": 1,
    "desc": "Test description",
    "flowInfoList": [
        {
            "externalId": "2000",
            "serialNo": 1,
            "productId": 1,
            "style": "A6",
            "styleNo": "A1000",
            "fit":"Slim Fit",
            "color": "Black",
            "orderQty": 1000,
            "extra": 5,
            "shortShipPercent": 5,
            "inseam":"32Inch",
            "destination": "US",
            "delMode": "Air",
            "gender": "Male",
            "sleeveType": "FULL",
            "exFactoryDate": "2023-05-30",
            "flowRef":"REF1",
            "delFlowRef":"D.REF1",
            "customerFlowRef": "BPO#01",
            "partList": [
                { "partName": "Shell", "placement": "Entire Body", "bomCu": 1.2, "uom": "meter", "bomFabricId": 1, "bomFabColor": "WHITE", "bomFabColorCode": "WH", "fabOrderQty": 1200 },
                { "partName": "Lining", "placement": "Lining", "bomCu": 0.86, "uom": "meter", "bomFabricId": 2, "bomFabColor": "WHITE", "bomFabColorCode": "WH", "fabOrderQty": 860 },                
                { "partName": "Trim", "placement": "Collar", "bomCu": 0.10, "uom": "meter", "bomFabricId": 3, "bomFabColor": "WHITE", "bomFabColorCode": "WH", "fabOrderQty": 100 }
            ],
            "sizeBreakupList": [
                { "serialNo": 1, "sizeGroup": "", "size": "S", "qty": 150 },
                { "serialNo": 2, "sizeGroup": "", "size": "M", "qty": 200 },
                { "serialNo": 3, "sizeGroup": "", "size": "L", "qty": 300 },
                { "serialNo": 4, "sizeGroup": "", "size": "XL", "qty": 200 },
                { "serialNo": 5, "sizeGroup": "", "size": "2XL", "qty": 150 }
            ]
        },
        {
            "externalId": "2001",
            "serialNo": 1,
            "productId": 1,
            "style": "A6",
            "styleNo": "A1000",
            "fit":"Slim Fit",
            "color": "Black",
            "orderQty": 1000,
            "extra": 5,
            "shortShipPercent": 5,
            "inseam":"32Inch",
            "destination": "UK",
            "delMode": "Air",
            "gender": "Male",
            "sleeveType": "FULL",
            "exFactoryDate": "2023-05-30",
            "flowRef":"REF1",
            "delFlowRef":"D. REF1",
            "customerFlowRef": "BPO#02",
            "partList": [
                { "partName": "Shell", "placement": "Entire Body", "bomCu": 1.2, "uom": "meter", "bomFabricId": 1, "bomFabColor": "WHITE", "bomFabColorCode": "WH", "fabOrderQty": 1200 },
                { "partName": "Lining", "placement": "Lining", "bomCu": 0.86, "uom": "meter", "bomFabricId": 2, "bomFabColor": "WHITE", "bomFabColorCode": "WH", "fabOrderQty": 860 },                
                { "partName": "Trim", "placement": "Collar", "bomCu": 0.10, "uom": "meter", "bomFabricId": 3, "bomFabColor": "WHITE", "bomFabColorCode": "WH", "fabOrderQty": 100 }
            ],
            "sizeBreakupList": [
                { "serialNo": 1, "sizeGroup": "", "size": "S", "qty": 150 },
                { "serialNo": 2, "sizeGroup": "", "size": "M", "qty": 200 },
                { "serialNo": 3, "sizeGroup": "", "size": "L", "qty": 300 },
                { "serialNo": 4, "sizeGroup": "", "size": "XL", "qty": 200 },
                { "serialNo": 5, "sizeGroup": "", "size": "2XL", "qty": 150 }
            ]
        }
    ]
}
</pre>

## Update Order

```shell
curl "~/api/orders?externalId=1000" \
  -X PATCH \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <access_token>" \
  -d '<JSON Payload>'
```

This endpoint updates an existing order.

### HTTP Request

`PATCH ~/api/orders?externalId=<External ID>`

| Parameter  | Description                                         |
|------------|-----------------------------------------------------|
| externalId | The Exetrnal ID  which was used to create the order |

### JSON Payload

<pre class="center-column">
{
    "externalId": "1000",
    "poRef": "J/102",
    "customerPoRef": "B/100",
    "customerId": 2,
    "seasonId": 1,
    "desc": "Test description",
    "flowInfoList": [
        {
            "externalId": "2000",
            "serialNo": 1,
            "productId": 1,
            "style": "A6",
            "styleNo": "A1000",
            "fit":"Slim Fit",
            "color": "Black",
            "orderQty": 1000,
            "extra": 5,
            "shortShipPercent": 5,
            "inseam":"32Inch",
            "destination": "US",
            "delMode": "Air",
            "gender": "Male",
            "sleeveType": "FULL",
            "exFactoryDate": "2023-05-30",
            "flowRef":"REF1",
            "delFlowRef":"D. REF1",
            "customerFlowRef": "BPO#01",
            "partList": [
                { "partName": "Shell", "placement": "Entire Body", "bomCu": 1.2, "uom": "meter", "bomFabricId": 1, "bomFabColor": "WHITE", "bomFabColorCode": "WH", "fabOrderQty": 1200 },
                { "partName": "Lining", "placement": "Lining", "bomCu": 0.86, "uom": "meter", "bomFabricId": 2, "bomFabColor": "WHITE", "bomFabColorCode": "WH", "fabOrderQty": 860 },                
                { "partName": "Trim", "placement": "Collar", "bomCu": 0.10, "uom": "meter", "bomFabricId": 3, "bomFabColor": "WHITE", "bomFabColorCode": "WH", "fabOrderQty": 100 }
            ],
            "sizeBreakupList": [
                { "serialNo": 1, "sizeGroup": "", "size": "S", "qty": 150 },
                { "serialNo": 2, "sizeGroup": "", "size": "M", "qty": 200 },
                { "serialNo": 3, "sizeGroup": "", "size": "L", "qty": 300 },
                { "serialNo": 4, "sizeGroup": "", "size": "XL", "qty": 200 },
                { "serialNo": 5, "sizeGroup": "", "size": "2XL", "qty": 150 }
            ]
        },
        {
            "externalId": "2001",
            "serialNo": 1,
            "productId": 1,
            "style": "A6",
            "styleNo": "A1000",
            "fit":"Slim Fit",
            "color": "Black",
            "orderQty": 1000,
            "extra": 5,
            "shortShipPercent": 5,
            "inseam":"32Inch",
            "destination": "UK",
            "delMode": "Air",
            "gender": "Male",
            "sleeveType": "FULL",
            "exFactoryDate": "2023-05-30",
            "flowRef":"REF1",
            "delFlowRef":"D. REF1",
            "customerFlowRef": "BPO#02",
            "partList": [
                { "partName": "Shell", "placement": "Entire Body", "bomCu": 1.2, "uom": "meter", "bomFabricId": 1, "bomFabColor": "WHITE", "bomFabColorCode": "WH", "fabOrderQty": 1200 },
                { "partName": "Lining", "placement": "Lining", "bomCu": 0.86, "uom": "meter", "bomFabricId": 2, "bomFabColor": "WHITE", "bomFabColorCode": "WH", "fabOrderQty": 860 },                
                { "partName": "Trim", "placement": "Collar", "bomCu": 0.10, "uom": "meter", "bomFabricId": 3, "bomFabColor": "WHITE", "bomFabColorCode": "WH", "fabOrderQty": 100 }
            ],
            "sizeBreakupList": [
                { "serialNo": 1, "sizeGroup": "", "size": "S", "qty": 150 },
                { "serialNo": 2, "sizeGroup": "", "size": "M", "qty": 200 },
                { "serialNo": 3, "sizeGroup": "", "size": "L", "qty": 300 },
                { "serialNo": 4, "sizeGroup": "", "size": "XL", "qty": 200 },
                { "serialNo": 5, "sizeGroup": "", "size": "2XL", "qty": 150 }
            ]
        }
    ]
}
</pre>

## Delete  Order

```shell
curl "~/api/orders?externalId=1000"
  -X DELETE
  -H "Authorization: Bearer <access_token>"
```

> The above command returns empty content with response status `204`

This endpoint deletes a specific order.

### HTTP Request

`DELETE ~/api/orders?externalId=<External Order Id>`

### URL Parameters

| Parameter  | Description                                                |
|------------|------------------------------------------------------------|
| externalId | The external Id of the order which was sent while creating |

## Schema - Order

```json
{
  "id": "long",
  "externalId": "string",
  "customerId": "long",
  "seasonId": "long",
  "poRef": "string",
  "customerPoRef": "string",
  "desc": "string",
  "orderQty": "int",
  "flowInfoList": [
    {
      "id": "long",
      "externalId": "string",
      "flowRef": "string",
      "delFlowRef": "string",
      "customerFlowRef": "string",
      "serialNo": "int",
      "productId": "long",
      "style": "string",
      "styleNo": "string",
      "fit": "string",
      "inseam": "string",
      "color": "string",
      "destination": "string",
      "exFactoryDate": "yyyy-MM-dd",
      "delMode": "string",
      "gender": "string",
      "sleeveType": "string",
      "orderQty": "int",
      "extra": "float",
      "shortShipPercent": "float",
      "partList": [
        {
          "id": "long",
          "serial": "int",
          "partName": "string",
          "placement": "string",
          "bomCu": "float",
          "uom": "string",
          "bomFabricId": "long",
          "bomFabColor": "string",
          "bomFabColorCode": "string",
          "fabOrderQty": "int"
        }
      ],
      "sizeBreakupList": [
        {
          "id": "long",
          "serialNo": "int",
          "sizeGroup": "string",
          "size": "string",
          "qty": "int"
        }
      ]
    }
  ]
}
```

**Order Table**

| Field         | Type   | Constraints | Description                       |
|---------------|--------|-------------|-----------------------------------|
| id            | Long   | Primary Key | Internal ID                       |
| externalId    | String | Unique      | External ID                       |
| poRef         | String | Required    | Purchase Order Reference          |
| customerPoRef | String |             | Customer Purchase Order Reference |
| customerId    | Long   |             | Internal ID of Customer           |
| seasonId      | Long   |             | Internal ID of Season             |
| desc          | Text   |             | description for Order             |

**FlowInfo Table**

| Field            | Type   | Constraints | Description                                     |
|------------------|--------|-------------|-------------------------------------------------|
| id               | Long   | Primary Key | Internal ID                                     |
| externalId       | String | Unique      | External ID                                     |
| serialNo         | Long   |             | Sequence                                        |
| flowRef          | String |             | ERP Reference number at Color Level             |
| delFlowRef       | String |             | Customer+ERP Reference number at Delivery Level |
| customerFlowRef  | String |             | Customer Reference  number at Color Level       |
| productId        | Long   | Required    | Internal ID of Product                          |
| style            | String | Required    | Style Name                                      |
| styleNo          | String |             | Style Long                                      |
| fit              | String |             | Fit                                             |
| inseam           | String |             | Inseam                                          |
| color            | String | Required    | Style Color                                     |
| destination      | String |             | Destination                                     |
| delMode          | String |             | Delivery Mode. Values: (`Air`, `Sea`, `Road`)   |
| gender           | String |             | Gender                                          |
| sleeveType       | String |             | Sleeve Type                                     |
| exFactoryDate    | Date   |             | Delivery Date. Format: `yyyy-MM-dd`             |
| orderQty         | Int    | Required    | Order Qty in this flow                          |
| extra            | Float  |             | Allowed Extra percent                           |
| shortShipPercent | Float  |             | Short Shipment Tolerance percent                |

**Part Table**

| Field           | Type   | Constraints | Description                                                                |
|-----------------|--------|-------------|----------------------------------------------------------------------------|
| id              | Long   | Primary Key | Internal ID                                                                |
| partName        | String | Required    | Part Name                                                                  |
| placement       | String |             | Part Placement                                                             |
| bomCu           | Float  |             | BOM Consumption                                                            |
| uom             | String |             | Unit of Measurement for BOM Consumption. Values: (`meter`, `gram`, `yard`) |
| bomFabricId     | Long   |             | Item Master ID                                                             |
| bomFabColor     | String |             | Item Color                                                                 |
| bomFabColorCode | String |             | Item Color Code                                                            |
| fabOrderQty     | Int    |             | Fabric Order Qty                                                           |

**Size Breakup Table**

| Field     | Type   | Constraints | Description            |
|-----------|--------|-------------|------------------------|
| id        | Long   | Primary Key | Internal ID            |
| serialNo  | Int    |             | Sequence of Size       |
| sizeGroup | String |             | Inseam if applicable   |
| size      | String | Required    | Size  Name             |
| qty       | Int    | Required    | Order qty in this size |







