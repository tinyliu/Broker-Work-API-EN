# 1. Query custom list

```
GET /v1/api/custom/info?from={from}&to={to}&page={page}&size={size}
```

#### Request Headers

| Name | Required | Type | Description |
| :--- | :--- | :--- | :--- |
| x-api-tenantId | yes | string | Tenant ID |
| x-api-token | yes | string | Authentication token |

#### Request Parameters

| Name | Required | Type | Description |
| :--- | :--- | :--- | :--- |
| from | yes | datetime | Start time |
| to | yes | datetime | End time |
| page | no | number | Page, default 1 |
| size | no | number | Size per page, default 20，limitd 200 |

#### Response

| Name | Type | Description |
| :--- | :--- | :--- |
| result | boolean | Success ID，if success then return true，others false |
| mcode | string | Error code，if success then return m00000，failure code see error map |
| data | object | Custom data |
| errorMessage | List | Error info, some error returns values |

##### 1、data

| Name | Type | Description |
| :--- | :--- | :--- |
| list | object | Custom list |
| offset | string | offset |
| pager | int | Current page |
| pages | int | Total pages |
| size | int | Records per page |
| total | string | Total Records |

##### 2、list数据类型

| Name | Type | Description |
| :--- | :--- | :--- |
| \_id | string | Custom id |
| customName | string | Custom Name |
| email | string | Email |
| customNo | string | Custom No. |
| oweId | string | Custom owner  |
| customerState | string | State |
| commendId | string | Referrer ID |
| phones | json | Phone |
| createTime | datetime | Create time |

#### 

#### 

#### 

#### Example

Request sample

```
GET /v1/api/custom/info?from=2019-11-01 00:00:00&to=2019-11-27 00:00:00&page=1&size=2
```

Return sample：success

```json
{
    "data": {
        "list": [
            {
                "_id": "c4699d03-ad43-4457-a418-6cd0a72483a6",
                "customName": "emilee2@lwork.com",
                "email": "",
                "customNo": "CNPP2F",
                "oweId": "27",
                "customerState": "Potential",
                "createTime": "2019-11-04 14:13:09"
            },
            {
                "_id": "8dd153a3-36ad-4d97-bf6a-26bdd643c9a0",
                "customName": "emilee2@lwork.com",
                "email": "",
                "customNo": "CYLE2U",
                "oweId": "27",
                "customerState": "Potential",
                "createTime": "2019-11-04 14:13:19"
            }
        ],
        "offset": 0,
        "pager": 1,
        "pages": 94,
        "size": 2,
        "total": 188
    },
    "mcode": "m0000000",
    "result": true,
    "time": 1575448536727
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



