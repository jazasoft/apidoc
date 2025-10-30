# RFID

## RFID - Read Current Status

```shell
curl "~/v1/api/rfid?lineId=1&userId=100" \
  -X GET \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <access_token>" \
  -d '<JSON Payload>'
```

Get call to fetch current stats of user

### HTTP Request

`GET ~/v1/api/rfid?lineId=<LineId>&userId=<UserId>`

### URL Parameters

| Parameter | Description            |
|-----------|------------------------|
| lineId    | Line ID                |
| userId    | User ID                |

> The above command returns JSON structured like this:

```json
{
  "userId": 1,
  "user": "Akash Kumar",
  "employeeId": "55555",
  "lineId": 1,
  "lineName": "Line 1",
  "operationList": [
    {
      "name": "Operation 1",
      "code": "F001",
      "description": ""
    },
    {
      "name": "Operation 2",
      "code": "F002",
      "description": ""
    }
  ],
  "orderId": 1000,
  "orderFlowId": 20000,
  "buyer": "GANT",
  "style": "A6",
  "flowLabel": "T/100 -> A6 -> Black",
  "output": 500,
  "target": 600,
  "hourlyTarget": 90,
  "targetDifference": -100,
  "efficiency": 75.1,
  "wip": 80,
  "downtime": 15.5
}
```



## RFID - Material Scan

```shell
curl "~/v1/api/rfid" \
  -X POST \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <access_token>" \
  -d '<JSON Payload>'
```

Scan Bundle/Piece RFID Tag to punch user output

### HTTP Request

`POST ~/v1/api/rfid`

### JSON Payload

<pre class="center-column">
{
  "tag": "Bundle/Piece RFID TAG Value",
  "userId": 1,
  "lineId": 1,
  "machineId": 100,
  "deviceId": 100
}
</pre>

> The above command returns JSON structured like this:

```json
{
  "tagType": "BUNDLE|PIECE",
  "userId": 1,
  "user": "Akash Kumar",
  "employeeId": "55555",
  "lineId": 1,
  "lineName": "Line 1",
  "operationList": [
    {
      "name": "Operation 1",
      "code": "F001",
      "description": ""
    },
    {
      "name": "Operation 2",
      "code": "F002",
      "description": ""
    }
  ],
  "orderId": 1000,
  "orderFlowId": 20000,
  "buyer": "GANT",
  "style": "A6",
  "flowLabel": "T/100 -> A6 -> Black",
  "output": 500,
  "target": 600,
  "hourlyTarget": 90,
  "targetDifference": -100,
  "efficiency": 75.1,
  "wip": 80,
  "downtime": 15.5
}
```

## RFID - Line Scan

```shell
curl "~/v1/api/rfid" \
  -X POST \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <access_token>" \
  -d '<JSON Payload>'
```

Scan Line RFID Tag to read line info

### HTTP Request

`POST ~/v1/api/rfid`

### JSON Payload

<pre class="center-column">
{
  "tag": "Line RFID TAG Value"
}
</pre>

> The above command returns JSON structured like this:

```json
{
  "tagType": "LINE",
  "lineId": 1,
  "linenName": "Line 1",
  "departmentId": 3,
  "departmentName": "Sewing"
}
```

## RFID - Machine Scan

```shell
curl "~/v1/api/rfid" \
  -X POST \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <access_token>" \
  -d '<JSON Payload>'
```

Scan Machine RFID Tag to read Machine info

### HTTP Request

`POST ~/v1/api/rfid`

### JSON Payload

<pre class="center-column">
{
  "tag": "Machine RFID TAG Value"
}
</pre>

> The above command returns JSON structured like this:

```json
{
  "tagType": "MACHINE",
  "machineId": 100,
  "machineName": "Machine 100",
  "machineTypeId": 3,
  "machineType": "SNLS"
}
```

## RFID - User Login

```shell
curl "~/v1/api/rfid" \
  -X POST \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <access_token>" \
  -d '<JSON Payload>'
```

Scan User RFID Tag to Login

### HTTP Request

`POST ~/v1/api/rfid`

### JSON Payload

<pre class="center-column">
{
  "tag": "User RFID TAG Value"
}
</pre>

> The above command returns JSON structured like this:

```json
{
  "tagType": "USER",
  "userId": 1,
  "employeeId": "55555",
  "employeeName": "Akash Kumar",
  "roles": ["operator"],
  "token": "eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCJ9.eyJmdWxsX25hbWUiOiJNZCBaYWhpZCBSYXphIiwidXNlcl9pZCI6MSwidXNlcl9uYW1lIjoiemFoaWQ3MjkyIiwic2NvcGUiOlsicmVhZCIsIndyaXRlIl0sImV4cCI6MTc1MDQ3MzM1NCwiYXV0aG9yaXRpZXMiOlsiUk9MRV9tYXN0ZXIiXSwianRpIjoiaWFSUzczR2RZZkEzT2h3M3ZIdU9IOGdWZFBvIiwidGVuYW50IjoibGFndW5hX3Rlc3QiLCJjbGllbnRfaWQiOiJjbGllbnQifQ.C8lwERQotdu1C_Bwc9aRt0li91O6Zulr31mHnJJFXsd4iY7MLlUorMszwUDZpuljorLpHk0HuLynE95CTQZUIjuP1dMTXs8qwFK3fT052my9mz2QIRrb31I7NLP65BHOd5eKL_3qYBB0C8tU7zd2jQVp13ilfn_UmYbeV55TjSlb6C5firKDiXsy8thtCBjSJfuf5UpwJxh4biMk1S5MAL8KulsDYekyeacdoPKxW0AS0f1sKYbr6dn4aR9T7NOsBnc6gJhzeIHzqZboc2eAyU3rki9wAMMWoyhn_a7Y9nXzLdyIavu1Nb4YZd_v8wRutGtmDjRIr3x_GtNWS4vLPA"
}
```
