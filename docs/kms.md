---
title: ETSI GS QKD 004 push mode specification, KMS server v1.0.0
language_tabs:
  - shell: Shell
  - http: HTTP
  - javascript: JavaScript
  - ruby: Ruby
  - python: Python
  - php: PHP
  - java: Java
  - go: Go
toc_footers: []
includes: []
search: true
highlight_theme: darkula
headingLevel: 2

---

<!-- Generator: Widdershins v4.0.1 -->

<h1 id="etsi-gs-qkd-004-push-mode-specification-kms-server">ETSI GS QKD 004 push mode specification, KMS server v1.0.0</h1>

> Scroll down for code samples, example requests and responses. Select a language for code samples from the tabs above or the mobile navigation menu.

Server description of the KMS endpoint processing ETSI GS QKD 004 push mode requests

Base URLs:

* <a href="https://qkd_server/api/v1/qkd/etsi004">https://qkd_server/api/v1/qkd/etsi004</a>

Web: <a href="https://qkd-kms.ait.ac.at">Support</a> 

<h1 id="etsi-gs-qkd-004-push-mode-specification-kms-server-etsi004">etsi004</h1>

## post_key_material

<a id="opIdpost_key_material"></a>

> Code samples

```shell
# You can also use wget
curl -X POST https://qkd_server/api/v1/qkd/etsi004/key-material \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
POST https://qkd_server/api/v1/qkd/etsi004/key-material HTTP/1.1
Host: qkd_server
Content-Type: application/json
Accept: application/json

```

```javascript
const inputBody = '{
  "status": null,
  "index": 0,
  "key_buffer": "string",
  "metadata": {
    "size": 57,
    "buffer": {
      "key_stream_id": "4eb81a5c-031f-4d1f-881d-309bee44fc20"
    }
  }
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'
};

fetch('https://qkd_server/api/v1/qkd/etsi004/key-material',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json'
}

result = RestClient.post 'https://qkd_server/api/v1/qkd/etsi004/key-material',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}

r = requests.post('https://qkd_server/api/v1/qkd/etsi004/key-material', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Content-Type' => 'application/json',
    'Accept' => 'application/json',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('POST','https://qkd_server/api/v1/qkd/etsi004/key-material', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://qkd_server/api/v1/qkd/etsi004/key-material");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json"},
        "Accept": []string{"application/json"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://qkd_server/api/v1/qkd/etsi004/key-material", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /key-material`

*endpoint to push key material to.*

According to the sequence, after a successful `get_key`, the QKD can push the corresponding key material to this endpoint, whenever it created a new key.

> Body parameter

```json
{
  "status": null,
  "index": 0,
  "key_buffer": "string",
  "metadata": {
    "size": 57,
    "buffer": {
      "key_stream_id": "4eb81a5c-031f-4d1f-881d-309bee44fc20"
    }
  }
}
```

<h3 id="post_key_material-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|object|true|none|
|» status|body|any|true|none|
|» index|body|integer(uint32)|true|increasing index of the key chunk in the key stream. Wrapping at UINT_MAX.|
|» key_buffer|body|string(base64)|true|none|
|» metadata|body|object|false|none|
|»» size|body|integer(uint32)|false|size of buffer in characters|
|»» buffer|body|object(json)|false|metadata in json format.|
|»»» key_stream_id|body|string(uuid)|true|key stream ID to which the value belongs (required for KMS in case of multiple open key streams)|

> Example responses

> 201 Response

```json
{
  "status": null,
  "metadata": null
}
```

<h3 id="post_key_material-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Key successfully received|Inline|

<h3 id="post_key_material-responseschema">Response Schema</h3>

Status Code **201**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» status|any|true|none|none|
|» metadata|any|false|none|none|

<aside class="success">
This operation does not require authentication
</aside>

