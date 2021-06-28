## Driver Authorisation Vehicle Certificate


### Get Driver Authorisation Vehicle Certificate

`GET /v2/fleet/documents/driver-authorisation/vehicle/:id/`

##### Example response

HTTP 200

```
headers={
    Content-type: application/pdf
    Content-Disposition: "attachment; filename=zego-authorization-ZLPA/H48P7UM-ABDEFGWAGON.pdf"
}
```

**This end point returns a PDF Document**

##### Example response

HTTP 400

```
{
    "status": "NOK",
    "error": "INVALID_DATA",
    "message": "Document generation failed",
    "detail": {
        "fleet driver assignment document": "Fleet vehicle membership dates do not overlap with policy dates"
    },
}
```
