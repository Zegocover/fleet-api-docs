## Driver Declared Claims
### Get Driver Declared Claim

`GET /v2/fleet/driver/:fleetDriverId/declared-claim/:id`

##### Example response

HTTP 200

```
{
    "status": "OK",
    "declaredClaims": [
        {
            "claimDate": "2019-09-11T00:00:00+00:00",
            "claimType": "L",
            "amount": 200,
            "id": "fltclm_nij2xowz6nbc5nuju2oajamziq",
            "customerAtFault": false,
            "faultType": "A1|Fault Including Hit and Run"
        },
        {
            "claimDate": "2019-10-10T00:00:00+00:00",
            "claimType": "L",
            "amount": 100,
            "id": "fltclm_nij2xowz6nbc5nuju2oajamziq",
            "customerAtFault": false,
            "faultType": “A1|Fault Including Hit and Run”
        }
    ]
}
```

##### Example response

HTTP 401

```
{
    "status": "NOK",
    "error": "INVALID_DATA",
    "message": "Invalid data format",
    "detail": "Driver does not exist"
}
```

### Create Driver Declared Claim

`POST v2/fleet/driver/:fleetDriverId/declared-claim`

#### Request Body

| Key | Type | Required | Notes |
| --- | --- | --- | --- |
| claimDate | iso-8601 string | yes |  |
| faultType | enum | yes | See [Fault types](./fault_types.md) |
| claimType | enum | yes | See [Claim types](./claim_types.md) |
| customerAtFault | boolean | yes |  |

##### Example response

HTTP 201

```
{
    "status": "OK",
    "declaredClaim": {
        "claimDate": "2019-10-10T00:00:00+00:00",
        "claimType": "L",
        "amount": 100,
        "id": "fltclm_nij2xowz6nbc5nuju2oajamziq",
        "customerAtFault": false,
        "faultType": "A1|Fault"
    }
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
### Delete Driver Declared Claim

`DELETE v2/fleet/driver/:fleetDriverId/declared-claim/:id`

##### Example response

HTTP 200

```
{
    "status": "OK"
}
```
