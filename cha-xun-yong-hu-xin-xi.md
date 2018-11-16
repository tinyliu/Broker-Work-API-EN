* # Query the specified user information

```
GET /v1/api/user/info?userIds={userIds}
```

Specify user ID to query user information

#### Request Headers

| Name | Required | Type | Description |
| :--- | :--- | :--- | :--- |
| x-api-tenantId | yes | string | Tenant number |
| x-api-token | yes | string | Authentication token |
| x-language | no | string | Language，zh-CN、en-US |

#### Request Parameters

| Name | Required | Type | Description |
| :--- | :--- | :--- | :--- |
| userIds | yes | List | User ID，Support multiple ，using Comma to separate|

#### Response

| Name | Type | Description |
| :--- | :--- | :--- |
| result | boolean | Success ID，return 'true' for success ，'false' for failed|
| mcode | string | Error code，if success then return m00000，failure code see error code map|
| data | object | Table data |
| errorMessage | string | Error info，some error returns value |

##### 1、data type

| Name | Type | Description |
| :--- | :--- | :--- |
| id | long | User ID |
| email | string | Email |
| roleId | integer | User role ID |
| levelId | integer | User level ID |
| parentId | integer | Superior user ID |
| entityNo | number | User code |
| name | number | User name |
| address | string | Address |
| phone | Phone | Phone |
| country | string | Country ID |
| province | string | Province ID |
| city | string | City ID |
| comment | string | Comments |
| serverId | integer | account server ID |
| login | integer | account ID |

#### Example

**Request sample**

```
GET /v1/api/user/info?userIds=71
```

Return sample ：Success

```json
{
    "data": [
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
                "phone": ""
            },
            "province": "",
            "roleId": 2,
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

#### Error code map（Error Code）

| mcode | MessageBW\_API\_ |
| :--- | :--- |
| BW\_API\_0000001 | token is empty |
| BW\_API\_0000003 | Invalid tenantID |
| BW\_API\_0000004 | OPENAPI permission not opened|
| -1 | Service exception,try again later|



