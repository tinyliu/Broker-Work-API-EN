# 1. Open commission account 

```
POST /v1/api/account/openCommissionAccount
```

#### Request Headers

| Name | Required | Type | Description |
| :--- | :--- | :--- | :--- |
| x-api-tenantId | yes | string | Tenant number |
| x-api-token | yes | string | Authentication token |

#### Request Body Parameters

| Name | Required | Type | Description |
| :--- | :--- | :--- | :--- |
| serverId | yes | string | server number |
| login | no | Long | account login |
| enable | yes | integer | login status，0 disable for login ，1 enable for login |
| readOnly | yes | interger | trading status，0 enable for trading ，1 disable for trading |
| group | yes | string | MT Group |
| leverage | yes | integer | Leverage |
| customerId | no | string | CustomerID |
| email | no | string | email |
| phone | no | object | phone，detail see data types|
| name | yes | string | Name |
| password | no | string | Master password |
| investorPassword | no | string | Investor password |

Phone data type

| Name | Type | Description |
| :--- | :--- | :--- |
| phone | string | Phone |
| countryCode | string | Country code |

#### Response


| Name | Type | Description |
| :--- | :--- | :--- |
| result | boolean |Success ID，if success then return true，others false |
| mcode | string | Error code，if success then return m00000，failure code see error map |
| data | object | account data |
| errorMessage | List | Error info, some error returns values|

Account info

| Name | Type | Description |
| :--- | :--- | :--- |
| serverId | string | Server ID |
| login | integer | account |
| password | string | Master password |
| investorPassword | string | Investor password |

#### Example

**Request sample**

```
POST /v1/api/account/openCommissionAccount
```

RequestBody

```json
    {
        "serverId": "428",
        "group":"OliTestCFH15",
        "userGroup":"9",
        "leverage":"1",
        "userId":4,
        "leadSource":"asd",
        "sendReports":"1",
        "readOnly":"1",
        "enable":"1",
        "name":"stevenadd",
        "phone":{"phone":"123123123", "countryCode":"+86"},
        "email":"steven@lwork.com"
    }
```

Return sample：success

```json
{
    "data": {
        "investorPassword": "3o9c4m",
        "login": "20004",
        "password": "9s2d1v",
        "serverId": "428"
    },
    "mcode": "m0000000",
    "result": true
}
```

Return sample：failed

```json
{
    "mcode": "MT4_3",
    "message": "",
    "result": false
}
```

# 2. Error handle

#### Error code map 

| mcode | Message |
| :--- | :--- |
| BW\_INVALID\_PARAM | parameters error |
| BW\_INVALID\_SERVERID | Invalid serverId |
| -1 | Service exception，try again later |



