## GET /v2/fleet/driver/&lt;fleetDriverId&gt;/declared-conviction/&lt;declaredConvictionId&gt;/

### Example response

HTTP 200

```
{
    "status": "OK",
    "declaredConvictions": [
        {
            "id": 12,
            "convictionDate": "2019-10-10T00:00:00+00:00",
            "convictionType": "N001"
        },
        {
            "id": 13,
            "convictionDate": "2019-10-10T00:00:00+00:00",
            "convictionType": "N001"
        }
    ]
}
```

### Example error

HTTP 404

```
{
    "status": "NOK",
    "error": "INVALID_DATA",
    "message": "Invalid data format",
    "detail": {
        "driver": [
            "Driver does not exist"
        ]
    }
}
```

## POST /v2/fleet/driver/&lt;fleetDriverId&gt;/declared-conviction/

### Request Body

| Key | Type | Required | Notes |
| --- | --- | --- | --- |
| convictionDate | iso-8601 string | yes |  |
| convictionType | string | yes | The type of conviction as defined by the ABI code list, see definition list |

### Example response

HTTP 201

```
{
    "status": "OK",
    "declaredConviction": {
        "convictionDate": "2019-10-10T00:00:00+00:00",
        "id": 13,
        "convictionType": "N001"
    }
}
```

### Example response

HTTP 404

```
{
    "status": "NOK",
    "error": "INVALID_DATA",
    "message": "Invalid data format",
    "detail": {
        "driver": [
            "Driver does not exist"
        ]
    }
}
```

## DELETE /v2/fleet/driver/&lt;fleetDriverId&gt;/declared-conviction/&lt;declaredConvictionId&gt;/

### Example response

HTTP 200

```
{
    "status": "OK"
}
```
