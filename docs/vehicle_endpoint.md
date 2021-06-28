## Vehicle
### Create Vehicle

`POST /v2/fleet/vehicle/`

#### Request body

| Key | Type | Required | Notes |
| --- | --- | --- | --- |
| coverStartsAt | iso-8601 string  | No |  |
| city | string  | No |  |
| coverEndsAt | iso-8601 string  | No |  |
| uberType | enum  | No | one of: “uber_x”, “uber_xl”, “uber_exec”, “uber_lux”  |
| ownerCompanyId | string  | No |  **Zego ID** of the company that owns the vehicle. See [company]('./company_endpoint.md) |
| vehicle.registrationNumber | string  | Yes |  |
| vehicle.make | string  | Yes | e.g. Honda |
| vehicle.model | string  | Yes | e.g Accord |
| vehicle.year | int  | Yes | Accepts values between 1950 and the current year + 1 |
| vehicle.engineSize | int  | No | Accepts values between 50 and 20000 cc |
| vehicle.valuation | int  | No | e.g 22000 |
| vehicle.fuelType | enum  | Yes | one of: &quot;PETROL&quot;, &quot;DIESEL&quot;, &quot;ELECTRICITY&quot;, &quot;HYBRID ELECTRIC&quot;, &quot;GAS BI-FUEL&quot; |
| vehicle.type | enum  | Yes | one of: &quot;car&quot;, &quot;scooter&quot;, &quot;van&quot; |
| vehicle.seats | int  | Yes |  |

##### Example body

```
{
    "vehicle": {
        "registrationNumber": "AAA0SFX",
        "make": "Toyota",
        "model": "Yaris",
        "year": 2010,
        "engineSize": 1000,
        "valuation": 20000,
        "fuelType": "PETROL",
        "type": "car",
        "seats": 9
    },
    "coverStartsAt": "2019-10-10T10:00:00+00:00",
    "city": "London",
    "coverEndsAt": "2019-10-10T20:00:00+00:00",
    "uberType": "uber_x",
    "ownerCompanyId": 1
}
```

##### Example response

HTTP 201

```
{
  "coverStartsAt": "2019-10-10 10:00:00+00:00",
  "uberType": "uber_x"
  "vehicle": {
    "type": "car",
    "seats": 9,
    "year": 2010,
    "make": "Toyota",
    "registrationNumber": "AAA0SFX",
    "engineSize": 1000,
    "fuelType": "PETROL",
    "model": "Yaris"
  },
  "id": "fltveh_hhz2wvyhdrgnzlt3pc2li24xmm",
  "city": "London",
  "ownerCompanyId": 1,
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
  --url http://localhost:8000/v2/fleet/vehicle/ \
  --header 'authorization: 357e80a5-f9d5-4368-86f4-e1edfd2ea590' \
  --header 'content-type: application/json' \
  --data '{
        "vehicle": {
        "registrationNumber": "AAA0SFX",
        "make": "Toyota",
        "model": "Yaris",
        "year": 1970,
        "engineSize": 1000,
        "valuation": 20000,
        "fuelType": "PETROL",
        "type": "car",
        "seats": 9
    },
    "coverStartsAt": "2019-10-10T10:00:00+00:00",
    "city": "London",
    "uberType": "uber_x",
}'
```

## Get Vehicle

`GET /v2/fleet/vehicle/:id`

##### Example response

HTTP 200

```
{
  "coverStartsAt": "2019-10-10 10:00:00+00:00",
  "vehicle": {
    "type": "car",
    "seats": 9,
    "year": 2010,
    "make": "Toyota",
    "registrationNumber": "AAA0SFX",
    "engineSize": 1000,
    "fuelType": "PETROL",
    "model": "Yaris"
  },
  "id": "fltveh_hhz2wvyhdrgnzlt3pc2li24xmm",
  "city": "London"
}
```

##### Example response

HTTP 401

```
{
  "status": "NOK",
  "error": "INVALID_DATA",
  "message": "Invalid data format",
  "detail": {
    "id": [
      "`id` does not exist."
    ]
  }
}
```

##### Example CURL

```
curl --request GET \
  --url http://localhost:8000/v2/fleet/vehicle/11/ \
  --header 'authorization: 357e80a5-f9d5-4368-86f4-e1edfd2ea590'
```

## Update Vehicle

`PUT /v2/fleet/vehicle/:id`

#### Request body

| **key** | **type** | required | **notes** |
| --- | --- | --- | --- |
| coverEndsAt | iso-8601  | No | string  |
| vehicle.valuation | int  | No | e.g 22000 |

##### Example body

```
{
    "coverEndsAt": "2019-10-10T20:00:00+00:00"
    "vehicle": {
        "valuation": 10000
    }
}
```

##### Example response

HTTP 200

```
{
  "city": "London",
  "coverEndsAt": "2019-10-10T20:00:00+00:00",
  "id": "fltveh_hhz2wvyhdrgnzlt3pc2li24xmm",
  "vehicle": {
    "engineSize": 1000,
    "type": "car",
    "registrationNumber": "AAA0SFX2",
    "seats": 9,
    "make": "Toyota",
    "fuelType": "PETROL",
    "model": "Yaris",
    "year": 2010
  },
  "coverStartsAt": "2019-10-10T10:00:00+00:00"
}
```

##### Example CURL

```
curl --request PUT \
  --url http://localhost:8000/v2/fleet/vehicle/12/ \
  --header 'authorization: 357e80a5-f9d5-4368-86f4-e1edfd2ea590' \
  --header 'content-type: application/json' \
  --data '{
    "coverEndsAt": "2019-10-10T20:00:00+00:00"
}'
```

## Remove Vehicle

`DELETE /v2/fleet/vehicle/:fleetVehicleId`

##### Example response

HTTP 200

```
{
  "vehicle": {
    "seats": 9,
    "model": "Yaris",
    "make": "Toyota",
    "year": 2010,
    "type": "car",
    "engineSize": 1000,
    "registrationNumber": "AAA0SFX21",
    "fuelType": "PETROL"
  },
  "city": "London",
  "id": "fltveh_hhz2wvyhdrgnzlt3pc2li24xmm",
  "coverEndsAt": "2019-07-01T13:50:11.635258+00:00",
  "uberType": "uber_x",
  "coverStartsAt": "2019-07-01T13:49:23.546984+00:00"
}
```

##### Example CURL

```
curl --request DELETE \
  --url http://localhost:8000/v2/fleet/vehicle/12/ \
  --header 'authorization: 357e80a5-f9d5-4368-86f4-e1edfd2ea590' \
```

## GET /v2/fleet/vehicle/

##### Example response

HTTP 200

```
{
  "fleet_vehicles": [
    {
      "coverEndsAt": "2019-07-01T13:50:11.635258+00:00",
      "city": "London",
      "id": "fltveh_hhz2wvyhdrgnzlt3pc2li24xmm",
      "vehicle": {
          "engineSize": 1000,
          "type": "car",
          "make": "Toyota",
          "fuelType": "PETROL",
          "registrationNumber": "AAA0SFX21",
          "model": "Yaris",
          "seats": 9,
          "year": 2010
      },
      "uberType": "uber_x",
      "coverStartsAt": "2019-07-01T13:49:23.546984+00:00"
    },
    {
      "coverEndsAt": null,
      "city": "London",
      "id": "fltveh_hhz2wvyhdrgnzlt3pc2li24xmm",
      "vehicle": {
          "engineSize": 1000,
          "type": "car",
          "make": "Toyota",
          "fuelType": "PETROL",
          "registrationNumber": "AAA0SFX2",
          "model": "Yaris",
          "seats": 9,
          "year": 2010
      },
      "uberType": "uber_x",
      "coverStartsAt": "2019-07-01T13:16:12.675830+00:00"
      }
  ]
}
```

##### Example CURL

```
# Example CURL
curl --request GET \
--url http://localhost:8000/v2/fleet/vehicle/
--header 'authorization: 357e80a5-f9d5-4368-86f4-e1edfd2ea590' \
```
