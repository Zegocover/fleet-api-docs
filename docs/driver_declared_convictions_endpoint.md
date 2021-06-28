## Driver Declared Convictions


### Get Driver Declared Conviction

`GET /v2/fleet/driver/:fleetDriverId/declared-conviction/:declaredConvictionId/`

##### Example response

HTTP 200

```
{
    "status": "OK",
    "declaredConvictions": [
        {
            "id": "fltcon_ow3b6pkhtjac7h7qgucggqmbha",
            "convictionDate": "2019-10-10T00:00:00+00:00",
            "convictionType": "N001"
        },
        {
            "id": "fltcon_ow3b6pkhtjac7h7qgucggqmbha",
            "convictionDate": "2019-10-10T00:00:00+00:00",
            "convictionType": "N001"
        }
    ]
}
```

##### Example error

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

### Create Driver Declared Conviction

`POST /v2/fleet/driver/:fleetDriverId/declared-conviction/`

#### Request Body

| Key | Type | Required | Notes |
| --- | --- | --- | --- |
| convictionDate | iso-8601 string | yes |  |
| convictionType | string | yes | See [Conviction Types](./conviction_types.md) |

##### Example response

HTTP 201

```
{
    "status": "OK",
    "declaredConviction": {
        "convictionDate": "2019-10-10T00:00:00+00:00",
        "id": "fltcon_ow3b6pkhtjac7h7qgucggqmbha",
        "convictionType": "N001"
    }
}
```

##### Example response

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

### Delete Driver Declared Conviction

`DELETE /v2/fleet/driver/:fleetDriverId/declared-conviction/:declaredConvictionId/`

##### Example response

HTTP 200

```
{
    "status": "OK"
}
```
