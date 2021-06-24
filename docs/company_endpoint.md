## Company

### Get Company

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
        "id": 48,
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

`GET /v2/fleet/company/`

##### Example response

HTTP 200

```
{
  "companies": [
    {
        "id": 48,
        "name": "Zego"
        "registrationNumber": "101010101",
        "addressLine1": "Tea Room",
        "addressLine2": "Shoreditch"
        "postCode": "E1 123",
        "countryCode": "GB",
    },
    {
        "id": 49,
        "name": "Drover"
        "registrationNumber": "101010102",
        "addressLine1": "8 Orsman Road",
        "addressLine2": ""
        "postCode": "N1 5QJ",
        "countryCode": "GB",
    }
  ]
}
```
