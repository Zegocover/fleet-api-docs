## GET /v2/fleet/documents/vehicle/&lt;fleetVehicleId&gt;/

##### Example response

```
headers={
    Content-type: application/pdf
    Content-Disposition: "attachment; filename=vehicle-certificate-ZLPA/H48P7UM-ABDEFGWAGON.pdf"
}

```

**This end point returns a PDF Document**

**Example error**

```
{
    "status": "NOK",
    "error": "INVALID_DATA",
    "message": "Document generation failed",
    "detail": {
        "vehicle certificate": "No vehicle found with ID 12345"
    },
}
```
