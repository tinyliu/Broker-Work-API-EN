# 1. Configure custom owner

```
POST /v1/api/custom/owner
```

#### Request Headers

| Name | Required | Type | Description |
| :--- | :--- | :--- | :--- |
| x-api-tenantId | yes | string | Tenant ID |
| x-api-token | yes | string | Authentication token |

#### Request Body Parameters

| Name | Required | Type | Description |
| :--- | :--- | :--- | :--- |
| customId | yes | string | Custom ID |
| commendId | no | string | New referrer ID |
| oweId | no | string | New owner ID |

#### Response

| Name | Type | Description |
| :--- | :--- | :--- |
| result | boolean | Success ID，if success then return true，others false |
| mcode | string | Error code，if success then return m00000，failure code see error map |
| message | List | Error info, some error returns values |

#### Example

Request sample

```
POST /v1/api/custom/owner
```

RequestBody

```json
    {
    "customId":"fc25ecba-e77e-41b9-94c2-d24e1d9cb89e",
    "oweId":"87",
    "commendId":"80eb3bbb-8d1d-434d-a495-6ec830ca09ec"

}
```

Return sample：success

```json
{
    "mcode": "m0000000",
    "result": true
}
```

Return sample：failed

```json
{
    "mcode":"m0000001",
    "errorMessage":"",
    "result":false
}
```

# 



