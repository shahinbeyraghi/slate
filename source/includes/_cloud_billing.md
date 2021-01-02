




## Get VM Pricing info

```shell
curl --location --request GET '{baseUrl}/cloud-billing/get-price-info/{location}' \
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