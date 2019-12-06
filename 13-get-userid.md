# Get userID

```
GET /v1/api/user/ids?email={email}
```

#### Request Headers

| Name | Required | Type | Description |
| :--- | :--- | :--- | :--- |
| x-api-tenantId | yes | string | Tenant ID |
| x-api-token | yes | string | Authentication token |
| x-language | no | string | Language，zh-CN、en-US |

#### Request Parameters

| Name | Required | Type | Description |
| :--- | :--- | :--- | :--- |
| email | yes | string | Email |

#### Response

| Name | Type | Description |
| :--- | :--- | :--- |
| result | boolean | Success ID，if success then return true，others false |
| mcode | string | Error code，if success then return m00000，failure code see error map |
| data | object | User Data |
| message | string | Error info, some error returns values |

##### 1、data数据类型

| Name | Type | Description |
| :--- | :--- | :--- |
| userId | long | User ID |
| email | string | Email |

#### Example

Request sample

```
GET /v1/api/user/info?email=71
```

Return sample：success

```json
{
    "data": [
        {
            "email": "asd12345@qq.com",
            "userId": 71
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

# 



