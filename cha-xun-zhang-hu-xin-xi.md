# 1. Query account info

```
GET /v1/api/account/info?serverId={serverId}&accountId={accountId}
```

Query the account info through account ID


#### Request Headers

| Name | Required | Type | Description |
| :--- | :--- | :--- | :--- |
| x-api-tenantId | yes | string | tenant number |
| x-api-token | yes | string |authentication token |

#### Request Parameters

| Name | Required | Type | Description |
| :--- | :--- | :--- | :--- |
| serverId | yes | string | server ID |
| accountId | yes | List | account ID for login，support multiple ，using comma to separate |

#### Response


| Name | Type | Description |
| :--- | :--- | :--- |
| result | boolean |Success ID，if success then return true，others false |
| mcode | string | Error code，if success then return m00000，failure code see error map |
| data | object | account data |
| errorMessage | List | Error info, some error returns values|


##### 1、data type

| Name | Type | Description |
| :--- | :--- | :--- |
| login | string | account ID |
| currency | string | deposit currency |
| enable | int | login status |
| readOnly | int | trading status |
| sendReports | int | send reports |
| group | string | total records |
| leadSource | int | leadSource |
| leverage | string | leverage |
| regdate | string | register time |
| maxLeverage | int | Max leverage， for ctrader only |
| frenchRisk | bool | French risk，for ctrader only |
| accountType | string | account type |
| totalMarginCalculationType | string | total margin calculation type |
| swapFree | bool |  |
| oweId | string | account owner |

#### Example

**Request sample**

```
GET /v1/api/account/info?serverId=1&accountId=3004273,3004272
```

Return sample：success

```json
{
    "data": [
        {
            "accountType": "HEDGED",
            "currency": "EUR",
            "enable": 1,
            "frenchRisk": false,
            "group": "Default",
            "leadSource": "",
            "leverage": 20,
            "login": "3004272",
            "maxLeverage": 0,
            "readOnly": 0,
            "regdate": "2016-10-05 15:52:47",
            "sendReports": 0,
            "swapFree": false,
            "totalMarginCalculationType": "MAX"
        },
        {
            "accountType": "HEDGED",
            "currency": "USD",
            "enable": 1,
            "frenchRisk": false,
            "group": "HFT",
            "leadSource": "",
            "leverage": 300,
            "login": "3004273",
            "maxLeverage": 0,
            "readOnly": 0,
            "regdate": "2016-10-06 16:02:17",
            "sendReports": 0,
            "swapFree": false,
            "totalMarginCalculationType": "MAX"
        }
    ],
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

#### Error code map（Error Code）

| mcode | Message |
| :--- | :--- |
| BW\_INVALID\_PARAM | Parameters Error |
| BW\_INVALID\_SERVERID | Invalid serverId |
| -1 | Service exception , try again later |



