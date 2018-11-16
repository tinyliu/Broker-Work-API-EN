# 1. Query account holding position

```
GET /v1/api/trade/position?serverId={serverId}&accountId={accountId}&from={from}&to={to}
```

Query the account holding position info through account ID

#### Request Headers

| Name | Required | Type | Description |
| :--- | :--- | :--- | :--- |
| x-api-tenantId | yes | string | tenant number |
| x-api-token | yes | string | authentication token |

#### Request Parameters

| Name | Required | Type | Description |
| :--- | :--- | :--- | :--- |
| serverId | yes | string | trading server ID |
| accountId | yes | string | account login |
| from | no | int | Start Time，timestamp，unit,millisecond |
| to | no | int | End time，timestamp，unit,millisecond |

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
| accountId | string | Account ID |
| ticket | string | Trading ID |
| openTime | string | Open position time |
| openPrice | double | Open position price |
| type | string | Trading type |
| symbol | string | Trading symbol |
| volume | double | Trading volume |
| profit | double | Profit/Loss |
| sl | double | Stop loss |
| tp | double | Take profit |

#### Example

**Request sample**

```
GET /v1/api/trade/position?serverId=428&accountId=1234580230
```

Return sample：success

```json
{
    "data": [
        {
            "accountId": 1234580230,
            "openPrice": 1.17294,
            "openTime": "2017-08-16 06:26:21",
            "profit": 1929,
            "sl": 0,
            "symbol": "EURUSD",
            "ticket": 3215317,
            "tp": 0,
            "type": "buy",
            "volume": 1
        },
        {
            "accountId": 1234580230,
            "openPrice": 1.17393,
            "openTime": "2017-08-16 03:25:53",
            "profit": 1830,
            "sl": 0,
            "symbol": "EURUSD",
            "ticket": 3215316,
            "tp": 0,
            "type": "buy",
            "volume": 1
        },
        {
            "accountId": 1234580230,
            "openPrice": 1.17394,
            "openTime": "2017-08-16 03:25:41",
            "profit": 1829,
            "sl": 0,
            "symbol": "EURUSD",
            "ticket": 3215315,
            "tp": 0,
            "type": "buy",
            "volume": 1
        },
        {
            "accountId": 1234580230,
            "openPrice": 1.17387,
            "openTime": "2017-08-16 03:24:37",
            "profit": -1855,
            "sl": 0,
            "symbol": "EURUSD",
            "ticket": 3215314,
            "tp": 0,
            "type": "sell",
            "volume": 1
        },
        {
            "accountId": 1234580230,
            "openPrice": 1.17263,
            "openTime": "2017-08-16 06:28:21",
            "profit": 1960,
            "sl": 0,
            "symbol": "EURUSD",
            "ticket": 3215313,
            "tp": 0,
            "type": "buy",
            "volume": 1
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
| BW\_INVALID\_PARAM | Parameter Error |
| BW\_INVALID\_SERVERID | Invalid serverId |
| -1 | Service exception , try again later |



