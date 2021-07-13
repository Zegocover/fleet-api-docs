## Driver

## Create Driver

`POST /v2/fleet/driver/`
#### Request Body

##### Driver

**Required**

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
| hasCriminalConvictions | booleana | no | Does the driver have any unspent criminal convictions |

##### Licence

**Required**

| Key | Type | Required | Notes |
| --- | --- | --- | --- |
| licenceTypeAbi | enum | yes | See [ABI licence types](./licence_types.md) |
| licenceNumber | string | yes |  |
| licenceValidFrom | iso-8601 date string | yes |  |
| country | ISO 3166-1 alpha-2 string | yes | country of issue |
| points | int | yes | current number of endorsement points on the licence |


##### Conviction

| Key | Type | Required | Notes |
| --- | --- | --- | --- |
| convictionDate | iso-8601 string | yes | iso-8601 string |
| convictionType | enum | yes | See [Conviction types](./conviction_types.md) |

##### Claim

| Key | Type | Required | Notes |
| --- | --- | --- | --- |
| claimDate | iso-8601 string | yes |  |
| faultType | enum | yes |  See [Fault types](./fault_types.md) |
| claimType | enum | yes | See [Claim types](./claim_types.md) |
| customerAtFault | boolean | yes |  |

##### Private Hire Licence

| Key | Type | Required | Notes |
| --- | --- | --- | --- |
| number | string | yes |  |
| expireTime | iso-8601 date string | yes |  |
| firstIssueTime | iso-8601 date string | yes | The date in which the person was first ever issued a PCO licence |
| issuingDistrict | string | yes | See [Private Hire Issuing Districts](./private_hire_issuing_districts.md) |

##### Example request

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
        "points": 2
    },
    "privateHireLicence": {
      "number": "P36696",
      "expireTime": "2022-10-10",
      "issuingDistrict": "london_(pco)",
      "firstIssueTime": "2016-10-10"
    },
    "claims": [
      {
          "claimDate": "2017-02-25 00:00:00+01:00", 
          "customerAtFault": false,
          "claimType": "A",
          "faultType": "A1|Fault Including Hit and Run"
       },
       {
          "claimDate": "2017-02-26 00:00:00+01:00", 
          "customerAtFault": true,
          "claimType": "L",
          "faultType": "A2"
       }
    ],
    "convictions": [
      {
          "convictionDate": "2017-02-25 00:00:00+01:00", 
          "convictionType": "CU40"
      }
    ]
}
```

##### Example response

HTTP 201

```
{
    "status": "OK",
    "id": "fltdrv_kiaqgehibbhktagg75drzcssxy",
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

### Update Driver

Updates the specified driver by setting the values of the parameters passed. Any parameters not provided will be left unchanged.

`PUT /v2/fleet/driver/:id`

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
    "id": "fltdrv_kiaqgehibbhktagg75drzcssxy",
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


### List Drivers

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
          "id": "fltdrv_kiaqgehibbhktagg75drzcssxy"
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
          "id": "fltdrv_kiaqgehibbhktagg75drzcssxy"
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

`GET /v2/fleet/driver/:id`

##### Example response

HTTP 200

```
{
  "status": "OK",
  "licence": {
    "licenceNumber": "adriverslicence"
  },
  "modifiedAt": "2019-07-08T16:32:58.138728+00:00",
  "id": "fltdrv_kiaqgehibbhktagg75drzcssxy"
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
