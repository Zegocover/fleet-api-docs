## Authentication

Authenticating with the API requires a token to be set as the AUTHORIZATION header value. The token can requested from your Zego Partnerships Manager. Each fleet will have its own authentication token, so if you are managing multiple fleets make sure to use the correct token in each request.

##### Example header

```
Authorization: 665a023e-58e6-42dd-87c3-12ee61d8d8d7
```

### Re issue authentication API key

`POST /v2/fleet/authentication/reissue`

##### Example response

HTTP 201

```
{
    "message": "Fleet API key updated"
}
```