# Query superior and subordinate info of specified user

```
GET /v1/api/user/getParentAndLowerUserInfo?userId={userId}
```

Specify user ID to query superior and subordinate info

#### Request Headers

| Name | Required | Type | Description |
| :--- | :--- | :--- | :--- |
| x-api-tenantId | yes | string | Tenant number |
| x-api-token | yes | string | authentication token |
| x-language | no | string | language，zh-CN、en-US |

#### Request Parameters

| Name | Required | Type | Description |
| :--- | :--- | :--- | :--- |
| userId | yes | String | User ID |

#### Response

| Name | Type | Description |
| :--- | :--- | :--- |
| result | boolean | Success ID，if success then return true，others false |
| mcode | string | Error code，if success then return m00000，failure code see error map |
| data | object | account data |
| errorMessage | List | Error info, some error returns values |

##### 1、data type

| Name | Type | Description |
| :--- | :--- | :--- |
| id | long | Tenant ID |
| email | string | Email |
| roleId | integer | User role ID |
| levelId | integer | User level ID |
| parentId | integer | Superior user ID |
| entityNo | number | User code |
| name | number | User name |
| address | string | address |
| phone | Phone | phone |
| country | string | country ID |
| province | string | provide ID |
| city | string | city ID |
| comment | string | comments |
| serverId | integer | account server ID |
| login | integer | account ID |

#### Example

**Request sample**

```
GET /v1/api/user/getParentAndLowerUserInfo?userId=4
```

Return sample:success

```json
{
    "data": [
        {
            "address": "",
            "city": "3226",
            "comment": "asd",
            "country": "3225",
            "email": "steven@lwork.com",
            "entityNo": "XOFP",
            "id": 4,
            "levelId": 1,
            "login": 100117,
            "name": "steven12345",
            "parentId": 1,
            "password": "",
            "phone": {
                "countryCode": "",
                "phone": "",
                "phoneStr": " "
            },
            "province": "7045",
            "roleId": 1,
            "sendEmail": false,
            "serverId": 429
        },
        {
            "address": "bbbb",
            "city": "21",
            "comment": "1111",
            "country": "1",
            "email": "sunny@lwork.com",
            "entityNo": "XKVP",
            "id": 1,
            "levelId": 0,
            "name": "Admin",
            "password": "",
            "phone": {
                "countryCode": "+86",
                "phone": "1341 1112222",
                "phoneStr": "+86 1341 1112222"
            },
            "province": "19",
            "roleId": 1,
            "sendEmail": false,
            "serverId": 429
        },
        {
            "address": "",
            "city": "",
            "comment": "",
            "country": "",
            "email": "asd12345@qq.com",
            "entityNo": "SO8T",
            "id": 71,
            "levelId": 6,
            "name": "A1",
            "parentId": 4,
            "password": "",
            "phone": {
                "countryCode": "",
                "phone": "",
                "phoneStr": " "
            },
            "province": "",
            "roleId": 2,
            "sendEmail": false
        },
        {
            "address": "",
            "city": "",
            "comment": "",
            "country": "",
            "email": "ads@asd.com",
            "entityNo": "GYFM",
            "id": 72,
            "levelId": 7,
            "name": "A111",
            "parentId": 71,
            "password": "",
            "phone": {
                "countryCode": "",
                "phone": "",
                "phoneStr": " "
            },
            "province": "",
            "roleId": 2,
            "sendEmail": false
        },
        {
            "address": "",
            "city": "",
            "comment": "",
            "country": "",
            "email": "223@qq.com",
            "entityNo": "NHGO",
            "id": 74,
            "levelId": 4,
            "name": "yona009",
            "parentId": 4,
            "password": "",
            "phone": {
                "countryCode": "",
                "phone": "",
                "phoneStr": " "
            },
            "province": "",
            "roleId": 8,
            "sendEmail": false
        },
        {
            "address": "是",
            "city": "3",
            "comment": "是",
            "country": "1",
            "email": "yona999@lwork.com",
            "entityNo": "JTI9",
            "id": 105,
            "levelId": 3,
            "name": "yona",
            "parentId": 4,
            "password": "",
            "phone": {
                "countryCode": "",
                "phone": "",
                "phoneStr": " "
            },
            "province": "2",
            "roleId": 2,
            "sendEmail": false
        },
        {
            "address": "chengdu",
            "city": "376",
            "comment": "why no drive",
            "country": "1",
            "email": "22222222@zzz.com",
            "entityNo": "2QLJ",
            "id": 143,
            "levelId": 5,
            "login": 1122334532,
            "name": "Jason",
            "parentId": 4,
            "password": "",
            "phone": {
                "countryCode": "",
                "phone": "",
                "phoneStr": " "
            },
            "province": "351",
            "roleId": 4,
            "sendEmail": false,
            "serverId": 428
        },
        {
            "address": "ffffffff",
            "city": "3227",
            "comment": "ggggggggg",
            "country": "3225",
            "email": "steven_test3@qq.com",
            "entityNo": "ZJ3L",
            "id": 233,
            "levelId": 13,
            "login": 123,
            "name": "name1234",
            "parentId": 4,
            "password": "",
            "phone": {
                "countryCode": "+86",
                "phone": "111112",
                "phoneStr": "+86 111112"
            },
            "province": "7045",
            "roleId": 11,
            "sendEmail": false,
            "serverId": 429
        },
        {
            "address": "",
            "city": "3251",
            "comment": "adsds",
            "country": "3249",
            "email": "ssdasd@qq.com",
            "entityNo": "GDLW",
            "id": 258,
            "levelId": 3,
            "name": "123123",
            "parentId": 4,
            "password": "",
            "phone": {
                "countryCode": "",
                "phone": "",
                "phoneStr": " "
            },
            "province": "7046",
            "roleId": 11,
            "sendEmail": false,
            "serverId": 429
        },
        {
            "address": "",
            "city": "21",
            "comment": "是",
            "country": "1",
            "email": "16819186123@qq.com",
            "entityNo": "EMIP",
            "id": 286,
            "levelId": 10,
            "name": "zzz123",
            "parentId": 4,
            "password": "",
            "phone": {
                "countryCode": "",
                "phone": "1888888",
                "phoneStr": " 1888888"
            },
            "province": "19",
            "roleId": 1,
            "sendEmail": false
        },
        {
            "address": "",
            "city": "4",
            "comment": "123213",
            "country": "1",
            "email": "A222@qq.com",
            "entityNo": "HWQD",
            "id": 337,
            "levelId": 16,
            "name": "A222",
            "parentId": 72,
            "password": "",
            "phone": {
                "countryCode": "",
                "phone": "",
                "phoneStr": " "
            },
            "province": "2",
            "roleId": 2,
            "sendEmail": false
        },
        {
            "address": "wewd",
            "city": "37",
            "comment": "sdfsd",
            "country": "1",
            "email": "nature_test2322@lwork.com",
            "entityNo": "LVN8",
            "id": 339,
            "levelId": 3,
            "name": "nature_test2322",
            "parentId": 4,
            "password": "",
            "phone": {
                "countryCode": "+86",
                "phone": "13695985632",
                "phoneStr": "+86 13695985632"
            },
            "province": "36",
            "roleId": 16,
            "sendEmail": false,
            "serverId": 428
        },
        {
            "address": "sdfsdfsda",
            "city": "3226",
            "comment": "sfdasfd",
            "country": "3225",
            "email": "naturetest1@lwork.com",
            "entityNo": "E25F",
            "id": 393,
            "levelId": 6,
            "name": "naturetest1",
            "parentId": 105,
            "password": "",
            "phone": {
                "countryCode": "",
                "phone": "",
                "phoneStr": " "
            },
            "province": "7045",
            "roleId": 32,
            "sendEmail": false,
            "serverId": 428
        },
        {
            "address": "chengdu",
            "city": "61",
            "comment": "sdf",
            "country": "1",
            "email": "sdfsdaf@lowk.com",
            "entityNo": "V1JN",
            "id": 401,
            "levelId": 17,
            "name": "dsdfsdaf",
            "parentId": 339,
            "password": "",
            "phone": {
                "countryCode": "",
                "phone": "",
                "phoneStr": " "
            },
            "province": "36",
            "roleId": 7,
            "sendEmail": false
        }
    ],
    "mcode": "m0000000",
    "result": true
}
```

Return sample：failed

```json
{
    "mcode": "PUB_AUTH_0000007",
    "result": false
}
```

# 2. Error handle

#### Error caode map（Error Code）

| mcode | MessageBW\_API\_ |
| :--- | :--- |
| BW\_API\_0000001 | token is empty |
| BW\_API\_0000003 | invalid ID |
| BW\_API\_0000004 | permission of OPENAPI not opened |
| -1 | service exception, try again later |



