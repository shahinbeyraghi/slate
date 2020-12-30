---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - php

toc_footers:
  - <a href='https://cl.parspack.com/clpanel/client-area/dashboard'>Sign Up for a JWT token</a>

includes:
  - errors

search: true

code_clipboard: true
---

# Introduction

Welcome to the Parspack API! You can use our API to access Management Your Cloud , which can get information on projects, VMs, and edit them in our database.

We have language bindings in PHP! You can view code examples in the dark area to the right.

# Authentication

> To authorize, use this code:


```shell
curl --location --request GET '{url}' \
--header 'Authorization: Bearer {token}'
```

```php
$curl = curl_init();

curl_setopt_array($curl, array(
    CURLOPT_URL => '{url}',
    CURLOPT_HTTPHEADER => array(
        'Authorization: Bearer {token}'
        )
    )
);
```

> Make sure to replace `{token}` with your JWT token and {url} with end point address.

Parspack uses JWT token authentication to allow access to the API. You can get a new JWT token at our [developer portal](https://cl.parspack.com/clients/cloud3/servers).

We expects for the JWT token to be included in all API requests to the server in a header that looks like the following:

`Authorization: Bearer {token}`

<aside class="notice">
You must replace <code>{token}</code> with your personal JWT token.
</aside>

# APIs

## Get All Your VMs


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
{vmId} | true | Set vm id

<aside class="notice">
Remember set {vmID} in url not in GET parameters
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
{vmId} | true | Set vm id

<aside class="notice">
Remember set {vmID} in url not in GET parameters
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
  "data": [
    {
      "ip": "185.208.172.18"
    }
  ]
}
```

This endpoint retrieves your vm ips list.

### HTTP Request

`PUT {baseUrl}/vm/{vmId}changeTitle`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
{vmId} | true | Set vm id
title | null | Set new title for vm

<aside class="notice">
Remember set {vmID} in url not in GET parameters
</aside>

