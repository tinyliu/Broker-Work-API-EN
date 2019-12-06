# User login

```
POST /v1/api/user/login
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
| password | yes | string | Password |

#### Response

| Name | Type | Description |
| :--- | :--- | :--- |
| result | boolean | Success ID，if success then return true，others false |
| mcode | string | Error code，if success then return m00000，failure code see error map |
| data | object | Data |
| message | string | Error info, some error returns values |

##### 1、data

| Name | Type | Description |
| :--- | :--- | :--- |
| userId | number | User ID |
| lastLoginTime | number | Last Login Time |

##### 

#### Example

Request sample

```
POST /v1/api/user/login
{
    "email":"aaa@lwork.com",
    "password":"Abcd1234"
}
```

Return sample：success

```json
{
    "data": {
        "lastLoginTime": 1574908245729,
        "userId": 85
    },
    "mcode": "m0000000",
    "result": true,
    "time": 1575366465006
}
```

Return sample：failed

```json
{
    "mcode":"m0000001",
    "message":"",
    "result":false,
    "time":1575366245727
}
```

# 



