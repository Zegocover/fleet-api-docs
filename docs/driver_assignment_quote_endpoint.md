## POST /v2/fleet/driver-assignment/quote/

### Request Body

| Key | Type | Required | Notes |
| --- | --- | --- | --- |
| fleetDriverId | int | yes |  |
| fleetVehicleId | int | yes |  |
| coverStartsAt | iso-8601 date time | no |  |
| coverEndsAt | iso-8601 date time | no |  |



##### Example body

```
{
    "fleetDriverId": 3,
    "fleetVehicleId": 2,
    "coverStartsAt": "2019-08-01T17:00:00",
    "coverEndsAt": "2019-12-01:21:00:00"
}
```

### Example response

HTTP 201

```
{
  "id": 5,
  "pricing": {
    "excess": 100000, # pence
    "dailyPremium": 1250 # pence
    "totalPremium": 250 # pounds
  },
  "fleetVehicleId": 2,
  "fleetDriverId": 3,
  "declined": false
}
```

### Example error

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

## GET /v2/fleet/driver-assignment/quote/&lt;assignmentQuoteId&gt;

### Example response

HTTP 201

```
{
  "id": 5,
  "pricing": {
    "excess": 100000, # pence
    "dailyPremium": 1250 # pence
    "totalPremium": 250 # pounds
  },
  "fleetVehicleId": 2,
  "fleetDriverId": 3,
  "declined": false
}
```

## GET /v2/fleet/driver-assignment/quote/

### Example response

HTTP 201

```
{
  "quotes": [
    {
    "declined": true,
    "fleetVehicleId": 2,
    "fleetDriverId": 3,
    "id": 1,
    "pricing": null
    },
    {
    "declined": true,
    "fleetVehicleId": 2,
    "fleetDriverId": 3,
    "id": 2,
    "pricing": null
    },
    {
    "declined": true,
    "fleetVehicleId": 2,
    "fleetDriverId": 3,
    "id": 3,
    "pricing": null
    },
    {
    "declined": true,
    "fleetVehicleId": 2,
    "fleetDriverId": 3,
    "id": 4,
    "pricing": null
    },
    {
    "declined": false,
    "fleetVehicleId": 2,
    "fleetDriverId": 3,
    "id": 5,
    "pricing": {
        "excess": 100000,
        "dailyPremium": 3500
    }
    }
  ]
}
```
