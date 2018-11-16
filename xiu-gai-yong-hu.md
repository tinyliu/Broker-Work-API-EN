# Modify user

```
POST /v1/api/user/info
```
Modify user through this interface 

#### Request Headers

| Name | Required | Type | Description |
| :--- | :--- | :--- | :--- |
| x-api-tenantId | yes | string | Tenant ID |
| x-api-token | yes | string |  Authentication token |
| x-language | no | string | language，zh-CN、en-US |

#### Request Body Parameters

| Name | Required | Type | Description |
| :--- | :--- | :--- | :--- |
| id | yes | integer | user ID |
| roleId | no | integer | user role ID |
| levelId | no | integer | user level ID |
| parentId | no | integer | superior ID |
| entityNo | no | number | user code, it not sending then it will automatically generate one |
| name | no | number | user name  |
| address | no | string | address detail |
| phone | no | object | phone data ，see phone data type |
| country | no | string | country ID |
| province | no | string | province ID |
| city | no | string | country ID |
| comment | no | string | comments |
| serverId | no | integer | Manager server ID |
| login | no | integer | account ID |

1. Phone data type 

| Name | Type | Description |
| :--- | :--- | :--- |
| phone | string | phone  |
| countryCode | string | country code |

#### 

#### Response

| Name | Type | Description |
| :--- | :--- | :--- |
| result | boolean |Success ID，if success then return true，others false |
| mcode | string | Error code，if success then return m00000，failure code see error map |
| data | object | account data |
| errorMessage | List | Error info, some error returns values|


#### Example

**Request sample**

```
POST /v1/api/user/info
{
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
| BW\_API\_0000004 | No OPENAPI Permission |
| PUB\_AUTH\_0000002 | Mobile format error |
| PUB\_AUTH\_0000007 | Email been registered |
| BW\_USER\_NAME\_NULL | User name is empty|
| BW\_USER\_ENTITYNO\_REPEAT | User code repeat |
| -1 | service exception , try again later |
| bw-user\_1008 | Email exists |
| bw-user\_1007 | Generate code error |
| bw-user\_1009 | role not exists |
| bw-user\_1010 | level not exists |
| bw-user\_1013 | name already exists |
| bw-user\_1014 | Loop check does not pass|
| bw-user\_1016 | Authority Sid illegal|
| bw-user\_1018 | account already exists |
| bw-user\_1019 | Code already exists |
| bw-user\_1020 | Commission level should not be higher than the superior level |



