## GET /v2/fleet/driver-assignment/&lt;driverAssignmentId&gt;/

### Example response

HTTP 200

```
{
    "status": "OK",
    "driverAssignment": {
        "driverAssignmentId": 1,
        "fleetDriverId": 12,
        "fleetVehicleId": 21,
        "assignmentQuoteId": 1,
        "coverStartsAt": "2019-08-01T17:00:00",
        "coverEndsAt": "2019-12-01:21:00:00"
        "externalId": "1232",
        "modifiedAt": "2019-07-29T17:01:02"
        "voidedAt": null
    }
}
```

## GET /v2/fleet/driver-assignment/

## GET /v2/fleet/driver-assignment/search?from=fromDateTime&amp;to=toDateTime

### Request Params

| Key | Type | Required | Notes |
| --- | --- | --- | --- |
| fromDateTime | iso-8601 date time | no |  |
| toDateTime | iso-8601 date time | no |  |

### Example response

HTTP 200

```
{
    "status": "OK"
    "driverAssignments": [
        {
            "driverAssignmentId": 1,
            "fleetDriverId": 12,
            "fleetVehicleId": 21,
            "assignmentQuoteId": 1,
            "coverStartsAt": "2019-08-01T17:00:00",
            "coverEndsAt": "2019-12-01:21:00:00"
            "externalId": "1232",
            "modifiedAt": "2019-07-29T17:01:02"
        },
        {
            "driverAssignmentId": 1,
            "fleetDriverId": 12,
            "fleetVehicleId: 21,
            "assignmentQuoteId": 1,
            "coverStartsAt": "2019-08-01T17:00:00",
            "coverEndsAt": "2019-12-01:21:00:00"
            "externalId": "1232",
            "modifiedAt: "2019-07-29T17:01:02"
        },
        {
            "driverAssignmentId": 1,
            "fleetDriverId": 12,
            "fleetVehicleId": 21,
            "assignmentQuoteId": 1,
            "coverStartsAt": "2019-08-01T17:00:00",
            "coverEndsAt": "2019-12-01:21:00:00",
            "externalId": "1232",
            "modifiedAt": "2019-07-29T17:01:02"
        },
    ]
}
```

## PUT /v2/fleet/driver-assignment/&lt;driverAssignmentId&gt;/

### Request Body

| Key | Type | Required | Notes |
| --- | --- | --- | --- |
| coverEndsAt | iso-8601 date time | yes |  |

##### Example response

HTTP 202

```
{
    "status": "OK"
    "driverAssignment": {
        "driverAssignmentId": 1,
        "fleetDriverId": 12,
        "fleetVehicleId: 21,
        "assignmentQuoteId": 1,
        "coverStartsAt": "2019-08-01T17:00:00",
        "coverEndsAt": "2019-12-01:21:00:00",
        "externalId": "1232",
        "modifiedAt: "2019-07-29T17:01:02"
    }
}
```

## DELETE /v2/fleet/driver-assignment/&lt;driverAssignmentId&gt;/

##### Scenario 1

If you perform a DELETE request on the driver assignment resource that has not started yet this will void the driver assignment.

##### Scenario 2

If you perform a DELETE request on the driver assignment that is in progress it will set the **coverEndsAt** to now.

Performing this action on an assignment may be subject to cancellation charges.

### Scenario 1 

##### Example response

HTTP 202

```
{
    "status": "OK"
    "driverAssignment": {
        "driverAssignmentId": 1,
        "fleetDriverId": 12,
        "fleetVehicleId: 21,
        "assignmentQuoteId": 1,
        "coverStartsAt": "2050-08-01T17:00:00",
        "coverEndsAt": "2050-08-10:21:00:00"
        "externalId": "1232",
        "modifiedAt: "2019-07-29T17:01:02",
        "voidedAt":  "2019-08-10:21:00:00" // Will be set to now
    }
}
```

### Scenario 2 

##### Example response

HTTP 202

```
{
    "status": "OK"
    "driverAssignment": {
        "driverAssignmentId": 1,
        "fleetDriverId": 12,
        "fleetVehicleId: 21,
        "assignmentQuoteId": 1,
        "coverStartsAt": "2019-08-01T17:00:00",
        "coverEndsAt": "2019-08-10:21:00:00", // Will be set to now
        "externalId": "1232",
        "modifiedAt: "2019-07-29T17:01:02",
        "voidedAt":  null
    }


}
```
