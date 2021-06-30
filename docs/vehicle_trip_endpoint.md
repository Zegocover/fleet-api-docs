## Trip

### Create Trip

`POST /v2/fleet/vehicle/trip/`

#### Request body

| Key | Type | Required | Notes |
| --- | --- | --- | --- |
| vehicleRegistrationNumber | string | Yes |  |
| startTime | string | Yes | iso-8601 string |
| endTime | string | Yes | iso-8601 string |
| distance | int | Yes | int |
| distanceUnit | string | Yes | One of `km` or `mi`  |

##### Example body

```
{ 
    "vehicleRegistrationNumber": "CBA 666",
    "startTime": "2021-07-24T10:00:00+00:00", 
    "endTime": "2021-07-25T10:00:00+00:00",
    "distance": 1000,
    "distanceUnits": "mi"
}
```

##### Example response

HTTP 201

```
{
  "distanceUnits": "mi",
  "distance": 1000,
  "endTime": "2021-07-25T10:00:00+00:00",
  "vehicleRegistrationNumber": "CBA 666",
  "startTime": "2021-07-24T10:00:00+00:00"
}
```

##### Example error

HTTP 400

```
{
    "status": "NOK",
    "error": "INVALID_DATA",
    "message": "An error occurred while creating the trip",
    "detail": "A \"trip\" exists for Nissan 1 Leaf CBA 666: Super Fleet GB Marketplace that covers the same time period"
}
```
