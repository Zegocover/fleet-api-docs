## Driver Authorisation Estimate

Returns estimate rates based on existing vehicles in your fleet. This can be useful if you don't know information about your driver but want some rough rates for your vehicle.
## Create Driver Authorisation Estimate



`POST /v2/fleet/driver-authorisation-estimate/`

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
  "fleetVehicleId": "fltveh_hhz2wvyhdrgnzlt3pc2li24xmm"
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
