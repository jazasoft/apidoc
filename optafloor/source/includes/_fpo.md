# Factory Production Order

## Create FPO

```shell
curl "~/v1/api/external/fpo" \
  -X POST \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <access_token>" \
  -d '<JSON Payload>'
```

This endpoint creates a factory production order.

### HTTP Request

`POST ~/v1/api/external/fpo`

### JSON Payload

<pre class="center-column">
[
  {
    "externalIds": "1377-WHITE",
    "serialNo": 1,
    "poRef": "1377",
    "seasonId": 1,
    "buyerId": 1,
    "fpo": "BPO1::BPO2",
    "customerFlowRef": "BPO1",
    "flowRef": "",
    "productId": 1,
    "style": "A87",
    "styleNo": "",
    "color": "WHITE",
    "inseam": "32",
    "destination": "US",
    "delMode": "Air",
    "deliveryDate": "2024-06-20",
    "orderQty": 500,
    "sizeBreakupList": [
      { "serial": 1, "size": "S", "qty": 150 },
      { "serial": 2, "size": "M", "qty": 200 },
      { "serial": 3, "size": "L", "qty": 150 }
    ],
    "departmentList": [
      { "id": 1, "name": "Cutting" },
      { "id": 2, "name": "Sewing" },
      { "id": 3, "name": "Finishing" }
    ]
  },
  {
    "externalIds": "1377-BLACK",
    "serialNo": 2,
    "poRef": "1377",
    "seasonId": 1,
    "buyerId": 1,
    "fpo": "BPO1::BPO2",
    "customerFlowRef": "BPO2",
    "flowRef": "",
    "productId": 1,
    "style": "A87",
    "styleNo": "",
    "color": "BLACK",
    "inseam": "32",
    "destination": "UK",
    "delMode": "Air",
    "deliveryDate": "2024-06-20",
    "orderQty": 450,
    "sizeBreakupList": [
      { "serial": 1, "size": "S", "qty": 150 },
      { "serial": 2, "size": "M", "qty": 150 },
      { "serial": 3, "size": "L", "qty": 150 }
    ],
    "departmentList": [
      { "id": 1, "name": "Cutting" },
      { "id": 2, "name": "Sewing" },
      { "id": 3, "name": "Finishing" }
    ]
  }
]
</pre>


> The above command returns JSON structured like this:

```json
{
  "status": 200,
  "code": 200,
  "message": "Transaction successful"
}
```

## Delete  FPO

```shell
curl "~/v1/api/external/fpo?poRef=1377&fpo=BPO1::BPO2&inseam=32"
  -X DELETE
  -H "Authorization: Bearer <access_token>"
```

> The above command returns empty content with response status `204`

This endpoint deletes a specific Factory Production Order.

### HTTP Request

`DELETE ~/v1/api/external/fpo?poRef=<PO Ref>&fpo=<FPO>&inseam=<Inseam>`

### URL Parameters

| Parameter | Required | Description                     |
|-----------|----------|---------------------------------|
| poRef     | Yes      | PO Reference number             |
| fpo       | Yes      | Factory Production Order Number |
| inseam    | No       | Inseam                          |

## Schema - FPO - Factory Production

```json
{
  "id": "long",
  "externalIds": "string",
  "serialNo": "long",
  "poRef": "string",
  "seasonId": "long",
  "buyerId": "long",
  "productId": "long",
  "fpo": "string",
  "customerPoRef": "string",
  "flowRef": "string",
  "style": "string",
  "styleNo": "string",
  "color": "string",
  "inseam": "string",
  "destination": "string",
  "delMode": "string",
  "deliveryDate": "2024-06-20",
  "orderQty": "long",
  "desc": "string",
  "sizeBreakupList": [
    {
      "id": "long",
      "sizeGroup": "string",
      "serialNo": "int",
      "size": "string",
      "qty": "int"
    }
  ]
}
```

**Order Table**

| Field         | Type   | Constraints | Description                                              |
|---------------|--------|-------------|----------------------------------------------------------|
| id            | Long   | Primary Key | Internal ID                                              |
| externlIds    | string | Required    | Combination of some unique value which identify the flow |
| poRef         | String | Required    | Purchase Order Reference                                 |
| seasonId      | Long   | Required    | Internal ID of Season                                    |
| buyerId       | Long   | Required    | Internal ID of Buyer                                     |
| productId     | Long   | Required    | Internal ID of Product                                   |
| fpo           | String | Required    | Factory Production Order number                          |
| customerPoRef | String |             | Customer Flow Reference number                           |
| flowRef       | String |             | Flow Reference number                                    |
| style         | String | Required    | Style of the Order                                       |
| styleNo       | String |             | Style No of the order                                    |
| color         | String | Required    | Style Color                                              |
| inseam        | String |             | Inseam if available                                      |
| destination   | String |             | Destination of Order                                     |
| delMode       | String |             | Delivery Mode                                            |
| deliveryDate  | Date   |             | Delivery Date                                            |
| orderQty      | Long   | Required    | Order Qty of style                                       |
| desc          | Text   |             | description for Order                                    |

                                                                                  |

**Size Breakup Table**

| Field     | Type   | Constraints | Description            |
|-----------|--------|-------------|------------------------|
| id        | Long   | Primary Key | Internal ID            |
| serialNo  | Int    |             | Sequence of Size       |
| size      | String | Required    | Size  Name             |
| sizeGroup | String |             | Size Group Name        |
| qty       | Int    | Required    | Order qty in this size |
