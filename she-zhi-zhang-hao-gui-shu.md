# 1. Configure account ownership

```
POST /v1/api/account/owner
```

#### Request Headers

| Name | Required | Type | Description |
| :--- | :--- | :--- | :--- |
| x-api-tenantId | yes | string | Tenant ID |
| x-api-token | yes | string |  Authentication token |

#### Request Body Parameters

| Name | Required | Type | Description |
| :--- | :--- | :--- | :--- |
| serverId | yes | string | server  |
| accountId | yes | Long | account ID |
| ownerId | yes | string | Owner ID |

#### Response

| Name | Type | Description |
| :--- | :--- | :--- |
| result | boolean |Success ID，if success then return true，others false |
| mcode | string | Error code，if success then return m00000，failure code see error map |
| data | object | account data |
| errorMessage | List | Error info, some error returns values|


#### Example

**Request sample**

```
POST /v1/api/account/owner
```

RequestBody

```json
    {
        "accountId":2109730462, 
        "serverId":"428",
        "ownerId":"7" 
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

# 2. Error handle

#### Error Code map

| mcode | Message |
| :--- | :--- |
| BW\_INVALID\_PARAM | parameters error |
| BW\_INVALID\_SERVERID | invalid serverId |
| -1 | service exception ,try again later |



