## Driver

## Create Driver

`POST /v2/fleet/driver/`
#### Request Body

| Key | Type | Required | Notes |
| --- | --- | --- | --- |
| email | string | yes |  |
| dob | iso-8601 date string | yes |  |
| givenNames | string | yes |  |
| lastName | string | yes |  |
| address | string | yes |  |
| city | string | yes |  |
| postCode | string | yes |  |
| country | ISO 3166-1 alpha-2 string | yes |  |
| agreedFairObtainingNoticeAt | iso-8601 string | no | The datetime the driver agreed to let us access conviction data from third parties |
| licence.licenceNumber | string | yes |  |
| licence.licenceValidFrom | iso-8601 date string | yes |  |
| licence.country | ISO 3166-1 alpha-2 string | yes | country of issue |
| licence.points | int | yes | current number of endorsement points on the licence |
| convictions.convictionDate | iso-8601 string | yes | iso-8601 string |
| convictions.convictionType | string | yes | The type of conviction as defined by the ABI code list, see definition list |
| claims.claimDate | iso-8601 string | yes |  |
| claims.faultType | enum | yes |  See [Fault types](./docs/fault_types.md) |
| claims.claimType | enum | yes | See [Claim types](./docs/claim_types.md) |
| claims.customerAtFault | boolean | yes |  |

```
{
    "driver": {
     "email": "raekwon@wutangforever.wu",
     "address": "25 Luke Street",
     "city": "London",
     "dob": "1982-04-01",
     "givenNames": "Reakwon The",
     "lastName": "Chef",
     "phoneNumber": "+4412314323423",
     "postCode": "EC2A 4DS",
     "country": "GB"
    },
    "licence": {
        "country": "GB",
        "licenceValidFrom": "1990-10-09",
        "licenceNumber": "adriverslicence",
        "licenceDuration": 8,
        "points": 2
    },
    "claims": [
      {
          "claimDate": "2017-02-25 00:00:00+01:00", 
          "customerAtFault": False,
          "claimType": "A",
          "faultType": "A1|Fault Including Hit and Run"
       },
       {
          "claimDate": "2017-02-26 00:00:00+01:00", 
          "customerAtFault": True,
          "claimType": "L",
          "faultType": "Collision"
       }
    ],
    "convictions": [
      {
          "convictionDate": "2017-02-25 00:00:00+01:00", 
          "convictionType": "CU40"
      },
    ]
}
```

##### Example response

HTTP 201

```
{
    "status": "OK",
    "id": 41,
    "driver": {
     "email": "raekwon@wutangforever.wu",
     "address": "25 Luke Street",
     "city": "London",
     "dob": "14/4/1990",
     "givenNames": "Reakwon The",
     "lastName": "Chef",
     "phoneNumber": "+4412314323423",
     "postCode": "EC2A 4DS",
     "country": "GB"
    },
}
```

##### Example response

HTTP 401

```
{
    "status": "NOK",
    "error": "INVALID_DATA",
    "message": "Invalid data format",
    "detail": "Driver 44 with this email already exists"
}
```

##### Example CURL

```
curl --request POST \
  --url http://localhost:8000/v2/fleet/driver/ \
  --header 'authorization: 357e80a5-f9d5-4368-86f4-e1edfd2ea590' \
  --header 'content-type: application/json' \
  --data '{
   "driver":{
    "email":"raekwon@wutangforever.wu",
    "address":"25 Luke Street",
    "city":"London",
    "dob":"14/4/2000",
    "givenNames":"Reakwon The",
    "lastName":"Chef",
    "phoneNumber":"+4412314323423",
    "postCode":"EC2A 4DS",
    "country":"GB"
   },
   "licence":{
    "country":"GB",
    "licenceNumber":"adriverslicence",
    "licenceDuration":4,
    "points":2
   },
   "convictions":[
    {
        "convictionDate":"2017-02-25 00:00:00+01:00",
        "convictionType":"CU40"
    }
   ],
   "claims":[
    {
        "claimDate":"2017-02-25 00:00:00+01:00",
        "customerAtFault":false
    }
   ]
}'
```

### Update Driver

Updates the specified driver by setting the values of the parameters passed. Any parameters not provided will be left unchanged.

`PUT /v2/fleet/driver/:fleetDriverId`

#### Request Body

| Key | Type | Required | Notes |
| --- | --- | --- | --- |
| email | string | yes |  |
| dob | iso-8601 date string | yes |  |
| givenNames | string | yes |  |
| lastName | string | yes |  |
| address | string | yes |  |
| city | string | yes |  |
| postCode | string | yes |  |
| country | ISO 3166-1 alpha-2 string | yes |  |
| agreedFairObtainingNoticeAt | iso-8601 string | no | The datetime the driver agreed to let us access conviction data from third parties |
| licence.licenceNumber | string | yes |  |
| licence.licenceValidFrom | iso-8601 date string | yes |  |
| licence.country | ISO 3166-1 alpha-2 string | yes | country of issue |
| licence.points | int | yes | current number of endorsement points on the licence |

```
{
    "driver": {
     "email": "raekwon@wutangforever.wu",
     "address": "25 Luke Street",
     "city": "London",
     "dob": "1982-04-01",
     "givenNames": "Reakwon The",
     "lastName": "Chef",
     "phoneNumber": "+4412314323423",
     "postCode": "EC2A 4DS",
     "country": "GB"
    },
    "licence": {
        "country": "GB",
        "licenceValidFrom": "1990-10-09",
        "licenceNumber": "adriverslicence",
        "licenceDuration": 8,
        "points": 2
    },
}
```

##### Example response

HTTP 201

```
{
    "status": "OK",
    "id": 41,
    "driver": {
     "email": "raekwon@wutangforever.wu",
     "address": "25 Luke Street",
     "city": "London",
     "dob": "14/4/1990",
     "givenNames": "Reakwon The",
     "lastName": "Chef",
     "phoneNumber": "+4412314323423",
     "postCode": "EC2A 4DS",
     "country": "GB"
    },
}
```


### List drivers

`GET /v2/fleet/driver/`

##### Example response

HTTP 200

```
{
    "status": "OK",
    [
        {
          "licence": {
            "licenceNumber": "adriverslicence"
          },
          "modifiedAt": "2019-07-08T16:32:58.138728+00:00",
          "fleetDriverId": 3,
          "driver": {
            "city": "London",
            "country": "GB",
            "address_line_2": "",
            "email": "raekwon@wutangforever.wu",
            "lastName": "Chef",
            "address": "25 Luke Street",
            "postCode": "EC2A 4DS",
            "givenNames": "Reakwon The",
            "phoneNumber": "+4412314323423",
            "dob": "1982-04-01"
          }
        },
        {
          "licence": {
            "licenceNumber": "adriverslicence"
          },
          "modifiedAt": "2019-07-08T16:32:58.138728+00:00",
          "fleetDriverId": 3,
          "driver": {
            "city": "London",
            "country": "GB",
            "address_line_2": "",
            "email": "raekwon@wutangforever.wu",
            "lastName": "Chef",
            "address": "25 Luke Street",
            "postCode": "EC2A 4DS",
            "givenNames": "Reakwon The",
            "phoneNumber": "+4412314323423",
            "dob": "1982-04-01"
          }
        }
    ]
}
```

### Get Driver

`GET /v2/fleet/driver/:fleetDriverId`

##### Example response

HTTP 200

```
{
  "status": "OK",
  "licence": {
    "licenceNumber": "adriverslicence"
  },
  "modifiedAt": "2019-07-08T16:32:58.138728+00:00",
  "fleetDriverId": 3,
  "driver": {
    "city": "London",
    "country": "GB",
    "address_line_2": "",
    "email": "raekwon@wutangforever.wu",
    "lastName": "Chef",
    "address": "25 Luke Street",
    "postCode": "EC2A 4DS",
    "givenNames": "Reakwon The",
    "phoneNumber": "+4412314323423",
    "dob": "1982-04-01"
  }
}
```
