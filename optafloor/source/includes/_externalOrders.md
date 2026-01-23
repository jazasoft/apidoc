# External Orders

## Create External Order

```shell
curl "~/v1/api/external/orders" \
  -X POST \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <access_token>" \
  -d '<JSON Payload>'
```

This endpoint creates an order.

### HTTP Request

`POST ~/v1/api/external/orders`

### JSON Payload

<pre class="center-column">
{
  "externalId": "OEID-1",
  "poRef": "CIPL-03205-2",
  "buyerId": 1017,
  "flowInfoList": [
    {
      "externalId": "FIEID-1",
      "productId": 2,
      "customerFlowRef": "P0821-436022-001",
      "flowRef": "",
      "style": "W S COTTON EASY PANT",
      "styleNo": "271H134A-Stripe",
      "color": "#01 OFF WHITE_2",
      "inseam": "34 L",
      "destination": "SINGAPORE",
      "delMode": "",
      "deliveryDate": "11/5/2020",
      "exFactoryDate": "2025-11-01",
      "washType": "With Wash",
      "wrinkleType": "Without WrinkleFree",
      "customField1": "CIPL-03205-P0821-436022-001-Singapore-01 Off White (Stripe)+69 Navy (Stripe)|W/s Cotton Pant",
      "sizeBreakupList": [
        {
          "serial": 1,
          "size": "XS",
          "sizeGroup": "N/A",
          "qty": 9
        },
        {
          "serial": 1,
          "size": "XS",
          "sizeGroup": "N/A",
          "qty": 9
        },
        {
          "serial": 2,
          "size": "S",
          "sizeGroup": "N/A",
          "qty": 568
        },
        {
          "serial": 3,
          "size": "M",
          "sizeGroup": "N/A",
          "qty": 568
        },
        {
          "serial": 4,
          "size": "L",
          "sizeGroup": "N/A",
          "qty": 320
        },
        {
          "serial": 5,
          "size": "XL",
          "sizeGroup": "N/A",
          "qty": 320
        },
        {
          "serial": 6,
          "size": "XXL",
          "sizeGroup": "N/A",
          "qty": 27
        },
        {
          "serial": 7,
          "size": "XXXL",
          "sizeGroup": "N/A",
          "qty": 18
        }
      ]
    },
    {
      "externalId": "FIEID-2",
      "productId": 2,
      "customerFlowRef": "P0821-436022-001",
      "flowRef": "",
      "style": "W S COTTON EASY PANT",
      "styleNo": "271H134A-Stripe",
      "color": "#69 NAVY",
      "inseam": "34 L",
      "destination": "SINGAPORE",
      "delMode": "",
      "deliveryDate": "11/5/2020",
      "exFactoryDate": "2025-11-01",
      "washType": "With Wash",
      "wrinkleType": "Without WrinkleFree",
      "customField1": "CIPL-03205-P0821-436022-001-Singapore-01 Off White (Stripe)+69 Navy (Stripe)|W/s Cotton Pant",
      "sizeBreakupList": [
        {
          "serial": 1,
          "size": "XS",
          "sizeGroup": "N/A",
          "qty": 9
        },
        {
          "serial": 2,
          "size": "S",
          "sizeGroup": "N/A",
          "qty": 584
        },
        {
          "serial": 3,
          "size": "M",
          "sizeGroup": "N/A",
          "qty": 776
        },
        {
          "serial": 4,
          "size": "L",
          "sizeGroup": "N/A",
          "qty": 808
        },
        {
          "serial": 5,
          "size": "XL",
          "sizeGroup": "N/A",
          "qty": 820
        },
        {
          "serial": 6,
          "size": "XXL",
          "sizeGroup": "N/A",
          "qty": 27
        },
        {
          "serial": 7,
          "size": "XXXL",
          "sizeGroup": "N/A",
          "qty": 18
        }
      ]
    }
  ]
}
</pre>

## Update External Order

```shell
curl "~/v1/api/external/orders?externalId=OEID-1" \
  -X PUT \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <access_token>" \
  -d '<JSON Payload>'
```

This endpoint creates an order.

### HTTP Request

`PUT ~/v1/api/external/orders?externalId=<External ID>`

### URL Parameters

| Parameter  | Description                                                    |
|------------|----------------------------------------------------------------|
| externalId | External Id at header level which was sent during Order create |

### JSON Payload

<pre class="center-column">
{
  "externalId": "OEID-1",
  "poRef": "CIPL-03205-2",
  "buyerId": 1017,
  "flowInfoList": [
    {
      "externalId": "FIEID-1",
      "productId": 2,
      "customerFlowRef": "P0821-436022-001",
      "flowRef": "",
      "style": "W S COTTON EASY PANT",
      "styleNo": "271H134A-Stripe",
      "color": "#01 OFF WHITE_2",
      "inseam": "34 L",
      "destination": "SINGAPORE",
      "delMode": "",
      "deliveryDate": "11/5/2020",
      "exFactoryDate": "2025-11-01",
      "washType": "With Wash",
      "wrinkleType": "Without WrinkleFree",
      "customField1": "CIPL-03205-P0821-436022-001-Singapore-01 Off White (Stripe)+69 Navy (Stripe)|W/s Cotton Pant",
      "sizeBreakupList": [
        {
          "serial": 1,
          "size": "XS",
          "sizeGroup": "N/A",
          "qty": 9
        },
        {
          "serial": 1,
          "size": "XS",
          "sizeGroup": "N/A",
          "qty": 9
        },
        {
          "serial": 2,
          "size": "S",
          "sizeGroup": "N/A",
          "qty": 568
        },
        {
          "serial": 3,
          "size": "M",
          "sizeGroup": "N/A",
          "qty": 568
        },
        {
          "serial": 4,
          "size": "L",
          "sizeGroup": "N/A",
          "qty": 320
        },
        {
          "serial": 5,
          "size": "XL",
          "sizeGroup": "N/A",
          "qty": 320
        },
        {
          "serial": 6,
          "size": "XXL",
          "sizeGroup": "N/A",
          "qty": 27
        },
        {
          "serial": 7,
          "size": "XXXL",
          "sizeGroup": "N/A",
          "qty": 18
        }
      ]
    },
    {
      "externalId": "FIEID-2",
      "productId": 2,
      "customerFlowRef": "P0821-436022-001",
      "flowRef": "",
      "style": "W S COTTON EASY PANT",
      "styleNo": "271H134A-Stripe",
      "color": "#69 NAVY",
      "inseam": "34 L",
      "destination": "SINGAPORE",
      "delMode": "",
      "deliveryDate": "11/5/2020",
      "exFactoryDate": "2025-11-01",
      "washType": "With Wash",
      "wrinkleType": "Without WrinkleFree",
      "customField1": "CIPL-03205-P0821-436022-001-Singapore-01 Off White (Stripe)+69 Navy (Stripe)|W/s Cotton Pant",
      "sizeBreakupList": [
        {
          "serial": 1,
          "size": "XS",
          "sizeGroup": "N/A",
          "qty": 9
        },
        {
          "serial": 2,
          "size": "S",
          "sizeGroup": "N/A",
          "qty": 584
        },
        {
          "serial": 3,
          "size": "M",
          "sizeGroup": "N/A",
          "qty": 776
        },
        {
          "serial": 4,
          "size": "L",
          "sizeGroup": "N/A",
          "qty": 808
        },
        {
          "serial": 5,
          "size": "XL",
          "sizeGroup": "N/A",
          "qty": 820
        },
        {
          "serial": 6,
          "size": "XXL",
          "sizeGroup": "N/A",
          "qty": 27
        },
        {
          "serial": 7,
          "size": "XXXL",
          "sizeGroup": "N/A",
          "qty": 18
        }
      ]
    }
  ]
}
</pre>

## Schema - External Order

```json
{
  "externalId": "string",
  "buyerId": "long",
  "seasonId": "long",
  "poRef": "string",
  "customerPoRef": "string",
  "desc": "string",
  "flowInfoList": [
    {
      "id": "long",
      "flowRef": "string",
      "serialNo": "int",
      "productId": "long",
      "style": "string",
      "color": "string",
      "inseam": "string",
      "destination": "string",
      "delMode": "string",
      "deliveryDate": "yyyy-MM-dd",
      "exFactoryDate": "yyyy-MM-dd",
      "washType": "string",
      "wrinkleType": "string",
      "orderQty": "int",
      "sizeBreakupList": [
        {
          "id": "long",
          "serialNo": "int",
          "size": "string",
          "qty": "int"
        }
      ]
    }
  ]
}
```

**Order Table**

| Field      | Type | Constraints | Description              |
|------------|------|-------------|--------------------------|
| externalId | Text | Unique Key  | External ID              |
| poRef      | Text | Required    | Purchase Order Reference |
| buyerId    | Long |             | Internal ID of Buyer     |
| seasonId   | Long |             | Internal ID of Season    |
| desc       | Text |             | description for Order    |

**FlowInfo Table**

| Field         | Type | Constraints | Description                          |
|---------------|------|-------------|--------------------------------------|
| externalId    | Text | Unique Key  | External ID                          |
| serialNo      | Long |             | Sequence                             |
| flowRef       | Text |             | Flow Reference                       |
| productId     | Long | Required    | Internal ID of Product               |
| style         | Text | Required    | Style Name                           |
| color         | Text | Required    | Style Color                          |
| inseam        | Text |             | Inseam                               |
| destination   | Text |             | Destination                          |
| delMode       | Text |             | Delivery Mode                        |
| deliveryDate  | Date | Required    | Delivery Date. Format: `yyyy-MM-dd`  |
| exFactoryDate | Date |             | ExFactory Date. Format: `yyyy-MM-dd` |
| washType      | Text |             | Wash Type                            |
| wrinkleType   | Text |             | Wrinkle Type                         |
| orderQty      | Int  | Required    | Order Qty in this flow               |

**Size Breakup Table**

| Field    | Type   | Constraints | Description            |
|----------|--------|-------------|------------------------|
| id       | Long   | Primary Key | Internal ID            |
| serialNo | Int    |             | Sequence of Size       |
| size     | String | Required    | Size  Name             |
| qty      | Int    | Required    | Order qty in this size |

