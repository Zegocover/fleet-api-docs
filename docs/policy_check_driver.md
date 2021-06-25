## Policy Driver Check

You might want the functionality where you check if a driver meets the criteria of the policy before making an authorisation request. For example, if you want to bail out early of a user onboarding flow and the driver has yet to be assigned to a vehicle.

We allow checking a drivers information against a [policy](./policy_endpoint.md). However this does not guarantee that a driver will be authorised to drive any vehicle on your fleet. You must still always request an authorisation as it will check the combination of both driver and vehicle.

### Driver


`GET /v2/fleet/policy/:id/check-driver/:driverId`

##### Example response

HTTP 200

```
{
  "status": "passed"
}
```

###### Status
|key|Notes|
|---|---|
|passed|Driver meets the underwriting criteria for the policy|
|failed|Driver does not meet the underwriting criteria for the policy|
|missing_information|We don't know enough about the driver to make the decision|