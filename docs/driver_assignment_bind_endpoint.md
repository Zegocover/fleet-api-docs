Supply a quote ID, cover start date and a cover end date to create an assignment.

**_Note:_** _Dates defined on the driver assignment bind will take precedent over the dates defined on the quote_

## POST /v2/fleet/driver-assignment/bind/

### Request Body

| Key | Type | Required | Notes |
| --- | --- | --- | --- |
| assignmentQuoteId | int | yes |  |
| coverStartsAt | iso-8601 date time | yes |  |
| coverEndsAt | iso-8601 date time | yes |  |
| externalId | string | no |  |

##### Example body

```
{
    "assignmentQuoteId": 1,
    "coverStartsAt": "2019-08-01T17:00:00",
    "coverEndsAt": "2019-12-01:21:00:00",
    "externalId": "1232",
}
```

##### Example response

HTTP 201

```
{
    "status": "OK",
    "driverAssignment": {
        "driverAssignmentId": 1,
        "fleetDriverId": 12,
        "fleetVehicleId: 21,
        "assignmentQuoteId": 1,
        "coverStartsAt": "2019-08-01T17:00:00",
        "coverEndsAt": "2019-12-01:21:00:00"
        "externalId": "1232",
        "modifiedAt: "2019-07-29T17:01:02"
    }
}
```
