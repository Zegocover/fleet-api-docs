## GET /v2/fleet/driver/&lt;fleetDriverId&gt;/declared-claim/&lt;declaredClaimId&gt;

### Example response

HTTP 200

```
{
    "status": "OK",
    "declaredClaims": [
        {
            "claimDate": "2019-09-11T00:00:00+00:00",
            "claimType": "L",
            "amount": 200,
            "id": 1,
            "customerAtFault": false,
            "faultType": "A1|Fault Including Hit and Run"
        },
        {
            "claimDate": "2019-10-10T00:00:00+00:00",
            "claimType": "L",
            "amount": 100,
            "id": 4,
            "customerAtFault": false,
            "faultType": “A1|Fault Including Hit and Run”
        }
    ]
}
```

### Example response

HTTP 401

```
{
    "status": "NOK",
    "error": "INVALID_DATA",
    "message": "Invalid data format",
    "detail": "Driver does not exist"
}
```

## POST v2/fleet/driver/&lt;fleetDriverId&gt;/declared-claim

### Request Body

| Key | Type | Required | Notes |
| --- | --- | --- | --- |
| claimDate | iso-8601 string | yes |  |
| faultType | enum | yes | One of **Fault Types** defined below |
| claimType | enum | yes | One of **Claim Types** defined below |
| customerAtFault | boolean | yes |  |

### Example response

HTTP 201

```
{
    "status": "OK",
    "declaredClaim": {
        "claimDate": "2019-10-10T00:00:00+00:00",
        "claimType": "L",
        "amount": 100,
        "id": 8,
        "customerAtFault": false,
        "faultType": "A1|Fault"
    }
}
```

### Example error

HTTP 404

```
{
    "status": "NOK",
    "error": "INVALID_DATA",
    "message": "Invalid data format",
    "detail": {
        "driver": [
            "Driver does not exist"
        ]
    }
}
```

## DELETE v2/fleet/driver/&lt;fleetDriverId&gt;/declared-claim/&lt;declaredClaimId&gt;

### Example response

HTTP 200

```
{
    "status": "OK"
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
| E | Hit Third Party |
| K | Loss Of Keys |
| P | Lost Control |
| M | Malicious Damage As A Result Of Theft |
| Y | Malicious Damage Claim |
| N | Multi-Vehicle Collision |
| 0 (zero) | Not Available |
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
