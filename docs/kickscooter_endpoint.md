## Kick Scooter

### Create Kick Scooter

`POST /v2/fleet/kickscooter`

#### Request body

| Key | Type | Required | Notes |
| --- | --- | --- | --- |
| coverStartsAt | iso-8601 string | No |  |
| city | string | No |  |
| coverEndsAt | iso-8601 string | No |  |
| kickscooter.serialNumber | string | Yes |  |
| kickscooter.make | string | Yes | e.g. Honda |
| kickscooter.model | string | Yes | e.g Accord |
| kickscooter.year | int | Yes | Accepts values between 1950 and the current year + 1 |
| kickscooter.valuation | int | Yes |  |
| kickscooter.type | string | Yes | e.g `electric_kick_scooter` or `electric_bike` |

##### Example body

```
{
    "kickScooter": {
        "serialNumber": "1234ABCD",
        "make": "Xiaomi",
        "model": "M365",
        "year": 2018,
        "valuation": 400,
        "type": "electric_kick_scooter"
    },
    "coverStartsAt": "2019-10-10T10:00:00+00:00",
    "coverEndsAt": "2019-10-10T20:00:00+00:00",
    "city": "London"
}
```

##### Example response

HTTP 201

```
{
    "id": 11,
    "coverStartsAt": "2019-10-10T10:00:00+00:00",
    "coverEndsAt": "2019-10-10T20:00:00+00:00",
    "city": "London",
    "kickScooter": {
        "serialNumber": "1234ABCD",
        "make": "Xiaomi",
        "model": "M365",
        "year": 2018,
        "valuation": 400,
        "type": "electric_kick_scooter"
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
    "vehicle": {
      "year": [
        "'1940' is Invalid. Must be between 1950 and 2019."
      ]
    }
  }
}
```

##### Example CURL

```
curl --request POST \
  --url http://api.zego.com/v2/fleet/kickscooter/ \
  --header 'authorization: 357e80a5-f9d5-4368-86f4-e1edfd2ea590' \
  --header 'content-type: application/json' \
  --data '{
    "coverStartsAt": "2019-10-10T10:00:00+00:00",
    "city": "London",
    "kickScooter": {
        "serialNumber": "1234ABCD",
        "make": "Xiaomi",
        "model": "M365",
        "year": 2018,
        "valuation": 400,
        "type": "electric_kick_scooter"
    }
}'
```

### Get Kick Scooter

`GET /v2/fleet/kickscooter/:kickscooterId`

##### Example response

HTTP 200

```
{
    "id": 11,
    "coverStartsAt": "2019-10-10T10:00:00+00:00",
    "coverEndsAt": "2019-10-10T20:00:00+00:00",
    "city": "London",
    "kickScooter": {
        "serialNumber": "1234ABCD",
        "make": "Xiaomi",
        "model": "M365",
        "year": 2018,
        "valuation": 400,
        "type": "electric_kick_scooter"
    }
}
```

##### Example CURL

```
curl --request GET \
  --url http://api.zego.com/v2/fleet/kickscooter/11/ \
  --header 'authorization: 357e80a5-f9d5-4368-86f4-e1edfd2ea590'
```

### Search Kick Scooter

`GET /v2/fleet/kickscooter/search?serialNumber=:kickscooterSerialNumber`

##### Example response

HTTP 200

```
{
    "id": 11,
    "coverStartsAt": "2019-10-10T10:00:00+00:00",
    "coverEndsAt": "2019-10-10T20:00:00+00:00",
    "city": "London",
    "kickScooter": {
        "serialNumber": "1234ABCD",
        "make": "Xiaomi",
        "model": "M365",
        "year": 2018,
        "valuation": 400,
        "type": "electric_kick_scooter"
    }
}
```

##### Example CURL

```
curl --request GET \
  --url http://api.zego.com/v2/fleet/kickscooter/11/ \
  --header 'authorization: 357e80a5-f9d5-4368-86f4-e1edfd2ea590'
```

### Update Kick Scooter

`PUT /v2/fleet/kickscooter/:id`

#### Request body

| **key** | **type** | required | **notes** |
| --- | --- | --- | --- |
| coverEndsAt | iso-8601 | Yes | string |

##### Example body

```
{
    "coverEndsAt": "2020-1-10T20:00:00+00:00"
}
```

##### Example response

HTTP 200

```
{
    "id": 12,
    "coverStartsAt": "2019-10-10T10:00:00+00:00",
    "coverEndsAt": "2020-1-10T20:00:00+00:00",
    "city": "London",
    "kickScooter": {
        "serialNumber": "1234ABCD",
        "make": "Xiaomi",
        "model": "M365",
        "year": 2018,
        "valuation": 400,
        "type": "electric_kick_scooter"
    }
}
```

##### Example CURL

```
curl --request PUT \
  --url http://api.zego.com/v2/fleet/kickscooter/12/ \
  --header 'authorization: 357e80a5-f9d5-4368-86f4-e1edfd2ea590' \
  --header 'content-type: application/json' \
  --data '{
    "coverEndsAt": "2020-1-10T20:00:00+00:00"
}'
```

### Remove Kick Scooter

`DELETE /v2/fleet/kickscooter/:id`

Sets **coverEndsAt** to the current UTC time

##### Example response

HTTP 200

```
{
    "id": 12,
    "coverStartsAt": "2019-10-10T10:00:00+00:00",
    "coverEndsAt": "2020-1-10T20:00:00+00:00",
    "city": "London",
    "kickScooter": {
        "serialNumber": "1234ABCD",
        "make": "Xiaomi",
        "model": "M365",
        "year": 2018,
        "valuation": 400,
        "type": "electric_kick_scooter"
    }
}
```

##### Example CURL

```
curl --request DELETE \
  --url http://api.zego.com/v2/fleet/kickscooter/12/ \
  --header 'authorization: 357e80a5-f9d5-4368-86f4-e1edfd2ea590' \
```
