# 1. Add promotion links

```
POST /v1/api/introduce/create
```

Add promotion links through the interface

#### Request Headers

| Name | Required | Type | Description |
| :--- | :--- | :--- | :--- |
| x-api-tenantId | yes | string | Tenant ID |
| x-api-token | yes | string | Authentication token |
| x-language | no | string | Language，zh-CN、en-US |

#### Request Body Parameters

| Name | Required | Type | Description |
| :--- | :--- | :--- | :--- |
| name | yes | string | Promotion name |
| entityNo | no | string | Promotion code, if not sending, it will automatically generate one |
| introduceType | yes | string | Agent/StraightGuest |
| visibleType | yes | string | UserAllVisible/UserPartVisible/UserNotVisible |
| visibleUserId | no | array | visible user ID，if configure UserPartVisible，then must be filled in |
| targetUrl | no/if introduceType=StraightGuest，then required | string | target links |
| parameterType | no | string | parameterType，uid/pid/sid |
| serverId | no | string | manager server id |
| vendor | no | bool | if to send email or not，if password was not sending then it surely send emails |
| mtGroup | no | string | custom MT group |
| accountGroup | no | int | custom account group ID |
| leverage | no | int | custom leverage |
| ownerType | no | string | custom owner type，value is RoleId/Id |
| ownerId | no | string | custom owner ID，only WEB and BW hidden user needs this value |
| ownerName | no | string | custom owner name,Redundancy field, for showing |

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
| name | string | Promotion name |
| entityNo | string | Promotion code，if not be filled in, it will automatically generate one |
| introduceType | string | Agent/StraightGuest |
| visibleType | string | UserAllVisible/UserPartVisible/UserNotVisible |
| visibleUserId | array | visible user ID，if configure UserPartVisible，then must be filled in |
| targetUrl | string | target links |
| displayUrl | string | the promotion links when showing |
| parameterType | string | parameterType，uid/pid/sid |
| serverId | string | manager server id |
| vendor | bool | if to send email or not，if password was not set then it surely send emails |
| mtGroup | string | custom MT group |
| accountGroup | int | custom account group ID |
| leverage | int | custom leverage |
| ownerType | string | custom owner type，value is RoleId/Id |
| ownerId | string | custom owner ID，only WEB and BW hidden user needs this value |
| ownerName | string | custom owner name,Redundancy field, for showing |

#### Example

**Request sample**

```
POST /v1/api/introduce/create
{    
    "entityNo":"EN03045"
    ,"name":"apiTest1234"
    , "introduceType":"Agent"
    , "visibleType":"UserPartVisible"
    , "visibleUserId":[1, 2]
    , "targetUrl":"http://www.baidu.com"
    , "parameterType":"uid"
    , "serverId":"428"
    , "vendor":"MT4"
    , "mtGroup":"test"
    , "accountGroup":"group1"
    , "leverage":"100"
    , "ownerType":"Id"
    , "ownerId":"4"
    , "ownerName":"哈哈 steven"
}
```

return sample：success

```json
{    
"data": {
    "entityNo":"EN03045"
    ,"name":"apiTest1234"
    , "introduceType":"Agent"
    , "visibleType":"UserPartVisible"
    , "visibleUserId":[1, 2]
    , "targetUrl":"http://www.baidu.com",
    , "displayUrl":"http://broker.btmsc.lwork.com/introduce?iid=EN03045"
    , "parameterType":"uid"
    , "serverId":"428"
    , "vendor":"MT4"
    , "mtGroup":"test"
    , "accountGroup":"group1"
    , "leverage":"100"
    , "ownerType":"Id"
    , "ownerId":"4"
    , "ownerName":"哈哈 steven"

},
"mcode": "m0000000",
"result": true

}
```

return sample：failed

```json
{
    "mcode": "PUB_AUTH_0000007",
    "result": false
}
```

# 2. Error handle

#### Error Code map

| mcode | MessageBW\_API\_ |
| :--- | :--- |
| BW\_API\_0000001 | token is empty |
| BW\_API\_0000003 | invalid ID |
| BW\_API\_0000004 | No OPENAPI Permission |
| BW\_USER\_INRR\_NAME\_NULL | User name is empty |
| BW\_USER\_INRR\_PARAM\_ERROR | target link repeat with parameterType |
| -1 | service exception , try again later |



