## Driver Assignments

The driver assignment object represents a period of time where a [driver](./driver_endpoint.md) is authorised to drive a vehicle. In order to create a driver assignment you must first create a [driver assignment quote](./driver_assignment_quote_endpoint.md). Assignments can only be created from **approved** quotes. 
### Create Driver Assignment

`POST /v2/fleet/driver-assignment/`

#### Request Body

| Key | Type | Required | Notes |
| --- | --- | --- | --- |
| assignmentQuoteId | string | yes |  |
| startTime | iso-8601 date time | no | Only required if the assignment quote has no startTime |
| endTime | iso-8601 date time | no | Only required if the assignment quote has no endTime |
| externalId | string | no | Allows you to add your unique identifier for the assignment |

##### Example body

```
{
    "assignmentQuoteId": "fltdar_btoowm25rzdljdm6ln7pon6yry",
    "startTime": "2019-08-01T17:00:00",
    "endTime": "2019-12-01:21:00:00",
    "externalId": "1232",
}
```

##### Example response

HTTP 201

```
{
    "status": "OK",
    "driverAssignment": {
        "id": "fltdau_ese55zccqze6tozzb5hjwtpxie",
        "fleetDriverId": "fltdrv_kiaqgehibbhktagg75drzcssxy",
        "fleetVehicleId": "fltveh_hhz2wvyhdrgnzlt3pc2li24xmm",
        "assignmentQuoteId": "fltdar_btoowm25rzdljdm6ln7pon6yry",
        "startTime": "2019-08-01T17:00:00",
        "endTime": "2019-12-01:21:00:00"
        "externalId": "1232",
        "modifiedAt: "2019-07-29T17:01:02"
    }
}
```

### Get Driver Assignment

Retrieves the details of a driver assignment that has previously been created. Supply the unique driver assignment ID that was returned from your previous request, and Zego will return the corresponding driver assignment information. The same information is returned when creating or updating the driver assignment.

`GET /v2/fleet/driver-assignment/:id/`

##### Example response

HTTP 200

```
{
    "status": "OK",
    "driverAssignment": {
        "id": "fltdau_ese55zccqze6tozzb5hjwtpxie",
        "fleetDriverId": "fltdrv_kiaqgehibbhktagg75drzcssxy",
        "fleetVehicleId": "fltveh_hhz2wvyhdrgnzlt3pc2li24xmm",
        "assignmentQuoteId": "fltdar_btoowm25rzdljdm6ln7pon6yry",
        "startTime": "2019-08-01T17:00:00",
        "endTime": "2019-12-01:21:00:00"
        "externalId": "1232",
        "modifiedAt": "2019-07-29T17:01:02"
        "cancelTime": null
    }
}
```

### List Driver Assignments

Returns a list of driver assignments you’ve previously created.

`GET /v2/fleet/driver-assignment/`


### Search Driver Assignments

Allows you to search driver assignments you’ve previously created.

`GET /v2/fleet/driver-assignment/search?from=fromDateTime&amp;to=toDateTime`

#### Request Params

| Key | Type | Required | Notes |
| --- | --- | --- | --- |
| fromDateTime | iso-8601 date time | no |  |
| toDateTime | iso-8601 date time | no |  |

##### Example response

HTTP 200

```
{
    "status": "OK"
    "driverAssignments": [
        {
            "id": "fltdau_ese55zccqze6tozzb5hjwtpxie",
            "fleetDriverId": "fltdrv_kiaqgehibbhktagg75drzcssxy",
            "fleetVehicleId": "fltveh_hhz2wvyhdrgnzlt3pc2li24xmm",
            "assignmentQuoteId": "fltdar_btoowm25rzdljdm6ln7pon6yry",
            "startTime": "2019-08-01T17:00:00",
            "endTime": "2019-12-01:21:00:00"
            "externalId": "1232",
            "modifiedAt": "2019-07-29T17:01:02"
        },
        {
            "id": "fltdau_ese55zccqze6tozzb5hjwtpxie",
            "fleetDriverId": "fltdrv_kiaqgehibbhktagg75drzcssxy",
            "fleetVehicleId": "fltveh_hhz2wvyhdrgnzlt3pc2li24xmm",
            "assignmentQuoteId": "fltdar_btoowm25rzdljdm6ln7pon6yry",
            "startTime": "2019-08-01T17:00:00",
            "endTime": "2019-12-01:21:00:00"
            "externalId": "1232",
            "modifiedAt: "2019-07-29T17:01:02"
        },
        {
            "id": "fltdau_ese55zccqze6tozzb5hjwtpxie",
            "fleetDriverId": "fltdrv_kiaqgehibbhktagg75drzcssxy",
            "fleetVehicleId": "fltveh_hhz2wvyhdrgnzlt3pc2li24xmm",
            "assignmentQuoteId": "fltdar_btoowm25rzdljdm6ln7pon6yry",
            "startTime": "2019-08-01T17:00:00",
            "endTime": "2019-12-01:21:00:00",
            "externalId": "1232",
            "modifiedAt": "2019-07-29T17:01:02"
        },
    ]
}
```

### Update Driver Assignment

Updates the endTime of the driver assignment. The endTime can only be shortened. You should create a new driver assignment quote if you wish to extend an assignment. The startTime can be when the existing one ends.

`PUT /v2/fleet/driver-assignment/:id/`

#### Request Body

| Key | Type | Required | Notes |
| --- | --- | --- | --- |
| endTime | iso-8601 date time | yes |  |

##### Example response

HTTP 202

```
{
    "status": "OK"
    "driverAssignment": {
        "id": "fltdau_ese55zccqze6tozzb5hjwtpxie",
        "fleetDriverId": "fltdrv_kiaqgehibbhktagg75drzcssxy",
        "fleetVehicleId": "fltveh_hhz2wvyhdrgnzlt3pc2li24xmm",
        "assignmentQuoteId": "fltdar_btoowm25rzdljdm6ln7pon6yry",
        "startTime": "2019-08-01T17:00:00",
        "endTime": "2019-12-01:21:00:00",
        "externalId": "1232",
        "modifiedAt: "2019-07-29T17:01:02"
    }
}
```

### Cancel Driver Assignment

`DELETE /v2/fleet/driver-assignment/:id/`

##### Scenario 1

If you perform a DELETE request on the driver assignment resource that has not started yet this will cancel the driver assignment.

##### Example response

HTTP 202

```
{
    "status": "OK"
    "driverAssignment": {
        "id": "fltdau_ese55zccqze6tozzb5hjwtpxie",
        "fleetDriverId": "fltdrv_kiaqgehibbhktagg75drzcssxy",
        "fleetVehicleId": "fltveh_hhz2wvyhdrgnzlt3pc2li24xmm",
        "assignmentQuoteId": "fltdar_btoowm25rzdljdm6ln7pon6yry",
        "startTime": "2050-08-01T17:00:00",
        "endTime": "2050-08-10:21:00:00"
        "externalId": "1232",
        "modifiedAt: "2019-07-29T17:01:02",
        "cancelTime":  "2019-08-10:21:00:00" // Will be set to now
    }
}
```
##### Scenario 2

If you perform a DELETE request on the driver assignment that is in progress it will set the **endTime** to now.

Performing this action on an assignment may be subject to cancellation charges.

##### Example response

HTTP 202

```
{
    "status": "OK"
    "driverAssignment": {
        "id": "fltdau_ese55zccqze6tozzb5hjwtpxie",
        "fleetDriverId": "fltdrv_kiaqgehibbhktagg75drzcssxy",
        "fleetVehicleId": "fltveh_hhz2wvyhdrgnzlt3pc2li24xmm",
        "assignmentQuoteId": "fltdar_btoowm25rzdljdm6ln7pon6yry",
        "startTime": "2019-08-01T17:00:00",
        "endTime": "2019-08-10:21:00:00", // Will be set to now
        "externalId": "1232",
        "modifiedAt: "2019-07-29T17:01:02",
        "cancelTime":  null
    }
}
```
