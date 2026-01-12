---
title: ETSI GS QKD 004 push mode specification, QKD server v1.0.0
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

<h1 id="etsi-gs-qkd-004-push-mode-specification-qkd-server">ETSI GS QKD 004 push mode specification, QKD server v1.0.0</h1>

> Scroll down for code samples, example requests and responses. Select a language for code samples from the tabs above or the mobile navigation menu.

Server description of the QKD endpoint processing ETSI GS QKD 004 push mode requests

Base URLs:

* <a href="https://qkd_server/api/v1/kms/etsi004">https://qkd_server/api/v1/kms/etsi004</a>

Web: <a href="https://qkd-kms.ait.ac.at">Support</a> 

<h1 id="etsi-gs-qkd-004-push-mode-specification-qkd-server-etsi004">etsi004</h1>

## post_open_connect

<a id="opIdpost_open_connect"></a>

> Code samples

```shell
# You can also use wget
curl -X POST https://qkd_server/api/v1/kms/etsi004/open-connect \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
POST https://qkd_server/api/v1/kms/etsi004/open-connect HTTP/1.1
Host: qkd_server
Content-Type: application/json
Accept: application/json

```

```javascript
const inputBody = '{
  "source": "http://kms-1.net",
  "destination": "http://kms-2.net",
  "key_stream_id": "4eb81a5c-031f-4d1f-881d-309bee44fc20",
  "qos": {
    "key_chunk_size": 32,
    "max_bps": 128,
    "min_bps": 64,
    "jitter": 1,
    "priority": 3,
    "timeout": 50,
    "ttl": 600,
    "metadata_mimetype": "application/json"
  }
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'
};

fetch('https://qkd_server/api/v1/kms/etsi004/open-connect',
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

result = RestClient.post 'https://qkd_server/api/v1/kms/etsi004/open-connect',
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

r = requests.post('https://qkd_server/api/v1/kms/etsi004/open-connect', headers = headers)

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
    $response = $client->request('POST','https://qkd_server/api/v1/kms/etsi004/open-connect', array(
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
URL obj = new URL("https://qkd_server/api/v1/kms/etsi004/open-connect");
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
    req, err := http.NewRequest("POST", "https://qkd_server/api/v1/kms/etsi004/open-connect", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /open-connect`

*open key stream*

The `open-connect` message connects a KMS to the QKD Device. Conforming to the specification, the QKD device will assign the `key_stream_id` and can suggest alternative QoS due to its capabilities.

> Body parameter

```json
{
  "source": "http://kms-1.net",
  "destination": "http://kms-2.net",
  "key_stream_id": "4eb81a5c-031f-4d1f-881d-309bee44fc20",
  "qos": {
    "key_chunk_size": 32,
    "max_bps": 128,
    "min_bps": 64,
    "jitter": 1,
    "priority": 3,
    "timeout": 50,
    "ttl": 600,
    "metadata_mimetype": "application/json"
  }
}
```

<h3 id="post_open_connect-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|object|true|none|
|» source|body|string(uri)|true|the source URI of the request.|
|» destination|body|string(uri)|true|the destination URI of the request.|
|» key_stream_id|body|string(uuid)|false|key stream ID. If not specified it is up to the QKD device to define the UUID|
|» qos|body|[qos](#schemaqos)|true|All values according to ETSI GS QKD 004 specification. If KMS does not want to specify a parameter, it is up to the choice of the QKD. Either the value is given as "null" or not present.|
|»» key_chunk_size|body|integer(uint32)|false|length of key chunks in Byte.|
|»» max_bps|body|integer(uint32)|false|in bit per second|
|»» min_bps|body|integer(uint32)|false|in bit per second|
|»» jitter|body|integer(uint32)|false|in bit per second|
|»» priority|body|integer(uint32)|false|Meaning up to implementation.|
|»» timeout|body|integer(uint32)|false|Timeout in msec after which the call will be aborted, returning an error.|
|»» ttl|body|integer(uint32)|false|Time in seconds after which the keys for this key stream ID shall be erased from the kms key store.|
|»» metadata_mimetype|body|string(json)|false|MIME type of the metadata of the `get` request|

> Example responses

> 201 Response

```json
{
  "source": "http://kms-1.net",
  "destination": "http://kms-2.net",
  "key_stream_id": "4eb81a5c-031f-4d1f-881d-309bee44fc20",
  "qos": {
    "key_chunk_size": 32,
    "max_bps": 128,
    "min_bps": 64,
    "jitter": 1,
    "priority": 3,
    "timeout": 50,
    "ttl": 600,
    "metadata_mimetype": "application/json"
  },
  "status": 0
}
```

<h3 id="post_open_connect-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Key stream successfully created|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Client sent a malformed input|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|The server experienced an internal error|None|

<h3 id="post_open_connect-responseschema">Response Schema</h3>

Status Code **201**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» source|string(uri)|true|none|the source URI of the request.|
|» destination|string(uri)|true|none|the destination URI of the request.|
|» key_stream_id|string(uuid)|false|none|key stream ID. If not specified it is up to the QKD device to define the UUID|
|» qos|[qos](#schemaqos)|true|none|All values according to ETSI GS QKD 004 specification. If KMS does not want to specify a parameter, it is up to the choice of the QKD. Either the value is given as "null" or not present.|
|»» key_chunk_size|integer(uint32)|false|none|length of key chunks in Byte.|
|»» max_bps|integer(uint32)|false|none|in bit per second|
|»» min_bps|integer(uint32)|false|none|in bit per second|
|»» jitter|integer(uint32)|false|none|in bit per second|
|»» priority|integer(uint32)|false|none|Meaning up to implementation.|
|»» timeout|integer(uint32)|false|none|Timeout in msec after which the call will be aborted, returning an error.|
|»» ttl|integer(uint32)|false|none|Time in seconds after which the keys for this key stream ID shall be erased from the kms key store.|
|»» metadata_mimetype|string(json)|false|none|MIME type of the metadata of the `get` request|
|» status|[status](#schemastatus)(uint32)|false|none|none|

*oneOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|integer|false|none|Successful|

*xor*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|integer|false|none|Successful connection, but peer not connected|

*xor*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|integer|false|none|GET_KEY failed because insufficient key available|

*xor*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|integer|false|none|GET_KEY failed because peer application is not yet connected|

*xor*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|integer|false|none|No QKD connection available|

*xor*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|integer|false|none|OPEN_CONNECT failed because the KSID is already in use|

*xor*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|integer|false|none|TIMEOUT_ERROR The call failed because the specified TIMEOUT|

*xor*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|integer|false|none|OPEN failed because requested QoS settings could not be met, counter proposal included in return has occurred|

*xor*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|integer|false|none|GET_KEY failed because metadata field size insufficient. Returned Metadata_size value holds minimum needed size of metadata|

<aside class="success">
This operation does not require authentication
</aside>

## get_key

<a id="opIdget_key"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://qkd_server/api/v1/kms/etsi004/get-key \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
GET https://qkd_server/api/v1/kms/etsi004/get-key HTTP/1.1
Host: qkd_server
Content-Type: application/json
Accept: application/json

```

```javascript
const inputBody = '{
  "key_stream_id": "4eb81a5c-031f-4d1f-881d-309bee44fc20",
  "index": 0,
  "metadata": {
    "size": 0,
    "buffer": ""
  }
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'
};

fetch('https://qkd_server/api/v1/kms/etsi004/get-key',
{
  method: 'GET',
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

result = RestClient.get 'https://qkd_server/api/v1/kms/etsi004/get-key',
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

r = requests.get('https://qkd_server/api/v1/kms/etsi004/get-key', headers = headers)

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
    $response = $client->request('GET','https://qkd_server/api/v1/kms/etsi004/get-key', array(
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
URL obj = new URL("https://qkd_server/api/v1/kms/etsi004/get-key");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
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
    req, err := http.NewRequest("GET", "https://qkd_server/api/v1/kms/etsi004/get-key", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /get-key`

*start pushed key retrieval process*

The `get-key` message is the starting point after which the QKD device can start pushing keys.

> Body parameter

```json
{
  "key_stream_id": "4eb81a5c-031f-4d1f-881d-309bee44fc20",
  "index": 0,
  "metadata": {
    "size": 0,
    "buffer": ""
  }
}
```

<h3 id="get_key-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|object|true|none|
|» key_stream_id|body|string(uuid)|true|corresponding to the one given in `open_connect`|
|» index|body|integer(uint32)|false|increasing index of the key chunk in the key stream. Wrapping at UINT_MAX.|
|» metadata|body|[metadata](#schemametadata)|false|none|
|»» size|body|integer(uint32)|false|size of buffer in characters|
|»» buffer|body|string(json)|false|metadata in json format.|

> Example responses

> 205 Response

```json
{
  "status": 0,
  "metadata": {
    "size": 0,
    "buffer": ""
  }
}
```

<h3 id="get_key-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|205|[Reset Content](https://tools.ietf.org/html/rfc7231#section-6.3.6)|Successful registration|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Client sent a malformed input|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|The server experienced an internal error|None|

<h3 id="get_key-responseschema">Response Schema</h3>

Status Code **205**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» status|[status](#schemastatus)(uint32)|true|none|none|

*oneOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|integer|false|none|Successful|

*xor*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|integer|false|none|Successful connection, but peer not connected|

*xor*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|integer|false|none|GET_KEY failed because insufficient key available|

*xor*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|integer|false|none|GET_KEY failed because peer application is not yet connected|

*xor*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|integer|false|none|No QKD connection available|

*xor*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|integer|false|none|OPEN_CONNECT failed because the KSID is already in use|

*xor*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|integer|false|none|TIMEOUT_ERROR The call failed because the specified TIMEOUT|

*xor*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|integer|false|none|OPEN failed because requested QoS settings could not be met, counter proposal included in return has occurred|

*xor*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|integer|false|none|GET_KEY failed because metadata field size insufficient. Returned Metadata_size value holds minimum needed size of metadata|

*continued*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» metadata|[metadata](#schemametadata)|false|none|none|
|»» size|integer(uint32)|false|none|size of buffer in characters|
|»» buffer|string(json)|false|none|metadata in json format.|

<aside class="success">
This operation does not require authentication
</aside>

## put_close

<a id="opIdput_close"></a>

> Code samples

```shell
# You can also use wget
curl -X PUT https://qkd_server/api/v1/kms/etsi004/close \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
PUT https://qkd_server/api/v1/kms/etsi004/close HTTP/1.1
Host: qkd_server
Content-Type: application/json
Accept: application/json

```

```javascript
const inputBody = '{
  "key_stream_id": "4eb81a5c-031f-4d1f-881d-309bee44fc20"
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'
};

fetch('https://qkd_server/api/v1/kms/etsi004/close',
{
  method: 'PUT',
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

result = RestClient.put 'https://qkd_server/api/v1/kms/etsi004/close',
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

r = requests.put('https://qkd_server/api/v1/kms/etsi004/close', headers = headers)

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
    $response = $client->request('PUT','https://qkd_server/api/v1/kms/etsi004/close', array(
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
URL obj = new URL("https://qkd_server/api/v1/kms/etsi004/close");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("PUT");
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
    req, err := http.NewRequest("PUT", "https://qkd_server/api/v1/kms/etsi004/close", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`PUT /close`

*close the key stream*

The `close` message disconnects the KMS from the QKD device.

> Body parameter

```json
{
  "key_stream_id": "4eb81a5c-031f-4d1f-881d-309bee44fc20"
}
```

<h3 id="put_close-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|object|true|none|
|» key_stream_id|body|string(uuid)|true|corresponding to the one given in `open_connect`|

> Example responses

> 204 Response

```json
{
  "status": 0
}
```

<h3 id="put_close-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|Key stream successfully closed|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Client sent a malformed input|None|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|The server experienced an internal error|None|

<h3 id="put_close-responseschema">Response Schema</h3>

Status Code **204**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» status|[status](#schemastatus)(uint32)|true|none|none|

*oneOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|integer|false|none|Successful|

*xor*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|integer|false|none|Successful connection, but peer not connected|

*xor*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|integer|false|none|GET_KEY failed because insufficient key available|

*xor*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|integer|false|none|GET_KEY failed because peer application is not yet connected|

*xor*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|integer|false|none|No QKD connection available|

*xor*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|integer|false|none|OPEN_CONNECT failed because the KSID is already in use|

*xor*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|integer|false|none|TIMEOUT_ERROR The call failed because the specified TIMEOUT|

*xor*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|integer|false|none|OPEN failed because requested QoS settings could not be met, counter proposal included in return has occurred|

*xor*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»» *anonymous*|integer|false|none|GET_KEY failed because metadata field size insufficient. Returned Metadata_size value holds minimum needed size of metadata|

<aside class="success">
This operation does not require authentication
</aside>

# Schemas

<h2 id="tocS_qos">qos</h2>
<!-- backwards compatibility -->
<a id="schemaqos"></a>
<a id="schema_qos"></a>
<a id="tocSqos"></a>
<a id="tocsqos"></a>

```json
{
  "key_chunk_size": 32,
  "max_bps": 128,
  "min_bps": 64,
  "jitter": 1,
  "priority": 3,
  "timeout": 50,
  "ttl": 600,
  "metadata_mimetype": "application/json"
}

```

All values according to ETSI GS QKD 004 specification. If KMS does not want to specify a parameter, it is up to the choice of the QKD. Either the value is given as "null" or not present.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|key_chunk_size|integer(uint32)|false|none|length of key chunks in Byte.|
|max_bps|integer(uint32)|false|none|in bit per second|
|min_bps|integer(uint32)|false|none|in bit per second|
|jitter|integer(uint32)|false|none|in bit per second|
|priority|integer(uint32)|false|none|Meaning up to implementation.|
|timeout|integer(uint32)|false|none|Timeout in msec after which the call will be aborted, returning an error.|
|ttl|integer(uint32)|false|none|Time in seconds after which the keys for this key stream ID shall be erased from the kms key store.|
|metadata_mimetype|string(json)|false|none|MIME type of the metadata of the `get` request|

<h2 id="tocS_metadata">metadata</h2>
<!-- backwards compatibility -->
<a id="schemametadata"></a>
<a id="schema_metadata"></a>
<a id="tocSmetadata"></a>
<a id="tocsmetadata"></a>

```json
{
  "size": 0,
  "buffer": ""
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|size|integer(uint32)|false|none|size of buffer in characters|
|buffer|string(json)|false|none|metadata in json format.|

<h2 id="tocS_status">status</h2>
<!-- backwards compatibility -->
<a id="schemastatus"></a>
<a id="schema_status"></a>
<a id="tocSstatus"></a>
<a id="tocsstatus"></a>

```json
0

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|integer(uint32)|false|none|none|

oneOf

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|integer|false|none|Successful|

xor

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|integer|false|none|Successful connection, but peer not connected|

xor

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|integer|false|none|GET_KEY failed because insufficient key available|

xor

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|integer|false|none|GET_KEY failed because peer application is not yet connected|

xor

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|integer|false|none|No QKD connection available|

xor

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|integer|false|none|OPEN_CONNECT failed because the KSID is already in use|

xor

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|integer|false|none|TIMEOUT_ERROR The call failed because the specified TIMEOUT|

xor

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|integer|false|none|OPEN failed because requested QoS settings could not be met, counter proposal included in return has occurred|

xor

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|integer|false|none|GET_KEY failed because metadata field size insufficient. Returned Metadata_size value holds minimum needed size of metadata|

