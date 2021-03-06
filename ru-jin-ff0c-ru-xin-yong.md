# 1. Deposit, Credit in

```
POST /v1/api/account/balance
```

#### Request Headers

| Name | Required | Type | Description |
| :--- | :--- | :--- | :--- |
| x-api-tenantId | yes | string | Tenant ID |
| x-api-token | yes | string | Authentication token |
| x-api-signature | yes | string | "T001117,serverId=XXX,accountId=xxx,amount=xxx", xxx is the data of body |

#### Request Body Parameters

|  | Name | Required | Type | Description |
| :--- | :--- | :--- | :--- | :--- |
|  | serverId | yes | string | server ID |
|  | accountId | yes | Long | account ID |
|  | amount | yes | double | deal amount |
|  | type | yes | string |  Operation type，CREDIT\_IN |
|  | comment | no | string | comment |

#### Response

| Name | Type | Description |
| :--- | :--- | :--- |
| result | boolean | Success ID，if success then return true，others false |
| mcode | string | Error code，if success then return m00000，failure code see error map |
| data | object | account data |
| errorMessage | List | Error info, some error returns values |

#### Example

**Request sample**

```
POST /v1/api/account/balance
```

RequestBody

```json
    {
        "accountId":2109730462, 
        "serverId":"428",
        "amount":5.5, 
        "type":"DEPOSITE",
        "comment":"123" 
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
| BW\_INVALID\_PARAM | parameter error |
| BW\_INVALID\_SERVERID | Invalid serverId |
| -1 | Service exception, try again later |



