# Add user

```
POST /v1/api/user/create
```

Add BW user through this interface

#### Request Headers

| Name | Required | Type | Description |
| :--- | :--- | :--- | :--- |
| x-api-tenantId | yes | string | tenant ID |
| x-api-token | yes | string | Authentication token |
| x-language | no | string | language，zh-CN、en-US |

#### Request Body Parameters

| Name | Required | Type | Description |
| :--- | :--- | :--- | :--- |
| email | yes | string | email |
| roleId | yes | integer | user role ID |
| password | no | string | user password，not encrypted。If not sending , then it will automatically generate one |
| levelId | no | integer | User level ID |
| parentId | no | integer | Superior user ID |
| entityNo | no | number | User code，if not sending ,then it will automatically generate one |
| name | no | number | User name |
| address | no | string | address detail |
| phone | no | object | phone data，see phone data type |
| country | no | string | Country ID |
| province | no | string | Province ID |
| city | no | string | City ID |
| comment | no | string | comments |
| sendEmail | no | bool | if to send email or not，if password was not sending then it will surely send emails |
| serverId | no/if login account was sent the server ID is required | integer | server ID |
| login | no | integer | account ID |

1. Phone data type

| Name | Type | Description |
| :--- | :--- | :--- |
| phone | string | Phone |
| countryCode | string | Country code |

#### 

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
| id | long | user ID |
| email | string | email |
| roleId | integer | user role ID |
| password | string | user password，not encrypted。If not sending then it will automatically generate one |
| levelId | integer | user level ID |
| parentId | integer | superior ID |
| entityNo | number | User code |
| name | number | User name |
| address | string | address |
| phone | string | Phone |
| country | string | Country ID |
| province | string | Province ID |
| city | string | City ID |
| comment | string | comments |
| serverId | integer | account serve ID |
| login | integer | account ID |

#### Example

**Request sample**

```
POST /v1/api/suer/create
{
"email":"16819186@qq.com",
"name":"zzz123", 
"roleId":1, 
"phone":{"countryCode":"+86", "phone":"1888888"}, 
"levelId":"10",
"parentId":"4"
}
```

Return sample：success

```json
{
    "data": {
        "email": "16819186123@qq.com",
        "entityNo": "EMIP",
        "id": 286,
        "levelId": 10,
        "name": "zzz123",
        "parentId": 4,
        "password": "9Bf$5Wj@",
        "phone": {
            "countryCode": "+86",
            "phone": "1888888"
        },
        "roleId": 1,
        "sendEmail": false
    },
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

#### Error Code Map

| mcode | MessageBW\_API\_ |
| :--- | :--- |
| BW\_API\_0000001 | token is empty |
| BW\_API\_0000003 | invalid ID |
| BW\_API\_0000004 | No OPENAPI permission |
| PUB\_AUTH\_0000001 | Email format error |
| PUB\_AUTH\_0000002 | Mobile format error |
| PUB\_AUTH\_0000007 | Email has been registered |
| BW\_USER\_NAME\_NULL | User name is empty |
| BW\_USER\_EMAIL\_REPEAT | Email repeat |
| BW\_USER\_ENTITYNO\_REPEAT | User code repeat |
| BW\_USER\_ROLE\_NULL | User role is empty |
| -1 | service exception, try again later |



