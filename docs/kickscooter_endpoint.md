## Kick Scooter

### Create Kick Scooter

`POST /v2/fleet/kickscooter`

#### Request body

| Key | Type | Required | Notes                                                                                                 |
| --- | --- |----------|-------------------------------------------------------------------------------------------------------|
| coverStartsAt | iso-8601 string | No       | If not provided in the POST message the vehicle will be created using the current date and time.                                                                     |
| city | string | No       |                                                                                                       |
| coverEndsAt | iso-8601 string | No       |                                                                                                       |
| kickscooter.serialNumber | string | Yes      |                                                                                                       |
| kickscooter.make | string | Yes      | e.g. Honda                                                                                            |
| kickscooter.model | string | Yes      | e.g Accord                                                                                            |
| kickscooter.year | int | Yes      | Accepts values between 1950 and the current year + 1                                                  |
| kickscooter.valuation | int | Yes      |                                                                                                       |
| kickscooter.type | string | Yes      | e.g `electric_kick_scooter` or `electric_bike`                                                        |
| kickscooter.stickerCode | string | Yes (DE only) | e.g `Temporary identity in addition to serialNumber` <br/> This field may be modified via PUT <br/> This field is required for Germany(DE) Scooters        |
| kickscooter.metadata | string | No       | e.g `unspecified additional vehicle data field for API User` <br/> This field may be modified via PUT |

##### Example body

```
{
    "kickScooter": {
        "serialNumber": "1234ABCD",
        "make": "Xiaomi",
        "model": "M365",
        "year": 2018,
        "valuation": 400,
        "type": "electric_kick_scooter",
        "stickerCode": "sticker_code_1",
        "metadata": "metadata info"
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
        "type": "electric_kick_scooter",
        "stickerCode": "sticker_code_1",
        "metadata": "metadata info"
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
  --url https://fleet-api-v2.zego.com/v2/fleet/kickscooter/ \
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
        "type": "electric_kick_scooter",
        "stickerCode": "sticker_code_1",
        "metadata": "metadata info"
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
        "type": "electric_kick_scooter",
        "stickerCode": "sticker_code_1",
        "metadata": "metadata info"
    }
}
```

##### Example CURL

```
curl --request GET \
  --url https://fleet-api-v2.zego.com/v2/fleet/kickscooter/11/ \
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
        "type": "electric_kick_scooter",
        "stickerCode": "sticker_code_1",
        "metadata": "metadata info"
    }
}
```

##### Example CURL

```
curl --request GET \
  --url https://fleet-api-v2.zego.com/v2/fleet/kickscooter/search?serialNumber=1234ABCD \
  --header 'authorization: 357e80a5-f9d5-4368-86f4-e1edfd2ea590'
```

### Search Kick Scooter By Sticker Code

`GET /v2/fleet/kickscooter/search?stickerCode=:kickscooterStickerCode`

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
        "type": "electric_kick_scooter",
        "stickerCode": "sticker_code_1",
        "metadata": "metadata info"
    }
}
```

##### Example CURL

```
curl --request GET \
  --url https://fleet-api-v2.zego.com/v2/fleet/kickscooter/search?stickerCode=sticker_code_1 \
  --header 'authorization: 357e80a5-f9d5-4368-86f4-e1edfd2ea590'
```

### Update Kick Scooter

`PUT /v2/fleet/kickscooter/:id`

#### Request body

| **key** | **type** | required | **notes** |
| --- | --- | --- | --- |
| coverEndsAt | iso-8601 | No | string |
| kickscooter.stickerCode | string | No  |    
| kickscooter.metadata | string | No    |


##### Example body

```
{
    "coverEndsAt": "2020-1-10T20:00:00+00:00",
    "kickScooter": {
        "stickerCode": "sticker_code_1",
        "metadata": "metadata info"
    }
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
        "type": "electric_kick_scooter",
        "stickerCode": "sticker_code_1",
        "metadata": "metadata info"
    }
}
```

##### Example CURL

```
curl --request PUT \
  --url https://fleet-api-v2.zego.com/v2/fleet/kickscooter/12/ \
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
        "type": "electric_kick_scooter",
        "stickerCode": "sticker_code_1",
        "metadata": "metadata info"
    }
}
```

##### Example CURL

```
curl --request DELETE \
  --url https://fleet-api-v2.zego.com/v2/fleet/kickscooter/12/ \
  --header 'authorization: 357e80a5-f9d5-4368-86f4-e1edfd2ea590' \
```
