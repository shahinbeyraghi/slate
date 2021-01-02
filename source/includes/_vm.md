# VM Endpoints














## Create VM

```shell
curl --location --request PUT '{baseUrl}/vm/createVm' \
--header 'Authorization: Basic {token}' \

```

```php
$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => '{baseUrl}/vm/createVm',
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => '',
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => true,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => 'PUT',
  CURLOPT_HTTPHEADER => array(
    'Authorization: Basic {token}',
  ),
));

$response = curl_exec($curl);
curl_close($curl);
echo $response;
```

> The above command returns JSON structured like this:

```json
{
  "success": true,
  "data": {
    "price": 5000,
    "estimated_exec_time": 89,
    "jid": 1994,
    "vmpass": "mCGTymjqLgy5qC",
    "ip": "185.208.172.17",
    "oid": 192,
    "vmid": 384108,
    "srv": 500219,
    "message": "Server created successfully"
  }
}
```

This endpoint create a vm.

### HTTP Request

`POST {baseUrl}/vm/createVm`

### Query Parameters

Parameter      | Required | Type     | Acceptable Values                                       | Description
---------      | -------  | -------- | -----------------------------                           | -----------
title          | true     | string   | ^[A-Za-z0-9- ]+$                                        | Set vm title
os             | true     | string   | ^[A-Za-z0-9-._ ]+$ (os list is [here](#get-os-list))    | Set vm os
location       | true     | string   | ir,eu                                                   | set location value
ram            | true     | integer  | min requirement ram for choosen os (1024-16384)         | Set ram amount
cpu            | true     | integer  | min requirement cpu for choosen os (1-16)               | Set cpu cores count
hdd            | true     | integer  | min requirement hdd for choosen os (25-150)             | Set HDD space
voucher        | false    | string   | ^[A-Za-z0-9]+$                                          | Set voucher
node_id        | false    | integer  | choosen location node id                                | Set node id
storage_id     | false    | integer  | specific storage id                                     | Set storage id
ip_pool_id     | false    | integer  | specific ip pool id                                     | Set ip pool id
project_id     | false    | integer  | your specific project id                                | Set project id


### Response Parameters
Parameter               | Description
------------------      | -----------
price                   | Daily price for this VM
estimated_exec_time     | Estimate to build VM
jid                     | Creation VM job id
vmpass                  | SSH VM password
ip                      | VM IP
oid                     | Order id
vmid                    | VM id
srv                     | Server id
message                 | Creation message

### Errors Sample

Success | Data
---------- | -------
false | Invalid parameters -- one if post data pattern is wrong
false | Invalid parameters -- wrong os
false | access_denied -- project is not yours
false | Iran cloud user must be from iran -- turn of vpn



















## Start VM

```shell
curl --location --request POST '{baseUrl}/vm/{vmId}/start' \
--header 'Authorization: Basic {token}' \

```

```php
$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => '{baseUrl}/vm/{vmId}/start',
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => '',
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => true,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => 'POST',
  CURLOPT_HTTPHEADER => array(
    'Authorization: Basic {token}',
  ),
));

$response = curl_exec($curl);
curl_close($curl);
echo $response;
```

> The above command returns JSON structured like this:

```json
{
  "success": true,
  "data": "Server successfully started"
}
```

This endpoint start specific vm.

### HTTP Request

`PUT {baseUrl}/vm/{vmId}/start`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
{vmId} | null | Set vm id


### Errors Sample

Success | Data
---------- | -------
false | Server is not running


<aside class="notice">
Remember change {vmID} with your vm id in url
</aside>














## Stop VM

```shell
curl --location --request POST '{baseUrl}/vm/{vmId}/stop' \
--header 'Authorization: Basic {token}' \

```

```php
$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => '{baseUrl}/vm/{vmId}/stop',
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => '',
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => true,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => 'POST',
  CURLOPT_HTTPHEADER => array(
    'Authorization: Basic {token}',
  ),
));

$response = curl_exec($curl);
curl_close($curl);
echo $response;
```

> The above command returns JSON structured like this:

```json
{
  "success": true,
  "data": "Server successfully stopped"
}
```

This endpoint stop specific vm.

### HTTP Request

`PUT {baseUrl}/vm/{vmId}/stop`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
{vmId} | null | Set vm id


### Errors Sample

Success | Data
---------- | -------
false | Server is not running


<aside class="notice">
Remember change {vmID} with your vm id in url
</aside>














## Restart VM

```shell
curl --location --request POST '{baseUrl}/vm/{vmId}/reset' \
--header 'Authorization: Basic {token}' \

```

```php
$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => '{baseUrl}/vm/{vmId}/reset',
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => '',
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => true,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => 'POST',
  CURLOPT_HTTPHEADER => array(
    'Authorization: Basic {token}',
  ),
));

$response = curl_exec($curl);
curl_close($curl);
echo $response;
```

> The above command returns JSON structured like this:

```json
{
  "success": true,
  "data": "Server successfully restarted"
}
```

This endpoint restart specific vm.

### HTTP Request

`PUT {baseUrl}/vm/{vmId}/reset`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
{vmId} | null | Set vm id


### Errors Sample

Success | Data
---------- | -------
false | Server is not running


<aside class="notice">
Remember change {vmID} with your vm id in url
</aside>

















## Get all your VMs

```shell
curl --location --request GET '{baseUrl}/vm' \
--header 'Authorization: Basic {token}'
```

```php
$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => '{baseUrl}/vm',
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => '',
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => true,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => 'GET',
  CURLOPT_HTTPHEADER => array(
    'Authorization: Basic {token}',
  ),
));

$response = curl_exec($curl);
curl_close($curl);
echo $response;
```

> The above command returns JSON structured like this:

```json
{
  "success": true,
  "data": [
    {
      "srv": 500088,
      "vmstatus": "running",
      "vmtitle": "test2",
      "vmos": "CentOS7-CI",
      "vmtype": "commercial",
      "vmostype": "centos",
      "lock_reason": "lockForBuild",
      "srv_status": "active",
      "suspendreason": [
        "Suspend because of credit"
      ],
      "project_id": null,
      "id": 80,
      "iscommercial": true,
      "isPrivateCloud": false,
      "issuspend": true,
      "dedicatedip": "185.208.172.18",
      "connectionstatus": "",
      "domainstatus": "Active",
      "notes": ""
    },
    {
      "srv": 500105,
      "vmstatus": "stopped",
      "vmtitle": "test5",
      "vmos": "ubuntu16-nolvm",
      "vmtype": "commercial",
      "vmostype": "ubuntu",
      "lock_reason": "lockForBuild",
      "srv_status": "active",
      "suspendreason": [
        ""
      ],
      "project_id": null,
      "id": 96,
      "iscommercial": true,
      "isPrivateCloud": false,
      "issuspend": false,
      "dedicatedip": "185.208.172.25",
      "connectionstatus": "در حال بررسی توسط تیم پشتیبانی",
      "domainstatus": "Active",
      "notes": ""
    }
  ]
}
```

This endpoint retrieves your all servers.

### HTTP Request

`GET {baseUrl}/vm`




















## Get VM info

```shell
curl --location --request GET '{baseUrl}/vm/{vmId}/info' \
--header 'Authorization: Basic {token}'
```

```php
$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => '{baseUrl}/vm/{vmId}/info',
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => '',
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => true,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => 'GET',
  CURLOPT_HTTPHEADER => array(
    'Authorization: Basic {token}',
  ),
));

$response = curl_exec($curl);
curl_close($curl);
echo $response;
```

> The above command returns JSON structured like this:

```json
{
  "success": true,
  "data": {
    "location": "eu",
    "ram": 1024,
    "cpu": 1,
    "hdd": 25,
    "status": "running",
    "title": "test2",
    "vp": "faPwN8imsZz8nQ",
    "os": "CentOS7-CI",
    "ostype": "centos",
    "type": "commercial",
    "dailyBudget": -1,
    "guestagent": 0,
    "ip": "185.208.172.18",
    "srv": 500088,
    "project_id": null,
    "isfree": false,
    "iscommercial": true,
    "isPrivateCloud": false,
    "charge": 3600,
    "id": 80,
    "domainstatus": "Active",
    "notes": "",
    "bandwidthUsage": 0,
    "bandwidthLimit": 0,
    "dlBandwidthUsage": 0
  }
}
```

This endpoint retrieves your vm info.

### HTTP Request

`GET {baseUrl}/vm/{vmId}/info`

### Query Parameters
Parameter | Default | Description
--------- | ------- | -----------
{vmId} | null | Set vm id

### Errors Sample
Success | Data
---------- | -------
false | null -- VM not exist.


<aside class="notice">
Remember change {vmID} with your vm id in url
</aside>











## Get VM ips list

```shell
curl --location --request GET '{baseUrl}/vm/{vmId}/ip/list' \
--header 'Authorization: Basic {token}'
```

```php
$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => '{baseUrl}/vm/{vmId}/ip/list',
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => '',
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => true,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => 'GET',
  CURLOPT_HTTPHEADER => array(
    'Authorization: Basic {token}',
  ),
));

$response = curl_exec($curl);
curl_close($curl);
echo $response;
```

> The above command returns JSON structured like this:

```json
{
  "success": true,
  "data": [
    {
      "ip": "185.208.172.18"
    }
  ]
}
```

This endpoint retrieves your vm ips list.

### HTTP Request

`GET {baseUrl}/vm/{vmId}/ip/list`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
{vmId} | null | Set vm id

<aside class="notice">
Remember change {vmID} with your vm id in url
</aside>














## Change vm title

```shell
curl --location --request PUT '{baseUrl}/vm/{vmId}changeTitle' \
--header 'Authorization: Basic {token}' \
--form 'title="test11"'

```

```php
$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => '{baseUrl}/vm/{vmId}changeTitle',
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => '',
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => true,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => 'PUT',
  CURLOPT_POSTFIELDS => array('title' => 'test11'),
  CURLOPT_HTTPHEADER => array(
    'Authorization: Basic {token}',
  ),
));

$response = curl_exec($curl);
curl_close($curl);
echo $response;
```

> The above command returns JSON structured like this:

```json
{
  "success": true,
  "data": "Title successfully changed"
}
```

This endpoint retrieves your vm ips list.

### HTTP Request

`PUT {baseUrl}/vm/{vmId}changeTitle`

### Query Parameters
Parameter | Default | Description
--------- | ------- | -----------
{vmId} | null | Set vm id
title | null | Set new title for vm

### Errors Sample
Success | Data
---------- | -------
false | Invalid parameters -- title is not valid.
false | null -- VM not exist.

<aside class="notice">
Remember change {vmID} with your vm id in url
</aside>













## Set daily budget

```shell
curl --location --request PUT '{baseUrl}/vm/{vmId}/dailybudget/set?daily_budget={amount}' \
--header 'Authorization: Basic {token}' \

```

```php
$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => '{baseUrl}/vm/{vmId}/dailybudget/set?daily_budget={amount}',
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => '',
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => true,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => 'PUT',
  CURLOPT_HTTPHEADER => array(
    'Authorization: Basic {token}',
  ),
));

$response = curl_exec($curl);
curl_close($curl);
echo $response;
```

> The above command returns JSON structured like this:

```json
{
  "success": true,
  "data": "Budget successfully set"
}
```

This endpoint set or change daily budget for specific vm.

### HTTP Request

`PUT {baseUrl}/vm/{vmId}/dailybudget/set?daily_budget={amount}`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
{vmId} | null | Set vm id
daily_budget | null | Set new daily budget


### Errors Sample

Success | Data
---------- | -------
false | Invalid parameters -- daily_budget is not valid.
false | null -- VM not exist.
false | wrong_server -- VM is not commercial.

<aside class="notice">
Remember change {vmID} with your vm id in url
Remember change {amount} with your specific amount for daily budget in url
</aside>











## Change VM spaces

```shell
curl --location --request POST '{baseUrl}/vm/{vmId}/changeSpecs' \
--header 'Authorization: Basic {token}' \

```

```php
$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => '{baseUrl}/vm/{vmId}/changeSpecs',
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => '',
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => true,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => 'POST',
  CURLOPT_HTTPHEADER => array(
    'Authorization: Basic {token}',
  ),
));

$response = curl_exec($curl);
curl_close($curl);
echo $response;
```

> The above command returns JSON structured like this:

```json
{
  "success": true,
  "data": "Server successfully restarted"
}
```

This endpoint change specific vm spaces.

### HTTP Request

`PUT {baseUrl}/vm/{vmId}/changeSpecs`

### Query Parameters

Parameter      | Required | Type     | Acceptable Values                                 | Description
---------      | -------  | -------- | -----------------------------------------------   | -----------
{ram}          | true     | integer  | min requirement ram for choosen os (1024-16384)   | Set ram amount
{cpu}          | true     | integer  | min requirement cpu for choosen os (1-16)         | Set cpu cores count


### Errors Sample

Success      | Data
----------   | -------
false        | invalid_parameters


<aside class="notice">
Remember change {vmID} with your vm id in url
</aside>















## Get OS list

```shell
curl --location --request GET '{baseUrl}/vm/os/list/all' \
--header 'Authorization: Basic {token}'
```

```php
$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => '{baseUrl}/vm/os/list/all',
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => '',
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => true,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => 'GET',
  CURLOPT_HTTPHEADER => array(
    'Authorization: Basic {token}',
  ),
));

$response = curl_exec($curl);
curl_close($curl);
echo $response;
```

> The above command returns JSON structured like this:

```json

{
  "success": true,
  "data": [
    {
      "title": "centos6-x64",
      "name": "centos6-x64",
      "min_ram": 512
    },
    {
      "title": "CentOS7-CI",
      "name": "centos7-cloudinit",
      "min_ram": 1024
    }
  ]
}
```

This endpoint return all os list.

### HTTP Request

`GET {baseUrl}/vm/os/list/all`


