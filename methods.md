# 1. User commission table

```
POST /v1/api/report/user/commission
```


Use this interface to query the user commission status in the specified date range. If there are more subordinate users in the specified user and the transaction volume of these users is particularly large, 
it is recommended that the date range of the query should not be too large. For example, you can query only one day's data at a time, then multiple requests.


#### Request Headers

| Name | Required | Type | Description |
| :--- | :--- | :--- | :--- |
| x-api-tenantId | yes | string | Tenant ID |
| x-api-token | yes | string | Authentication token |
| x-language | no | string | Language，zh-CN、en-US |

#### Request Parameters

| Name | Required | Type | Description |
| :--- | :--- | :--- | :--- |
| userId | yes | string | User ID |
| serverId | yes | string | Configure MT Server number |
| level | yes | string | Level range：0 All 、1Direct Subordinate、2Indirect Subordinate |
| start | no | string | Start time，format：2017-01-01，custom today |
| end | no | string | End time，format：2017-01-01，custom today |
| index | no | number | Page no，custom：1 |
| pageSize | no | number | Items per page，custom 20，more than 500，return 500 |

#### Response


| Name | Type | Description |
| :--- | :--- | :--- |
| result | boolean |Success ID，if success then return true，others false |
| mcode | string | Error code，if success then return m00000，failure code see error map |
| data | object | account data |
| errorMessage | List | Error info, some error returns values|

##### 1、data type

| Name | Type | Description |
| :--- | :--- | :--- |
| list | List | request data list |
| offset | number | offset value |
| pager | number | Current page |
| pages | number | Total pages |
| total | number | Total Items |

##### 2、List data list

| Name | Type | Description |
| :--- | :--- | :--- |
| closeVolume | double | close position volume |
| commissionValue | double | commission fee |
| date | string | Data，format：2017-01-01 |
| levelId | number | level ID |
| login | number | account number for the user |
| parentId | number | Superior user number |
| userId | number | User ID |
| details | List | Commission details |
| -- closeVolume | double | close position lots |
| -- commissionValue | double | commission fee |
| -- symbol | string | symbol code |

#### Example

**Request sample**

```
POST /v1/api/report/user/commission
{
    "serverId":"454",
    "userId":"2",
    "level":"0",
    "start":"2017-08-01",
    "end":"2017-09-01"
}
```

Return sample：success

```json
{
    "mcode":"m0000000",
    "result":true,
    "data":{
        "list":[
            {
                "closeVolume":1,
                "commissionValue":51.09,
                "date":"2017-08-15",
                "details":[
                    {
                        "closeVolume":1,
                        "commissionValue":51.09,
                        "resultId":1,
                        "symbol":"USDCHF"
                    }
                ],
                "levelId":6,
                "login":123123,
                "parentId":4,
                "userId":2
            },
            {......},
            {......}
        ],
        "offset":0,
        "pager":1,
        "pages":2,
        "size":20,
        "total":24
    }
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

# 2. Error handle

#### Error Code map

| mcode | Message |
| :--- | :--- |
| BW\_REPORT\_0000 | parameters error|
| RIGHT\_NO\_00000001 | No permission to view this data |
| BW\_REPORT\_0022 | User not exist |
| BW\_REPORT\_0023 | serverId not exist |
| -1 | service exception，try later |



