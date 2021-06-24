### Motor Trade Cover Endpoint

#### POST /v2/fleet/motor-trade-cover/

#### Request Body

| Key | Type | Required | Notes |
| --- | --- | --- | --- |
| coverStartsAt | iso-8601 datetime string | true |
| fleetVehicleId | int | true |


##### Example response

HTTP 201

```
{
  "message": "MotorTradeCover created!",
  "status": "OK",
  "motorTradeCover": {
    "id": 9,
    "fleetVehicleId": 812,
    "coverStartsAt": "2019-07-12T14:34:00+00:00",
    "coverEndsAt": null
  }
}
```

#### GET /v2/fleet/motor-trade-cover/:motorTradeCoverId:/

##### Example response

HTTP 200

```
{
  "status": "OK",
  "motorTradeCover": {
    "id": 1,
    "fleetVehicleId": 2,
    "coverEndsAt": "2019-09-10T15:54:00+00:00",
    "coverStartsAt": "2019-09-10T15:54:00+00:00"
  }
}
```

#### DELETE /v2/fleet/motor-trade-cover/:motorTradeCoverId:/

##### Example response

HTTP 202

```
{
  "message": "MotorTradeCover updated!",
  "status": "OK",
  "motorTradeCover": {
    "fleet_vehicle_id": 812,
    "id": 7,
    "coverEndsAt": "2019-07-12T10:12:58.935994+00:00",
    "coverStartsAt": "2019-07-11T14:34:00+00:00"
  }
}
```
