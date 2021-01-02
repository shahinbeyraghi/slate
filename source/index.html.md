---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - javascript
  - python
  - shell
  - php

toc_footers:
  - <a href='https://cl.parspack.com/clpanel/client-area/dashboard'>Sign Up for a JWT token</a>

includes:
  - vm
  - errors

search: true

code_clipboard: true
---

# Introduction

Welcome to the Parspack API! You can use our API to access Management Your Cloud , which can get information on projects, VMs, and edit them in our database.

We have language bindings in PHP! You can view code examples in the dark area to the right.

# Authentication

> To authorize, use this code:


```javascript
var options = {
    'headers': {
        'Accept': 'application/json',
        'Authorization': 'Basic {token}'
    }
}
```

```python
headers = {
  'Accept': 'application/json',
  'Authorization': 'Basic {token}',
}

response = requests.request("Method", url, headers=headers, data=payload, files=files)
```


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



