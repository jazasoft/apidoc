# External Roll

## Fetch Roll QC

```shell
curl "~/api/external/rolls/qc?search=qcAt=ge=1707762600000" \
  -X GET \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <access_token>" \
```

This endpoint updates QC for Roll in OptaCut from External System.

> The above command returns JSON structured like this:

```json
[
  {
    "invoiceExternalId": "110",
    "fabricItemExternalId": "210",
    "itemCode": "F000002337",
    "itemColor": "BLACK",
    "fpo": "FPO#100",
    "grn": "GRN#100",
    "width": 145.0,
    "uomWidth": "centimeter",
    "uomLength": "meter",
    "qcDate": "2024-02-13",
    "checkQty": 429.0,
    "passQty": 328.0,
    "rejectQty": 101.2,
    "rollList": [
      {
        "factoryRollNo": "INV-100/5477",
        "supplierRollNo": "5477",
        "supplierLength": 129.0,
        "inspectedLength": 127.5,
        "shade": "A",
        "csv": "No",
        "qcStatus": "Pass"
      },
      {
        "factoryRollNo": "INV-100/5479",
        "supplierRollNo": "5479",
        "supplierLength": 100.0,
        "inspectedLength": 101.2,
        "shade": "C",
        "qcStatus": "Fail"
      },
      {
        "factoryRollNo": "INV-100/5480",
        "supplierRollNo": "5480",
        "supplierLength": 200.0,
        "inspectedLength": 200.5,
        "shade": "D",
        "csv": "No",
        "qcStatus": "Pass"
      }
    ]
  },
  {
    "invoiceExternalId": "111",
    "fabricItemExternalId": "211",
    "itemCode": "F000002337",
    "itemColor": "BLACK",
    "fpo": "FPO#101",
    "grn": "GRN#101",
    "width": 145.0,
    "uomWidth": "centimeter",
    "uomLength": "meter",
    "qcDate": "2024-02-13",
    "checkQty": 290.0,
    "passQty": 287.5,
    "rejectQty": 0.0,
    "rollList": [
      {
        "factoryRollNo": "INV-101/5483",
        "supplierRollNo": "5483",
        "supplierLength": 114.0,
        "inspectedLength": 110.5,
        "warpShrPercent": 2.5,
        "weftShrPercent": 1.5,
        "shade": "A",
        "csv": "Yes",
        "qcStatus": "Pass"
      },
      {
        "factoryRollNo": "INV-101/5484",
        "supplierRollNo": "5484",
        "supplierLength": 176.0,
        "inspectedLength": 177.0,
        "warpShrPercent": 1.0,
        "weftShrPercent": 1.6,
        "shade": "B",
        "csv": "Yes",
        "qcStatus": "Pass"
      }
    ]
  }
]
```

### HTTP Request

`GET ~/api/external/rolls/qc?search=<Search Query>`

### URL Parameters

| Parameter | Description                                                                                       |
|-----------|---------------------------------------------------------------------------------------------------|
| search    | Search Query. e.g. `qcAt=ge=1707762600000` for `qcAt` greater than equal to timestamp (in millis) |

## Update Roll QC by GRN

```shell
curl "~/api/external/rolls/qc/by-grn?externalInvoiceId=1000" \
  -X PUT \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <access_token>" \
  -d '<JSON Payload>'
```

This endpoint updates QC for Roll in OptaCut from External System.

### HTTP Request

`PUT ~/api/external/rolls/qc/by-grn?externalOrderId=<External Order Id>`

### URL Parameters

| Parameter         | Description                |
|-------------------|----------------------------|
| externalInvoiceId | The external ID of Invoice |

### JSON Payload

<pre class="center-column">
[
  {
    "rollNo": "INV-100/R100",
    "supplierRollNo": "R100",
    "length": 100.2,
    "weight": null,
    "blanketQty": 0,
    "width": 144,
    "finishedWidth": null,
    "gsm": null,
    "shade": "A",
    "csv": "Grade 3",
    "lengthShrinkagePercent": -2.5,
    "widthShrinkagePercent": -1.5,
    "lengthPatternValue": 2.0,
    "widthPatternValue": 1.5,
    "patternNo": "P1",
    "skewnessValue": 2.0,
    "skewnessGroup": "Less than 3.0%",
    "consignment": "1",
    "qcStatus": "Pass"
  },
  {
    "rollNo": "INV-100/R101",
    "supplierRollNo": "R100",
    "length": null,
    "weight": 20.5,
    "blanketQty": 0,
    "width": 144.2,
    "finishedWidth": 145.5,
    "gsm": 150,
    "shade": "A",
    "csv": "Grade 3",
    "lengthShrinkagePercent": -2.5,
    "widthShrinkagePercent": -1.5,
    "lengthPatternValue": 2.0,
    "widthPatternValue": 1.5,
    "patternNo": "P1",
    "skewnessValue": 2.0,
    "skewnessGroup": "Less than 3.0%",
    "consignment": "1",
    "qcStatus": "Pass"
  }
]
</pre>

## Schema - Update Roll QC by GRN

```json
[
  {
    "rollNo": "string",
    "supplierRollNo": "string",
    "length": "double",
    "weight": "double",
    "blanketQty": "int",
    "width": "double",
    "finishedWidth": "double",
    "gsm": "int",
    "shade": "string",
    "csv": "string",
    "lengthShrinkagePercent": "double",
    "widthShrinkagePercent": "double",
    "lengthPatternValue": "double",
    "widthPatternValue": "double",
    "patternNo": "string",
    "skewnessValue": "double",
    "skewnessGroup": "string",
    "consignment": "string",
    "qcStatus": "Pass|Fail"
  }
]
```
**Roll Table**

| Field                  | Type   | Constraints      | Description                                                                         |
|------------------------|--------|------------------|-------------------------------------------------------------------------------------|
| rollNo                 | String | Required         | Factory Roll Number                                                                 |
| supplierRollNo         | String |                  | Supplier Roll Number                                                                |
| length                 | Double | Required (Woven) | Inspected Length                                                                    |
| weight                 | Double | Required (Knits) | Inspected Weight                                                                    |
| blanketQty             | Double |                  | Blanket Qty                                                                         |
| width                  | Double | Required         | Cuttable Width                                                                      |
| finishedWidth          | Double | Required (Knits) | Finished Width                                                                      |
| gsm                    | Double | Required (Knits) | GSM                                                                                 |
| shade                  | String | Required         | Roll Shade                                                                          |
| csv                    | String | Required         | Roll CSV values. Accepted values - (`Yes`, `No`, `Grade 3`, `Grade 3-4`, `Grade 4`) |
| lengthShrinkagePercent | Double |                  | Length wise shrinkage value                                                         |
| widthShrinkagePercent  | Double |                  | Width wise shrinkage value                                                          |
| lengthPatternValue     | Double |                  | Length wise pattern value                                                           |
| widthPatternValue      | Double |                  | Width wise pattern value                                                            |
| patternNo              | String |                  | Pattern No                                                                          |
| skewnessValue          | Double |                  | Skewness value                                                                      |
| skewnessGroup          | String |                  | Skewness Group                                                                      |
| consignment            | String |                  | Consignment Number                                                                  |
| qcStatus               | String | Required         | QC Status of Roll. Accepted values - (`Pass`, `Fail`)                               |

## Update Roll QC by Order

```shell
curl "~/api/external/rolls/qc/by-order?externalOrderId=1000" \
  -X PUT \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <access_token>" \
  -d '<JSON Payload>'
```

This endpoint updates QC for Roll in OptaCut from External System.

### HTTP Request

`PUT ~/api/external/rolls/qc/by-order?externalOrderId=<External Order Id>`

**Note:** URL has been changed from `~/api/external-roll/qc` to `~/api/external/rolls/qc`. Old API will continue to work
but will be removed in the future. Please, update URL to avoid breaking API

### URL Parameters

| Parameter       | Description              |
|-----------------|--------------------------|
| externalOrderId | The external ID of Order |

### JSON Payload

<pre class="center-column">
{
  "productId": 1,
  "style": "Black",
  "styleColor": "A6",
  "part": "Shell",
  "placement": "Entire Body",
  "fabricItemList": [
    {
      "externalInvoiceId": "100",
      "externalFabricItemId": "200",
      "fabColor": "Blue",
      "rollList": [
        {
          "factoryRollNo": "INV-100/R100",
          "length": 100.2,
          "cuttableWidth": 144,
          "shade": "A",
          "csv": "Grade 3",
          "lengthShrinkagePercent": -2.5,
          "widthShrinkagePercent": -1.5,
          "lengthPatternValue": 2.0,
          "widthPatternValue": 1.5,
          "patternNo": "P1",
          "skewnessValue": 2.0,
          "skewnessGroup": "Less than 3.0%",
          "consignment": "1",
          "qcStatus": "Pass"
        },
        {
          "factoryRollNo": "INV-100/R101",
          "length": 110.6,
          "cuttableWidth": 145,
          "shade": "B",
          "csv": "Grade 3",
          "lengthShrinkagePercent": -2.1,
          "widthShrinkagePercent": -1.7,
          "lengthPatternValue": 2.0,
          "widthPatternValue": 1.5,
          "patternNo": "P1",
          "skewnessValue": 5.0,
          "skewnessGroup": "Between 3.0% to 6.0%",
          "consignment": "1",
          "qcStatus": "Pass"
        }
      ]
    }
  ]
}
</pre>

## Schema - Update Roll QC

```json
{
  "productId": "long",
  "style": "string",
  "styleColor": "string",
  "part": "string",
  "placement": "string",
  "fabricItemList": [
    {
      "externalInvoiceId": "string",
      "externalFabricItemId": "string",
      "fabColor": "string",
      "rollList": [
        {
          "factoryRollNo": "string",
          "length": "double",
          "cuttableWidth": "double",
          "shade": "string",
          "csv": "string",
          "lengthShrinkagePercent": "double",
          "widthShrinkagePercent": "double",
          "lengthPatternValue": "double",
          "widthPatternValue": "double",
          "patternNo": "string",
          "skewnessValue": "double",
          "skewnessGroup": "string",
          "consignment": "string",
          "qcStatus": "Pass|Fail"
        }
      ]
    }
  ]
}
```

**FlowInfo Table**

| Field      | Type   | Constraints | Description                                                              |
|------------|--------|-------------|--------------------------------------------------------------------------|
| productId  | Long   | Required    | Product Id which was sent in FlowInfo while creating order               |
| style      | String | Required    | Style which was sent in FlowInfo while creating order                    |
| styleColor | String | Required    | Style/FG Color which was sent in FlowInfo while creating order           |
| part       | Int    | Required    | PartName which was sent in Fabric BOM details while creating order       |
| placement  | Int    | Required    | Part Placement which was sent in Fabric BOM details while creating order |

**Fabric Item Table**

| Field                | Type   | Constraints | Description                                                            |
|----------------------|--------|-------------|------------------------------------------------------------------------|
| externalInvoiceId    | String | Required    | External Invoice ID which was sent during GRN at invoice level         |
| externalFabricItemId | String | Required    | External Fabric Item ID which was sent during GRN at Fabric Item levle |
| fabColor             | String | Required    | Fabric Color                                                           |
| size                 | String | Required    | Size  Name                                                             |
| qty                  | Int    | Required    | Order qty in this size                                                 |

**Roll Table**

| Field                  | Type   | Constraints | Description                                                                         |
|------------------------|--------|-------------|-------------------------------------------------------------------------------------|
| factoryRollNo          | String | Required    | Factory Roll Number                                                                 |
| length                 | Double | Required    | Inspected Length                                                                    |
| cuttableWidth          | Double |             | Cuttable Width                                                                      |
| shade                  | String |             | Roll Shade                                                                          |
| csv                    | String |             | Roll CSV values. Accepted values - (`Yes`, `No`, `Grade 3`, `Grade 3-4`, `Grade 4`) |
| lengthShrinkagePercent | Double |             | Length wise shrinkage value                                                         |
| widthShrinkagePercent  | Double |             | Width wise shrinkage value                                                          |
| lengthPatternValue     | Double |             | Length wise pattern value                                                           |
| widthPatternValue      | Double |             | Width wise pattern value                                                            |
| patternNo              | String |             | Pattern No                                                                          |
| skewnessValue          | Double |             | Skewness value                                                                      |
| skewnessGroup          | String |             | Skewness Group                                                                      |
| consignment            | String |             | Consignment Number                                                                  |
| qcStatus               | String |             | QC Status of Roll. Accepted values - (`Pass`, `Fail`)                               |

## Lock Roll QC

```shell
curl "~/api/external/rolls/lock-qc" \
  -X PUT \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <access_token>" \
  -d '<JSON Payload>'
```

This endpoint Locks Roll QC in OptaCut

### HTTP Request

`PUT ~/api/external/rolls/lock-qc`

### JSON Payload

<pre class="center-column">
{
  "externalId": "TXN/1000",
  "fabricItemExternalId": "210",
  "rollList": [
    {
      "factoryRollNo": "INV-100/5477"
    },
    {
      "factoryRollNo": "INV-100/5479"
    },
    {
      "factoryRollNo": "INV-100/5480"
    }
  ]
}
</pre>

## Schema - Lock Roll QC

```json
{
  "externalId": "string",
  "fabricItemExternalId": "string",
  "rollList": [
    {
      "factoryRollNo": "string"
    }
  ]
}
```

**Table**

| Field                | Type   | Constraints | Description                                    |
|----------------------|--------|-------------|------------------------------------------------|
| externalId           | String |             | Transaction number of External System (if any) |
| fabricItemExternalId | String | Required    | External ID of Fabric Item                     |
| factoryRollNo        | String | Required    | Factory Roll Number                            |

## Roll RE-QC

```shell
curl "~/api/external/rolls/re-qc" \
  -X PUT \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <access_token>" \
  -d '<JSON Payload>'
```

This endpoint marks already QCied roll in OptaCut for Re-QC.

### HTTP Request

`PUT ~/api/external/rolls/re-qc`

**Note:** URL has been changed from `~/api/external-roll/re-qc` to `~/api/external/rolls/re-qc`. Old API will continue
to work but will be removed in the future. Please, update URL to avoid breaking API

Re-QC API accepts on of two Payload Structure

### JSON Payload 1

<pre class="center-column">
{
  "externalId": "100",
  "fabricItemList": [
    {
      "externalId": "200",
      "fabricId": 1,
      "color": "Blue",
      "colorCode": "Blue,
      "colorShade": null,
      "fpo": "FPO#100",
      "grn": "GRN#100",
      "supplierRollList": [
        {
          "factoryRollNo": "INV-100/R100"
        },
        {
          "factoryRollNo": "INV-100/R101"
        }
      ]
    }
  ]
}
</pre>

### JSON Payload 2

<pre class="center-column">
{
  "fabricItemExternalId": "210",
  "rollList": [
    {
      "factoryRollNo": "INV-100/5477"
    },
    {
      "factoryRollNo": "INV-100/5479"
    },
    {
      "factoryRollNo": "INV-100/5480"
    }
  ]
}
</pre>

## Schema - Roll Re-QC

```json
{
  "externalId": "string",
  "fabricItemList": [
    {
      "externalId": "string",
      "fabricId": "long",
      "color": "string",
      "colorCode": "string",
      "colorShade": "string",
      "fpo": "string",
      "grn": "string",
      "supplierRollList": [
        {
          "factoryRollNo": "string"
        }
      ]
    }
  ]
}
```

Schema of invoice entity

**Invoice Table**

| Field      | Type   | Constraints | Description             |
|------------|--------|-------------|-------------------------|
| externalId | String | Required    | External ID  of Invoice |

**Fabric Item Table**

| Field      | Type   | Constraints | Description                           |
|------------|--------|-------------|---------------------------------------|
| externalId | String | Required    | RE-QC Transaction Number              |
| fabricId   | Long   | Required    | Fabric Internal ID                    |
| color      | String | Required    | Fabric Color                          |
| colorCode  | String | Required    | Fabric Color Code                     |
| colorShade | String |             | Fabric Color Shade (e.g. Light, Dark) |
| fpo        | String | Required    | Fabric Purchase Order Number          |
| grn        | String | Required    | GRN Number                            |

**SupplierRoll Table**

| Field         | Type   | Constraints | Description                  |
|---------------|--------|-------------|------------------------------|
| factoryRollNo | String | Required    | Factory/Internal Roll Number |

## Roll Splitting

```shell
curl "~/api/external/rolls/splitting" \
  -X POST \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <access_token>" \
  -d '<JSON Payload>'
```

This endpoint can be used for splitting roll.

### HTTP Request

`POST ~/api/external/rolls/splitting`

### URL Parameters

| Parameter | Description                                                                    |
|-----------|--------------------------------------------------------------------------------|
| action    | `default`: Normal Splitting, `return`: Splitting while returning issued fabric |

### JSON Payload

<pre class="center-column">
{
  "originalFactoryRollNo": "INV-100/R100"
  "factoryRollNo": "INV-100/R100/1",
  "originalLength": 120.5,
  "splitLength": 30.0
}
</pre>
