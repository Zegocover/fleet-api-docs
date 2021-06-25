## Driver Authorisations

The driver authorisation object represents a period of time where a [driver] is authorised to drive a vehicle. In order to create a driver authorisation you must first create a [driver authorisation request](./driver_authorisation_quote_endpoint.md). Authorisations can only be created from **approved** requests. 
### Create Driver Authorisation

`POST /v2/fleet/driver-authorisation/`

#### Request Body

| Key | Type | Required | Notes |
| --- | --- | --- | --- |
| authorisationRequestId | int | yes |  |
| startTime | iso-8601 date time | no | Only required if the authorisation request has no startTime |
| endTime | iso-8601 date time | no | Only required if the authorisation request has no endTime |
| externalId | string | no | Allows you to add your unique identifier for the authorisation |

##### Example body

```
{
    "authorisationRequestId": 1,
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
    "driverAuthorisation": {
        "id": 1,
        "fleetDriverId": 12,
        "fleetVehicleId: 21,
        "authorisationRequestId": 1,
        "startTime": "2019-08-01T17:00:00",
        "endTime": "2019-12-01:21:00:00"
        "externalId": "1232",
        "modifiedAt: "2019-07-29T17:01:02"
    }
}
```

### Get Driver Authorisation

Retrieves the details of a driver authorisation that has previously been created. Supply the unique driver authorisation ID that was returned from your previous request, and Zego will return the corresponding driver authorisation information. The same information is returned when creating or updating the driver authorisation.

`GET /v2/fleet/driver-authorisation/&lt;id&gt;/`

##### Example response

HTTP 200

```
{
    "status": "OK",
    "driverAuthorisation": {
        "id": 1,
        "fleetDriverId": 12,
        "fleetVehicleId": 21,
        "authorisationRequestId": 1,
        "startTime": "2019-08-01T17:00:00",
        "endTime": "2019-12-01:21:00:00"
        "externalId": "1232",
        "modifiedAt": "2019-07-29T17:01:02"
        "voidedAt": null
    }
}
```

### List Driver Authorisations

Returns a list of driver authorisations you’ve previously created.

`GET /v2/fleet/driver-authorisation/`


### Search Driver Authorisations

Allows you to search driver authorisations you’ve previously created.

`GET /v2/fleet/driver-authorisation/search?from=fromDateTime&amp;to=toDateTime`

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
    "driverAuthorisations": [
        {
            "id": 1,
            "fleetDriverId": 12,
            "fleetVehicleId": 21,
            "authorisationRequestId": 1,
            "startTime": "2019-08-01T17:00:00",
            "endTime": "2019-12-01:21:00:00"
            "externalId": "1232",
            "modifiedAt": "2019-07-29T17:01:02"
        },
        {
            "id": 1,
            "fleetDriverId": 12,
            "fleetVehicleId: 21,
            "authorisationRequestId": 1,
            "startTime": "2019-08-01T17:00:00",
            "endTime": "2019-12-01:21:00:00"
            "externalId": "1232",
            "modifiedAt: "2019-07-29T17:01:02"
        },
        {
            "id": 1,
            "fleetDriverId": 12,
            "fleetVehicleId": 21,
            "authorisationRequestId": 1,
            "startTime": "2019-08-01T17:00:00",
            "endTime": "2019-12-01:21:00:00",
            "externalId": "1232",
            "modifiedAt": "2019-07-29T17:01:02"
        },
    ]
}
```

### Update Driver Authorisation

Updates the endTime of the driver authorisation. The endTime can only be shortened. You should create a new driver authorisation request if you wish to extend an authorisation. The startTime can be when the existing one ends.

`PUT /v2/fleet/driver-authorisation/&lt;id&gt;/`

#### Request Body

| Key | Type | Required | Notes |
| --- | --- | --- | --- |
| endTime | iso-8601 date time | yes |  |

##### Example response

HTTP 202

```
{
    "status": "OK"
    "driverAuthorisation": {
        "id": 1,
        "fleetDriverId": 12,
        "fleetVehicleId: 21,
        "authorisationRequestId": 1,
        "startTime": "2019-08-01T17:00:00",
        "endTime": "2019-12-01:21:00:00",
        "externalId": "1232",
        "modifiedAt: "2019-07-29T17:01:02"
    }
}
```

### Cancel Driver Authorisation

`DELETE /v2/fleet/driver-authorisation/&lt;id&gt;/`

##### Scenario 1

If you perform a DELETE request on the driver assignment resource that has not started yet this will cancel the driver assignment.

##### Scenario 2

If you perform a DELETE request on the driver assignment that is in progress it will set the **endTime** to now.

Performing this action on an assignment may be subject to cancellation charges.

##### Scenario 1 

##### Example response

HTTP 202

```
{
    "status": "OK"
    "driverAuthorisation": {
        "id": 1,
        "fleetDriverId": 12,
        "fleetVehicleId: 21,
        "authorisationRequestId": 1,
        "startTime": "2050-08-01T17:00:00",
        "endTime": "2050-08-10:21:00:00"
        "externalId": "1232",
        "modifiedAt: "2019-07-29T17:01:02",
        "voidedAt":  "2019-08-10:21:00:00" // Will be set to now
    }
}
```

##### Scenario 2 

##### Example response

HTTP 202

```
{
    "status": "OK"
    "driverAuthorisation": {
        "id": 1,
        "fleetDriverId": 12,
        "fleetVehicleId: 21,
        "authorisationRequestId": 1,
        "startTime": "2019-08-01T17:00:00",
        "endTime": "2019-08-10:21:00:00", // Will be set to now
        "externalId": "1232",
        "modifiedAt: "2019-07-29T17:01:02",
        "voidedAt":  null
    }


}
```
