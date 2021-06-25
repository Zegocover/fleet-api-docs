## Driver Authorisation Estimate

Returns estimate rates based on existing vehicles in your fleet. This can be useful if you don't know information about your driver but want some rough rates for your vehicle.
## Create Driver Authorisation Estimate



`POST /v2/fleet/driver-authorisation/estimate/`

#### Request Body

| Key | Type | Required | Notes |
| --- | --- | --- | --- |
| fleetVehicleId | int | yes |  |

##### Example body

```
{
    "fleetVehicleId": 2
}
```

##### Example response

HTTP 201

```
{
  "id": 5,
  "pricing": {
    "excess": 100000,
    "dailyPremium": 35
    "totalPremium": 700
  },
  "fleetVehicleId": 2,
  "declined": false
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
    "fleetDriverId": [
    "`id` does not exist."
    ]
  }
}
```
