# 1. Query account transaction records

```
GET /v1/api/trade/deal?serverId={serverId}&accountId={accountId}&from={from}&to={to}
```

Query the account transaction info through account ID

#### Request Headers

| Name | Required | Type | Description |
| :--- | :--- | :--- | :--- |
| x-api-tenantId | yes | string | Tenant Number |
| x-api-token | yes | string | Authentication token |

#### Request Parameters

| Name | Required | Type | Description |
| :--- | :--- | :--- | :--- |
| serverId | yes | string | Trading sever ID |
| accountId | yes | string | account login |
| from | no | int | Start Time，timestamp，units milliseconds |
| to | no | int | End Time，timestamp，units milliseconds |

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
| accountId | string | account ID |
| ticket | string | Trading ID |
| openTime | string | Open position time  |
| openPrice | double | Open position price  |
| closeTime | string | Close position time |
| closePrice | double |Close position price |
| type | string | Trading Type |
| symbol | string | Trading symbol |
| volume | double | Trading volume |
| profit | double | Profit/Loss |
| swap | double | Swap |
| commission | double | Commission fee |
| sl | double | Stop loss |
| tp | double | Take profit |

#### Example

**Request sample**

```
GET /v1/api/trade/deal?serverId=428&accountId=1122334496
```

Return sample：success 

```json
{
    "data": [
        {
            "accountId": 1122334496,
            "closePrice": 100.426,
            "closeTime": "2016-08-17 14:50:30",
            "commission": 0,
            "openPrice": 105.67,
            "openTime": "2016-07-21 09:32:52",
            "profit": 522.18,
            "swap": -0.03,
            "symbol": "USDJPY",
            "ticket": 192290,
            "type": "sell",
            "volume": 0.1
        },
        {
            "accountId": 1122334496,
            "closePrice": 1.1275,
            "closeTime": "2016-08-17 14:50:30",
            "commission": -1,
            "openPrice": 1.10639,
            "openTime": "2016-07-20 02:31:22",
            "profit": -2111,
            "swap": -0.28,
            "symbol": "EURUSD",
            "ticket": 192249,
            "type": "sell",
            "volume": 1
        },
        {
            "accountId": 1122334496,
            "closePrice": 1.39099,
            "closeTime": "2016-08-17 14:50:29",
            "commission": -1,
            "openPrice": 1.10639,
            "openTime": "2016-07-19 10:56:20",
            "profit": -28460,
            "swap": -0.29,
            "symbol": "EURUSD",
            "ticket": 192246,
            "type": "sell",
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
| BW\_INVALID\_PARAM | Parameters error |
| BW\_INVALID\_SERVERID | Invalid serverId |
| -1 | Service exception, please try again later|



