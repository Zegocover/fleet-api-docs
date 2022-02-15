## Duration

The duration object represents a period of time that a vehicle was in use. This is usually used to work out the flexible premium charges for your fleet.

### Create Duration

`POST /v2/fleet/kickscooter/duration`

#### Request body

| Key | Type | Required | Notes                                                                                                                                                                                                  |
| --- | --- | --- |--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| vehicleId | int | Yes |                                                                                                                                                                                                        |
| startsAt | iso-8601 string | Yes |                                                                                                                                                                                                        |
| endsAt | iso-8601 string | Yes |                                                                                                                                                                                                        |
| externalId | string | No | Do not provide this field in the JSON message unless necessary. It is not searchable once written. <br><br> Data in this field must be unique for each duration record. Use a UUID formated reference. |

##### Example body

```
{
  "vehicleId": 833,
  "startsAt": "2019-07-10T10:00:00+00:00",
  "endsAt": "2019-07-11T10:00:00+00:00",
  "externalId": "JCG5PPOIOL"
}
```

##### Example response

HTTP 201

```
{
  "message": "Duration created!",
  "status": "OK",
  "duration": {
    "id": 12,
    "vehicleId": 833,
    "startsAt": "2019-10-10T10:00:00+00:00",
    "endsAt": "2019-10-11T10:00:00+00:00",
    "externalId": "JCG5PPOIOL"
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
    "duration": {
      "endsAt": [
        "endsAt is before startsAt"
      ]
    }
  }
}
```
