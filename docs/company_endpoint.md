## Company

The company object can be associated as the owner of a [Vehicle](./vehicle_endpoint.md). You can retrieve a list of all the companies you created.

### Create Company

`POST /v2/fleet/company/`
#### Request Body

| Key | Type | Required | Notes |
| --- | --- | --- | --- |
| name | string | yes |  |
| registrationNumber | string | no |  |
| addressLine1 | string | yes |  |
| addressLine2 | string | no |  |
| postCode | string | yes |  |
| countryCode | ISO 3166 alpha-2 | yes |  |

##### Example response

HTTP 201

```
{
    "message": "Company created!",
    "status": "OK",
    "company": {
        "id": "fltcom_be3nayyhqbgknoou3nl6oe77rq",
        "name": "Zego",
        "registrationNumber": "101010101",
        "addressLine1": "Tea Room",
        "addressLine2": "Shoreditch"
        "postCode": "E1 123",
        "countryCode": "GB",
    }
}
```

### List Companies

Returns a list of the companies you created. The companies are returned sorted by creation date, with the most recent companies appearing first.

`GET /v2/fleet/company/`

##### Example response

HTTP 200

```
{
  "companies": [
    {
        "id": "fltcom_be3nayyhqbgknoou3nl6oe77rq",
        "name": "Zego"
        "registrationNumber": "101010101",
        "addressLine1": "Tea Room",
        "addressLine2": "Shoreditch"
        "postCode": "E1 123",
        "countryCode": "GB",
    },
    {
        "id": "fltcom_be3nayyhqbgknoou3nl6oe77rq",
        "name": "Zego 2"
        "registrationNumber": "101010102",
        "addressLine1": "8 Orsman Road",
        "addressLine2": ""
        "postCode": "N1 5QJ",
        "countryCode": "GB",
    }
  ]
}
```
