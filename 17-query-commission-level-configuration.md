# 1. Query Commission level configuration

```
GET /v1/api/system/levels
```

Query system configuration - Commission level configuration

#### Request Headers

| Name | Required | Type | Description |
| :--- | :--- | :--- | :--- |
| x-api-tenantId | yes | string | Tenant number |
| x-api-token | yes | string | authentication token |

#### Response

| Name | Type | Description |
| :--- | :--- | :--- |
| result | boolean | Success identify ，true stands for success ，false sands for failed |
| mcode | string | Error Code，If Success then return m00000，failure code see the Error code map |
| data | object | Account data |
| errorMessage | List | Error info，some error returns value |

##### 1、data type

| Name | Type | Description |
| :--- | :--- | :--- |
| id | integer | Commission ID |
| level | integer | Commission level |
| name | string | Commission name |

#### Example

**Request sample**

```
GET /v1/api/system/levels
```

Return sample：Success

```json
{
    "data": [
        {
            "id": 1,
            "level": 0,
            "name": "1st level agent 232324"
        },
        {
            "id": 3,
            "level": 1,
            "name": "2nd level agent 111222"
        },
        {
            "id": 4,
            "level": 2,
            "name": "3nd level agent 2222"
        },
        {
            "id": 5,
            "level": 3,
            "name": "IB"
        }
    ],
    "mcode": "m0000000",
    "result": true,
    "time": 1519883581325
}
```

Return sample：failure

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
|  BW\_REQUEST\_TOO\_MUCH | Request too frequently |
| -1 | Service exception, please try later |



