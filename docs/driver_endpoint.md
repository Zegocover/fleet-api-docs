## POST /v2/fleet/driver/

## PUT /v2/fleet/driver/&lt;fleetDriverId&gt;

### Request Body

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
| claims.faultType | enum | yes |  One of **Fault Types** defined below |
| claims.claimType | enum | yes | One of **Claim Types** defined below |
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

### Example response

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

### Example response

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

## GET /v2/fleet/driver/

### Example response

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

## GET /v2/fleet/driver/&lt;fleetDriverId&gt;

### Example response

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

### Claim Type Codes

| Key | Notes |
| --- | --- |
| A | Accident |
| B | Accident Damage |
| C | Chemical |
| L | Collision |
| J | Collision with Pedestrian |
| F | Fire |
| D | Flood |
| G | Hit by Third Party |
| E | Hit Third Party  |
| K | Loss Of Keys |
| P | Lost Control |
| M | Malicious Damage As A Result Of Theft |
| Y | Malicious Damage Claim |
| N | Multi-Vehicle Collision |
| 0 (zero) | Not Available  |
| X | Other |
| H | Parked |
| R | Riot |
| S | Storm |
| Q | Theft from Vehicle |
| Z | Theft of Vehicle |
| U | Unknown |
| V | Vandalism |
| W | Windscreen/Glass |

### Fault Type Codes

| Key | Notes |
| --- | --- |
| A1|Fault | Fault |
| A1|Fault Including Hit and Run |  |
| A2 | Fault and Conviction |
| A3 | Fault and Personal Injury |
| A4 | Fault and Personal Injury and Conviction |
| A5 | Non Fault (Full Recovery of Costs Made) |
| A6 | Non Fault (Including Personal Injury) |
| F | Fire |
| T | Theft |
| W | Windscreen |
| YF | Fault |
| NF | Non Fault |
