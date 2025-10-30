# Device

## Read Device

```shell
curl "~/v1/api/devices/by-device-id?deviceId=3c794f3239bc62e1" \
  -X GET \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <access_token>" \  
```

This endpoint fetches device info

> The above command returns JSON structured like this:

```json
{
  "id": 100,
  "deviceId": "3c794f3239bc62e1",
  "brand": "Lenovo",
  "deviceType": "Tablet",
  "model": "TB310FU",
  "osName": "Android",
  "osVersion": "13",
  "platformApiLevel": 33,
  "ram": 2048,
  "active": true
}
```

### HTTP Request

`GET ~/v1/api/devices/by-device-id?deviceId=<Device ID>`


### URL Parameters

| Parameter | Description |
|-----------|-------------|
| deviceId  | Device ID   |

## Register Device

```shell
curl "~/v1/api/devices" \
  -X POST \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <access_token>" \
  -d '<JSON Payload>'
```

This endpoint registers a new device.

### HTTP Request

`POST ~/v1/api/devices`

### JSON Payload

<pre class="center-column">

{
    "deviceId": "3c794f3239bc62e1",
    "brand": "Lenovo",
    "deviceType": "Tablet",
    "model": "TB310FU",
    "osName": "Android",
    "osVersion": "13",
    "platformApiLevel": 33,
    "ram": 2048,
    "active": true
}
</pre>

> The above command returns JSON structured like this:

```json
{
  "id": 100,
  "deviceId": "3c794f3239bc62e1",
  "brand": "Lenovo",
  "deviceType": "Tablet",
  "model": "TB310FU",
  "osName": "Android",
  "osVersion": "13",
  "platformApiLevel": 33,
  "ram": 2048,
  "active": true
}
```
