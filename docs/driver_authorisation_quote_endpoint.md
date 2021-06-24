## Driver Authorisation Request

### Create Driver Authorisation Request

`POST /v2/fleet/driver-authorisation-request/`

#### Request Body

| Key | Type | Required | Notes |
| --- | --- | --- | --- |
| fleetDriverId | int | yes |  |
| fleetVehicleId | int | yes |  |
| startTime | iso-8601 date time | no |  |
| endTime | iso-8601 date time | no |  |



##### Example body

```
{
    "fleetDriverId": 3,
    "fleetVehicleId": 2,
    "startTime": "2019-08-01T17:00:00",
    "endTime": "2019-12-01:21:00:00"
}
```

##### Example response

HTTP 201

```
{
  "id": 5,
  "fleetVehicleId": 2,
  "fleetDriverId": 3,
  "status": "approved",
  "rates": [
    {
      "kind": "premium_per_day",
      "amount": 992,
      "currency": "GBP"
    },
    {
      "kind": "excess",
      "amount": 50000,
      "currency": "GBP"
    }
  ],
}
```

##### Example error

HTTP 401

```
{
  "status": "NOK",
  "error": "INVALID_DATA",
  "message": "Invalid data format",
  "detail": {
    "fleetDriverId": [
    "`id` does not exist."
    ]
  }
}
```

### Get Driver Authorisation Request

`GET /v2/fleet/driver-authorisation-request/&lt;authorisationRequestId&gt;`

##### Example response

HTTP 201

```
{
  "id": 5,
  "fleetVehicleId": 2,
  "fleetDriverId": 3,
  "status": "approved",
  "rates": [
    {
      "kind": "premium_per_day",
      "amount": 992,
      "currency": "GBP"
    },
    {
      "kind": "excess",
      "amount": 50000,
      "currency": "GBP"
    }
  ],
}
```

### List Driver Authorisation Requests

`GET /v2/fleet/driver-authorisation-request/`

##### Example response

HTTP 201

```
{
  "requests": [
    {
      "status": "declined",
      "fleetVehicleId": 2,
      "fleetDriverId": 3,
      "id": 1,
      "rates": null
    },
    {
      "declined": "approved",
      "fleetVehicleId": 2,
      "fleetDriverId": 3,
      "id": 2,
      "rates": null
    }
  ]
}
```
