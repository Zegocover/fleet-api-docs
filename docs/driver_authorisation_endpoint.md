## Driver Authorisation

The driver authorisation object represents a period of time where an approved [driver](./driver_endpoint.md) is authorised to drive an insured vehicle on your policy. This can then be used to generate a letter of authorisation. It's not an indication of insurance, see the driver assignment documentation if you would like a driver and vehicle to be insured together.
### Create Driver authorisation

`POST /v2/fleet/driver-authorisation/`

#### Request Body

| Key | Type | Required | Notes |
| --- | --- | --- | --- |
| policyId | string | yes |  |
| fleetVehicleId | string | yes |  |
| fleetDriverId | string | yes |  |
| startTime | iso-8601 date time | no | Must be between the cover period for the vehicle. |
| endTime | iso-8601 date time | no | Must be between the cover period for the vehicle. |

##### Example body

```
{
	"policyId": "fltpol_yxsmj3dadfh7zaj5lvr3hsqeue",
	"fleetVehicleId": "fltveh_vphjyzcl6bhyvku5l6oap2iiqq",
	"fleetDriverId": "fltdrv_bezvvs2fcrhalivycd77cwwy7a",	
	"startTime": "2021-01-10T00:00:00Z",
	"endTime": "2021-02-10T00:00:00Z"
}
```

##### Example response

HTTP 201

```
{
  "startTime": "2021-01-10T00:00:00+00:00",
  "endTime": "2021-02-10T00:00:00+00:00",
  "id": "fltdau_4ik3biuptraztez7u34pdzgguq",
  "policyId": "fltpol_yxsmj3dadfh7zaj5lvr3hsqeue",
  "fleetDriverId": "fltdrv_bezvvs2fcrhalivycd77cwwy7a",
  "fleetVehicleId": "fltveh_vphjyzcl6bhyvku5l6oap2iiqq"
}
```

### Get Driver Authorisation

Retrieves the details of a driver authorisation that has previously been created. Supply the unique driver authorisation ID that was returned from your previous request, and Zego will return the corresponding driver authorisation information. The same information is returned when creating or updating the driver authorisation.

`GET /v2/fleet/driver-authorisation/:id/`

##### Example response

HTTP 200

```
{
  "startTime": "2021-01-10T00:00:00+00:00",
  "endTime": "2021-02-10T00:00:00+00:00",
  "id": "fltdau_4ik3biuptraztez7u34pdzgguq",
  "policyId": "fltpol_yxsmj3dadfh7zaj5lvr3hsqeue",
  "fleetDriverId": "fltdrv_bezvvs2fcrhalivycd77cwwy7a",
  "fleetVehicleId": "fltveh_vphjyzcl6bhyvku5l6oap2iiqq"
}
```

### Update Driver authorisation

Updates the startTime or endTime of the driver authorisation. These dates must be within the cover period of the vehicle.

`PUT /v2/fleet/driver-authorisation/:id/`

#### Request Body

| Key | Type | Required | Notes |
| --- | --- | --- | --- |
| startTime | iso-8601 date time | yes |  |
| endTime | iso-8601 date time | yes |  |


##### Example body

```
{
	"startTime": "2021-01-10T00:00:00+00:00",
	"endTime": "2021-02-10T00:00:00+00:00"
}
```

##### Example response

HTTP 202

```
{
  "startTime": "2021-01-10T00:00:00+00:00",
  "endTime": "2021-02-10T00:00:00+00:00",
  "id": "fltdau_4ik3biuptraztez7u34pdzgguq",
  "policyId": "fltpol_yxsmj3dadfh7zaj5lvr3hsqeue",
  "fleetDriverId": "fltdrv_bezvvs2fcrhalivycd77cwwy7a",
  "fleetVehicleId": "fltveh_vphjyzcl6bhyvku5l6oap2iiqq"
}
```
