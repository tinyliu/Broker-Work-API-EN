# 1. Query account list

```
GET /v1/api/account/list?serverId={serverId}&from={from}&to={to}&page={page}&size={size}
```



#### Request Headers

| Name | Required | Type | Description |
| :--- | :--- | :--- | :--- |
| x-api-tenantId | yes | string | Tenant ID |
| x-api-token | yes | string | Authentication token |

#### Request Parameters

| Name | Required | Type | Description |
| :--- | :--- | :--- | :--- |
| serverId | yes | string | Server ID |
| from | yes | datetime | Start time |
| to | yes | datetime | End time |
| page | no | number | Page, default 1 |
| size | no | number | Size per page, default 20, limitd 200 |

#### Response

| Name | Type | Description |
| :--- | :--- | :--- |
| result | boolean | Success ID，if success then return true，others false |
| mcode | string | Error code，if success then return m00000，failure code see error map |
| data | object | Account Data |
| errorMessage | List | Error info, some error returns values |

##### 1、data

| Name | Type | Description |
| :--- | :--- | :--- |
| list | object | Account list |
| offset | string | Offset |
| pager | int | Current page |
| pages | int | Total pages |
| size | int | Records per page |
| total | string | Total records |

##### 2、list

| Name | Type | Description |
| :--- | :--- | :--- |
| login | number | Login |
| name | string | Name |
| parentId | number | Owen User ID |
| email | string | Email |
| phone | string | Phone |
| group | string | Group |
| leverage | number | Leverage |
| currency | string | Currency |
| regdate | datetime | Create Time |

#### 

#### 

#### 

#### Example

Request sample

```
GET /v1/api/account/list?serverId=428&from=2019-11-01 00:00:00&to=2019-11-27 00:00:00&page=1&size=5
```

Return sample：success

```json
{
    "data": {
        "list": [
            {
                "currency": "USD",
                "email": "329371046@qq.com",
                "group": "jimmy",
                "leverage": 100,
                "login": 330006,
                "name": "jimmy666",
                "parentId": 0,
                "phone": "+86 11111111111",
                "regdate": "2019-11-01 05:34:33"
            },
            {
                "currency": "USD",
                "email": "",
                "group": "amity-online",
                "leverage": 1,
                "login": 2110000262,
                "name": "emilee2@lwork.com",
                "parentId": 27,
                "phone": "",
                "regdate": "2019-11-04 06:13:03"
            },
            {
                "currency": "USD",
                "email": "",
                "group": "amity-online",
                "leverage": 1,
                "login": 2110000263,
                "name": "emilee2@lwork.com",
                "parentId": 27,
                "phone": "",
                "regdate": "2019-11-04 06:13:09"
            },
            {
                "currency": "USD",
                "email": "",
                "group": "amity-online",
                "leverage": 1,
                "login": 2110000264,
                "name": "emilee2@lwork.com",
                "parentId": 27,
                "phone": "",
                "regdate": "2019-11-04 06:13:19"
            },
            {
                "currency": "USD",
                "email": "",
                "group": "amity-online",
                "leverage": 1,
                "login": 2110000265,
                "name": "1019@lwork.com",
                "parentId": 0,
                "phone": "",
                "regdate": "2019-11-04 06:15:04"
            }
        ],
        "offset": 0,
        "pager": 1,
        "pages": 21,
        "size": 5,
        "total": 105
    },
    "mcode": "m0000000",
    "result": true,
    "time": 1575368835183
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



