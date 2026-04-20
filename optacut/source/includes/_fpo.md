# Factory Production Order

## Create FPO (v2)

```shell
curl "~/api/fpo?externalOrderId=1000" \
  -X POST \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <access_token>" \
  -d '<JSON Payload>'
```

This endpoint creates a factory production order.

### HTTP Request

`POST ~/api/fpo?externalOrderId=<External Order Id>`

### URL Parameters

| Parameter       | Description                     |
|-----------------|---------------------------------|
| externalOrderId | The external ID of parent Order |

### JSON Payload

<pre class="center-column">
{
  "fpo": "FPO#200",
  "unitId": "unit1",
  "fpoLevel": "BPO",
  "flowInfoList": [
    {
      "externalId": "2000",
      "productId": 1,
      "extProductId": "P001",
      "style": "A6",
      "color": "Black",
      "inseam": "32Inch",
      "destination": "US",
      "delMode": "Air",
      "deliveryDate": "2023-05-30",
      "flowRef": "REF1",
      "delFlowRef": "D. REF1",
      "customerFlowRef": "BPO#01",
      "orderQty": 1000,
      "extra": 5,
      "sizeBreakupList": [
        { "serialNo": 1, "sizeGroup": "", "size": "S", "qty": 150 },
        { "serialNo": 2, "sizeGroup": "", "size": "M", "qty": 200 },
        { "serialNo": 3, "sizeGroup": "", "size": "L", "qty": 300 },
        { "serialNo": 4, "sizeGroup": "", "size": "XL", "qty": 200 },
        { "serialNo": 5, "sizeGroup": "", "size": "2XL", "qty": 150 }
      ],
      "departmentList": [
        { "id": 1, "name": "Cutting" },
        { "id": 2, "name": "Sewing" },
        { "id": 3, "name": "Finishing" }
      ]
    },
    {
      "externalId": "2001",
      "productId": 1,
      "extProductId": "P001",
      "style": "A6",
      "color": "Black",
      "inseam": "32Inch",
      "destination": "UK",
      "delMode": "Air",
      "deliveryDate": "2023-05-30",
      "flowRef": "REF1",
      "delFlowRef": "D. REF1",
      "customerFlowRef": "BPO#01",
      "orderQty": 1000,
      "extra": 5,
      "sizeBreakupList": [
        { "serialNo": 1, "sizeGroup": "", "size": "S", "qty": 150 },
        { "serialNo": 2, "sizeGroup": "", "size": "M", "qty": 200 },
        { "serialNo": 3, "sizeGroup": "", "size": "L", "qty": 300 },
        { "serialNo": 4, "sizeGroup": "", "size": "XL", "qty": 200 },
        { "serialNo": 5, "sizeGroup": "", "size": "2XL", "qty": 150 }
      ],
      "departmentList": [
        { "id": 1, "name": "Cutting" },
        { "id": 2, "name": "Sewing" },
        { "id": 3, "name": "Finishing" }
      ]
    }
  ]
}
</pre>

## Update FPO (v2)

```shell
curl "~/api/fpo?externalOrderId=1000" \
  -X PUT \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <access_token>" \
  -d '<JSON Payload>'
```

This endpoint updates a factory production order.

### HTTP Request

`PUT ~/api/fpo?externalOrderId=<External Order Id>`

### URL Parameters

| Parameter       | Description                     |
|-----------------|---------------------------------|
| externalOrderId | The external ID of parent Order |

### JSON Payload

<pre class="center-column">
{
  "fpo": "FPO#200",
  "unitId": "unit1",
  "fpoLevel": "BPO",
  "flowInfoList": [
    {
      "externalId": "2000",
      "productId": 1,
      "extProductId": "P001",
      "style": "A6",
      "color": "Black",
      "inseam": "32Inch",
      "destination": "US",
      "delMode": "Air",
      "deliveryDate": "2023-05-30",
      "flowRef": "REF1",
      "delFlowRef": "D. REF1",
      "customerFlowRef": "BPO#01",
      "orderQty": 1000,
      "extra": 5,
      "sizeBreakupList": [
        { "serialNo": 1, "sizeGroup": "", "size": "S", "qty": 150 },
        { "serialNo": 2, "sizeGroup": "", "size": "M", "qty": 200 },
        { "serialNo": 3, "sizeGroup": "", "size": "L", "qty": 300 },
        { "serialNo": 4, "sizeGroup": "", "size": "XL", "qty": 200 },
        { "serialNo": 5, "sizeGroup": "", "size": "2XL", "qty": 150 }
      ],
      "departmentList": [
        { "id": 1, "name": "Cutting" },
        { "id": 2, "name": "Sewing" },
        { "id": 3, "name": "Finishing" }
      ]
    },
    {
      "externalId": "2001",
      "productId": 1,
      "extProductId": "P001",
      "style": "A6",
      "color": "Black",
      "inseam": "32Inch",
      "destination": "UK",
      "delMode": "Air",
      "deliveryDate": "2023-05-30",
      "flowRef": "REF1",
      "delFlowRef": "D. REF1",
      "customerFlowRef": "BPO#01",
      "orderQty": 1000,
      "extra": 5,
      "sizeBreakupList": [
        { "serialNo": 1, "sizeGroup": "", "size": "S", "qty": 150 },
        { "serialNo": 2, "sizeGroup": "", "size": "M", "qty": 200 },
        { "serialNo": 3, "sizeGroup": "", "size": "L", "qty": 300 },
        { "serialNo": 4, "sizeGroup": "", "size": "XL", "qty": 200 },
        { "serialNo": 5, "sizeGroup": "", "size": "2XL", "qty": 150 }
      ],
      "departmentList": [
        { "id": 1, "name": "Cutting" },
        { "id": 2, "name": "Sewing" },
        { "id": 3, "name": "Finishing" }
      ]
    }
  ]
}
</pre>

## Delete FPO (v2)

```shell
curl "~/api/fpo?action=delete&externalOrderId=1000&fpo=FP-100" \
  -X DELETE \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <access_token>" \
```

This endpoint creates a factory production order.

### HTTP Request

`DELETE ~/api/fpo?action=<delete|cancel>externalOrderId=<External Order Id>&fpo=<FPO No>`

### URL Parameters

| Parameter       | Description                                                           |
|-----------------|-----------------------------------------------------------------------|
| action          | `delete`: Delete record, `cancel`: Cancel FPO without deleting record |
| externalOrderId | The external ID of parent Order                                       |
| fpo             | FPO Number to be deleted                                              |

## Schema - FPO (v2)

```json
{
  "fpo": "string",
  "unitId": "string",
  "fpoLevel": "BPO,COLOR",
  "flowInfoList": [
    {
      "externalId": "string",
      "productId": "long",
      "extProductId": "string",
      "style": "string",
      "color": "string",
      "inseam": "string",
      "destination": "string",
      "delMode": "string",
      "deliveryDate": "yyyy-MM-dd",
      "flowRef": "string",
      "delFlowRef": "string",
      "customerFlowRef": "string",
      "orderQty": "int",
      "extra": "double",
      "sizeBreakupList": [
        {
          "id": "long",
          "serialNo": "int",
          "sizeGroup": "string",
          "size": "string",
          "qty": "int"
        }
      ],
      "departmentList": [
        {
          "id": "long",
          "name": "string"
        }
      ]
    }
  ]
}
```

**FPO Table**

| Field    | Type   | Constraints | Description                                                                                    |
|----------|--------|-------------|------------------------------------------------------------------------------------------------|
| fpo      | String | Required    | Factory Production Order number                                                                |
| unitId   | String | Required    | Unit in which this order is planned                                                            |
| fpoLevel | Int    | Required    | Whether FPO is created at Color level or BPO/Delivery schedule level. Values: (`BPO`, `COLOR`) |

**FlowInfo Table**

| Field           | Type   | Constraints                                     | Description                                     |
|-----------------|--------|-------------------------------------------------|-------------------------------------------------|
| externalId      | String | Unique                                          | External ID                                     |
| flowRef         | String |                                                 | ERP Reference number at Color Level             |
| delFlowRef      | String |                                                 | Customer+ERP Reference number at Delivery Level |
| customerFlowRef | String |                                                 | Customer Reference  number at Color Level       |
| productId       | Long   | Required if External Product ID is not present  | Internal ID of Product                          |
| extProductId    | String | Required if Product ID is not present           | Internal ID of Product                          |
| style           | String | Required                                        | Style Name                                      |
| color           | String | Required                                        | Style Color                                     |
| inseam          | String |                                                 | Inseam                                          |
| destination     | String |                                                 | Destination                                     |
| delMode         | String |                                                 | Delivery Mode. Values: (`Air`, `Sea`, `Road`)   |
| deliveryDate    | Date   |                                                 | Delivery Date. Format: `yyyy-MM-dd`             |
| orderQty        | Int    | Required                                        | Order Qty in this flow                          |
| extra           | Float  |                                                 | Allowed Extra percent                           |

**Size Breakup Table**

| Field     | Type   | Constraints | Description            |
|-----------|--------|-------------|------------------------|
| id        | Long   | Primary Key | Internal ID            |
| serialNo  | Int    |             | Sequence of Size       |
| sizeGroup | String |             | Inseam if applicable   |
| size      | String | Required    | Size  Name             |
| qty       | Int    | Required    | Order qty in this size |

## Create FPO (v1)

```shell
curl "~/api/production-orders?externalOrderId=1000" \
  -X POST \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <access_token>" \
  -d '<JSON Payload>'
```

This endpoint creates a order.

### HTTP Request

`POST ~/api/production-orders?externalOrderId=<External Order Id>`

### URL Parameters

| Parameter       | Description                     |
|-----------------|---------------------------------|
| externalOrderId | The external ID of parent Order |

### JSON Payload

<pre class="center-column">
[
  {
    "externalId": "2000",
    "primaryUnitId": "unit1",
    "cancelled":false,
    "fpo": "FPO#200",
    "orderQty": 1000,
    "sizeBreakupList": [
        { "serialNo": 1, "sizeGroup": "", "size": "S", "qty": 150 },
        { "serialNo": 2, "sizeGroup": "", "size": "M", "qty": 200 },
        { "serialNo": 3, "sizeGroup": "", "size": "L", "qty": 300 },
        { "serialNo": 4, "sizeGroup": "", "size": "XL", "qty": 200 },
        { "serialNo": 5, "sizeGroup": "", "size": "2XL", "qty": 150 }
    ],
    "departmentList": [
      { "id": 1, "name": "Cutting" },
      { "id": 2, "name": "Sewing" },
      { "id": 3, "name": "Finishing" },
    ]
  },
  {
    "externalId": "2001",
    "primaryUnitId": "unit1",
    "cancelled":false,
    "fpo": "FPO#200",
    "orderQty": 1000,
    "sizeBreakupList": [
        { "serialNo": 1, "sizeGroup": "", "size": "S", "qty": 150 },
        { "serialNo": 2, "sizeGroup": "", "size": "M", "qty": 200 },
        { "serialNo": 3, "sizeGroup": "", "size": "L", "qty": 300 },
        { "serialNo": 4, "sizeGroup": "", "size": "XL", "qty": 200 },
        { "serialNo": 5, "sizeGroup": "", "size": "2XL", "qty": 150 }
    ],
    "departmentList": [
      { "id": 1, "name": "Cutting" },
      { "id": 2, "name": "Sewing" },
      { "id": 3, "name": "Finishing" },
    ]
  }
]
</pre>

## Schema - FPO (v1)

```json
[
  {
    "externalId": "string",
    "primaryUnitId": "string",
    "fpo": "string",
    "orderQty": "int",
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
```

**PO Table**

| Field         | Type   | Constraints | Description                                                 |
|---------------|--------|-------------|-------------------------------------------------------------|
| externalId    | String | Required    | External ID which was sent in FlowInfo while creating order |
| primaryUnitId | String | Required    | Unit in which this order is planned                         |
| fpo           | String |             | Factory Production Order number                             |
| orderQty      | Int    | Required    | Order Qty in this flow                                      |

**Size Breakup Table**

| Field     | Type   | Constraints | Description            |
|-----------|--------|-------------|------------------------|
| id        | Long   | Primary Key | Internal ID            |
| serialNo  | Int    |             | Sequence of Size       |
| sizeGroup | String |             | Inseam if applicable   |
| size      | String | Required    | Size  Name             |
| qty       | Int    | Required    | Order qty in this size |







