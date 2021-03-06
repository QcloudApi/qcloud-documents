## 1. API Description

This API (GetCdnOverseaPv) is used to query the statistics of number of requests for specified domain on a specified day.

+ There is a statistical point every 5 minutes, and a total of 288 statistical points a day;
+ You may specify a date within the last 30 days;
+ You can query one domain at a time. The domain must have overseas CDN activated.


Domain name for API request:cdn.api.qcloud.com

[Call Demo](https://www.qcloud.com/document/product/228/1734)

## 2. Input Parameters
The following request parameter list only provides API request parameters. Common request parameters need to be added when the API is called. See the [Common Request Parameters](https://www.qcloud.com/doc/api/231/4473) page for details. The Action field for this API is GetCdnOverseaPv.

| Parameter Name | Required | Type     | Description                    |
| ---- | ---- | ------ | --------------------- |
| date | Yes    | String | Specifies query date (within last 30 days) in the format of yyyy-mm-dd. For example: 2016-09-22|
| host  | Yes    | String | Specifies the domain to be queried |


## 3. Output Parameters

| Parameter Name     | Type     | Description                                       |
| -------- | ------ | ---------------------------------------- |
| code     | Int    | Common error code; 0: Succeeded; other values: Failed. For more information, refer to [Common Error Codes](https://www.qcloud.com/doc/api/231/5078#1.-.E5.85.AC.E5.85.B1.E9.94.99.E8.AF.AF.E7.A0.81) |
| message  | String | Module error message description depending on API.                           |
| codeDesc | String | English error message or error code at business side.                           |
| data     | Object | Returned data result, details are described below                            |

#### data Field Description
| Parameter Name           | Type     | Description                                       |
| -------------- | ------ | ---------------------------------------- |
| period         | Int    | Time span of the statistic data, default is 5 minutes                          |
| app_id         | String | Tencent Cloud Services account ([see here](http://console.qcloud.com/cloudAccount)), corresponding to the UIN |
| host           | String | Domain that was specified to be queried                                  |
| start_datetime | String | Start time of the query. If you enter 2016-09-22, the start time will be 2016-09-22 00:00:00 |
| end_datetime   | String | End time of the query. If you enter 2016-09-22, the end time will be 2016-09-22 23:55:00 |
| time_data      | Object | Detailed data regarding the number of requests. Details are described below                           |

#### time_data Field Description
| Parameter Name     | Type    | Description       |
| -------- | ----- | -------- |
| requests | Array | Statistical array of the number of requests |


**Note:**
+ requests is an array of Int type which contains one set a data every 5 minutes, starting from 0:00 on the specified date;
+ The statistics at 00:05:00 represents statistics between 00:00:00 and 00:04:59.

## 4. Example

### 4.1 Example of Input

> date: 2016-09-22
> host: www.test.com


### 4.2 GET Request

All the parameters are required to be added after URL in GET request:

```
https://cdn.api.qcloud.com/v2/index.php?
Action=GetCdnOverseaPv
&SecretId=XXXXXXXXXXXXXXXXXXXXXXXXXXX
&Timestamp=1462422547
&Nonce=12345678
&Signature=XXXXXXXXXXXXXXXXXXXXXXXXX
&date=2016-09-22
&host=www.test.com
```

### 4.3 POST Request

In POST request, the parameters will be filled in HTTP Request-body. The request address is:

```
https://cdn.api.qcloud.com/v2/index.php
```

Such formats of parameters as form-data, x-www-form-urlencoded are supported. The array of parameters is as follows:

```
array (
  'Action' => 'GetCdnOverseaPv',
  'SecretId' => 'XXXXXXXXXXXXXXXXXXXXXXXXXXXX',
  'Timestamp' => 1462782282,
  'Nonce' => 123456789,
  'Signature' => 'XXXXXXXXXXXXXXXXXXXXXXXX',
  'date' => '2016-09-22',
  "host" => 'www.test.com'
)
```

### 4.4 Example of Returned Results

```json
{
    "code": 0,
    "message": "",
    "codeDesc": "Success",
    "data": {
        "period": 5,
        "app_id": 1234567
        "host": "www.test.com",
        "start_datetime": "2016-09-22 00:00:00",
        "end_datetime": "2016-09-22 23:55:00",
        "time_data": {
            "requests": [
            	1,
                2,
                ...
            ]
        }
    }
}
```

