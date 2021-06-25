## Policy

### Get Policy

`GET /v2/fleet/policy/:id`

##### Example response

HTTP 200

```
{
  "id": "fltpol_bieoesnrpfftvicp2d7xbiratq", 
  "startTime": "2021-07-07T05:00:00+00:00", 
  "endTime": "2022-07-07T12:00:00+00:00"
}
```

### List Policies

`GET /v2/fleet/policy/`

##### Example response

HTTP 200

```
{
    "status": "OK",
    [
      {
        "id": "fltpol_bieoesnrpfftvicp2d7xbiratq", 
        "startTime": "2021-07-07T05:00:00+00:00", 
        "endTime": "2022-07-07T12:00:00+00:00"
      }
    ]
}
```