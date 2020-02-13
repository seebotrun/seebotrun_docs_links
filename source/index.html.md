---
title: SeeBotRun - Shortener API

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - ruby
  - php
  - javascript

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---





# Introduction

The SeeBotRun Shortener API is a REST API designed to provide a clear, concise pathway into a client's account.





# Authentication

> To authorize, use this code:

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
```

```php
import kittn

api = kittn.authorize('meowmeowmeow')
```

```shell
# With shell, you can just pass the correct header with each request
curl "https://portal.seebot.run/api/auth/login"
  -H "Authorization: mytemporaryauthtoken"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
```

> Make sure to replace `mytemporaryauthtoken` with the provided API token.

To obtain access, you must first have an active account, as well as a username/password provided.  Authentication is performed against the username/password for a given user account, and returns an access token to be used as a bearer token on all API requests.

API tokens have a rolling expiration, and if not used, will expire after two hours.

When used in requests, you'll want to set the Authorization header with each request.

`Authorization: mytemporaryauthtoken`

<aside class="notice">
You must replace <code>mytemporaryauthtoken</code> with the provided API token.
</aside>





# Domains

## Get All Domains

```ruby
require 'uri'
require 'net/http'

url = URI("http://links.sbr.test/api/domains")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Get.new(url)
request["accept"] = 'application/json'
request["content-type"] = 'application/json'
request["authorization"] = 'Bearer eyJpdiI6IjVnWUhxUlwvMFZwNTJOR0IwZjhZR1Z3PT0iLCJ2YWx1ZSI6InVuOHVRSVFZdk5aSCtIZVVRS3U2Q085OUFycXFWMTRZSWpBNEF4YXVMOTNNbEYxVitKQkVGYnBPMjl3Sm5jenc4SDIrbVB3cHp3NE45d3JXSFNFTzNcL24rdE1nMFRIZFVCY2liTVFZTjN6RT0iLCJtYWMiOiI5M2EzNjAyZmZlYzllYTZhYjhlNTIyZDdiNGJlYjdkZTQ1NWYzNzhkNzYxMjdlZTk2YmRjOTY2MTRkYTQ4ODljIn0='

response = http.request(request)
puts response.read_body
```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$request->setRequestUrl('http://links.sbr.test/api/domains');
$request->setRequestMethod('GET');
$request->setHeaders(array(
  'accept' => 'application/json',
  'content-type' => 'application/json',
  'authorization' => 'Bearer eyJpdiI6IjVnWUhxUlwvMFZwNTJOR0IwZjhZR1Z3PT0iLCJ2YWx1ZSI6InVuOHVRSVFZdk5aSCtIZVVRS3U2Q085OUFycXFWMTRZSWpBNEF4YXVMOTNNbEYxVitKQkVGYnBPMjl3Sm5jenc4SDIrbVB3cHp3NE45d3JXSFNFTzNcL24rdE1nMFRIZFVCY2liTVFZTjN6RT0iLCJtYWMiOiI5M2EzNjAyZmZlYzllYTZhYjhlNTIyZDdiNGJlYjdkZTQ1NWYzNzhkNzYxMjdlZTk2YmRjOTY2MTRkYTQ4ODljIn0='
));

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```shell
curl --request GET \
  --url http://links.sbr.test/api/domains \
  --header 'accept: application/json' \
  --header 'authorization: Bearer eyJpdiI6IjVnWUhxUlwvMFZwNTJOR0IwZjhZR1Z3PT0iLCJ2YWx1ZSI6InVuOHVRSVFZdk5aSCtIZVVRS3U2Q085OUFycXFWMTRZSWpBNEF4YXVMOTNNbEYxVitKQkVGYnBPMjl3Sm5jenc4SDIrbVB3cHp3NE45d3JXSFNFTzNcL24rdE1nMFRIZFVCY2liTVFZTjN6RT0iLCJtYWMiOiI5M2EzNjAyZmZlYzllYTZhYjhlNTIyZDdiNGJlYjdkZTQ1NWYzNzhkNzYxMjdlZTk2YmRjOTY2MTRkYTQ4ODljIn0=' \
  --header 'content-type: application/json'
```

```javascript
var request = require("request");

var options = {
  method: 'GET',
  url: 'http://links.sbr.test/api/domains',
  headers: {
    accept: 'application/json',
    'content-type': 'application/json',
    authorization: 'Bearer eyJpdiI6IjVnWUhxUlwvMFZwNTJOR0IwZjhZR1Z3PT0iLCJ2YWx1ZSI6InVuOHVRSVFZdk5aSCtIZVVRS3U2Q085OUFycXFWMTRZSWpBNEF4YXVMOTNNbEYxVitKQkVGYnBPMjl3Sm5jenc4SDIrbVB3cHp3NE45d3JXSFNFTzNcL24rdE1nMFRIZFVCY2liTVFZTjN6RT0iLCJtYWMiOiI5M2EzNjAyZmZlYzllYTZhYjhlNTIyZDdiNGJlYjdkZTQ1NWYzNzhkNzYxMjdlZTk2YmRjOTY2MTRkYTQ4ODljIn0='
  }
};

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": 1,
      "name": "sbr.im",
      "url": "sbr.im",
      "status": "active",
      "scope": "system",
      "default_root_url": null,
      "default_catchall_url": null
    },
    {
      "id": 2,
      "name": "utt.im",
      "url": "utt.im",
      "status": "active",
      "scope": "client",
      "default_root_url": null,
      "default_catchall_url": null
    }
  ],
  "meta": {
    "total": 2,
    "count": 2,
    "page": 1,
    "pages": 1,
    "per_page": 25,
    "order": "id",
    "sort": "DESC"
  }
}
```

This endpoint retrieves all domains available to the client.

### HTTP Request

`GET https://links.seebot.run/api/domains`

### Query Parameters

Parameter                    | Required                | Default                    | Description
---------------------------- | ----------------------- | -------------------------- | ---------------------------------------------------------
page                         | false                   | 1                          | The current page of results to retrieve.
per_page                     | false                   | 25                         | The number of results to pull back. Allowed values: 25, 50, 100, -1 (for all)
sort                         | false                   | desc                       | The order for record sorting.
order                        | false                   | id                         | The field for sorting records. Allowed values: id, name, url, status









## Get a Domain By ID

```ruby
require 'uri'
require 'net/http'

url = URI("http://links.sbr.test/api/domains/4")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Get.new(url)
request["accept"] = 'application/json'
request["content-type"] = 'application/json'
request["authorization"] = 'Bearer eyJpdiI6IjVnWUhxUlwvMFZwNTJOR0IwZjhZR1Z3PT0iLCJ2YWx1ZSI6InVuOHVRSVFZdk5aSCtIZVVRS3U2Q085OUFycXFWMTRZSWpBNEF4YXVMOTNNbEYxVitKQkVGYnBPMjl3Sm5jenc4SDIrbVB3cHp3NE45d3JXSFNFTzNcL24rdE1nMFRIZFVCY2liTVFZTjN6RT0iLCJtYWMiOiI5M2EzNjAyZmZlYzllYTZhYjhlNTIyZDdiNGJlYjdkZTQ1NWYzNzhkNzYxMjdlZTk2YmRjOTY2MTRkYTQ4ODljIn0='

response = http.request(request)
puts response.read_body
```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$request->setRequestUrl('http://links.sbr.test/api/domains/4');
$request->setRequestMethod('GET');
$request->setHeaders(array(
  'accept' => 'application/json',
  'content-type' => 'application/json',
  'authorization' => 'Bearer eyJpdiI6IjVnWUhxUlwvMFZwNTJOR0IwZjhZR1Z3PT0iLCJ2YWx1ZSI6InVuOHVRSVFZdk5aSCtIZVVRS3U2Q085OUFycXFWMTRZSWpBNEF4YXVMOTNNbEYxVitKQkVGYnBPMjl3Sm5jenc4SDIrbVB3cHp3NE45d3JXSFNFTzNcL24rdE1nMFRIZFVCY2liTVFZTjN6RT0iLCJtYWMiOiI5M2EzNjAyZmZlYzllYTZhYjhlNTIyZDdiNGJlYjdkZTQ1NWYzNzhkNzYxMjdlZTk2YmRjOTY2MTRkYTQ4ODljIn0='
));

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```shell
curl --request GET \
  --url http://links.sbr.test/api/domains/4 \
  --header 'accept: application/json' \
  --header 'authorization: Bearer eyJpdiI6IjVnWUhxUlwvMFZwNTJOR0IwZjhZR1Z3PT0iLCJ2YWx1ZSI6InVuOHVRSVFZdk5aSCtIZVVRS3U2Q085OUFycXFWMTRZSWpBNEF4YXVMOTNNbEYxVitKQkVGYnBPMjl3Sm5jenc4SDIrbVB3cHp3NE45d3JXSFNFTzNcL24rdE1nMFRIZFVCY2liTVFZTjN6RT0iLCJtYWMiOiI5M2EzNjAyZmZlYzllYTZhYjhlNTIyZDdiNGJlYjdkZTQ1NWYzNzhkNzYxMjdlZTk2YmRjOTY2MTRkYTQ4ODljIn0=' \
  --header 'content-type: application/json'
```

```javascript
var request = require("request");

var options = {
  method: 'GET',
  url: 'http://links.sbr.test/api/domains/4',
  headers: {
    accept: 'application/json',
    'content-type': 'application/json',
    authorization: 'Bearer eyJpdiI6IjVnWUhxUlwvMFZwNTJOR0IwZjhZR1Z3PT0iLCJ2YWx1ZSI6InVuOHVRSVFZdk5aSCtIZVVRS3U2Q085OUFycXFWMTRZSWpBNEF4YXVMOTNNbEYxVitKQkVGYnBPMjl3Sm5jenc4SDIrbVB3cHp3NE45d3JXSFNFTzNcL24rdE1nMFRIZFVCY2liTVFZTjN6RT0iLCJtYWMiOiI5M2EzNjAyZmZlYzllYTZhYjhlNTIyZDdiNGJlYjdkZTQ1NWYzNzhkNzYxMjdlZTk2YmRjOTY2MTRkYTQ4ODljIn0='
  }
};

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": 4,
    "name": "seebot.test",
    "url": "seebot.test",
    "status": "active",
    "scope": "client",
    "default_root_url": null,
    "default_catchall_url": null
  }
}
```

This endpoint retrieves a domain owned by a client.

### HTTP Request

`GET http://links.sbr.test/api/domains/<ID>`

### URL Parameters

Parameter                    | Required                | Default                    | Description
---------------------------- | ----------------------- | -------------------------- | ---------------------------------------------------------
ID                           | true                    | n/a                        | The ID used to identify the domain.


## Create a New Domain

```ruby
require 'uri'
require 'net/http'

url = URI("http://links.sbr.test/api/domains")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Post.new(url)
request["accept"] = 'application/json'
request["content-type"] = 'application/json'
request["authorization"] = 'Bearer eyJpdiI6IjVnWUhxUlwvMFZwNTJOR0IwZjhZR1Z3PT0iLCJ2YWx1ZSI6InVuOHVRSVFZdk5aSCtIZVVRS3U2Q085OUFycXFWMTRZSWpBNEF4YXVMOTNNbEYxVitKQkVGYnBPMjl3Sm5jenc4SDIrbVB3cHp3NE45d3JXSFNFTzNcL24rdE1nMFRIZFVCY2liTVFZTjN6RT0iLCJtYWMiOiI5M2EzNjAyZmZlYzllYTZhYjhlNTIyZDdiNGJlYjdkZTQ1NWYzNzhkNzYxMjdlZTk2YmRjOTY2MTRkYTQ4ODljIn0='
request.body = "{\n\t\"name\": \"seebot.test\",\n\t\"url\": \"seebot.test\",\n\t\"status\": \"active\",\n\t\"default_root_url\": \"\",\n\t\"default_catchall_url\": \"\"\n}"

response = http.request(request)
puts response.read_body
```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$body = new http\Message\Body;
$body->append('{
	"name": "seebot.test",
	"url": "seebot.test",
	"status": "active",
	"default_root_url": "",
	"default_catchall_url": ""
}');

$request->setRequestUrl('http://links.sbr.test/api/domains');
$request->setRequestMethod('POST');
$request->setBody($body);

$request->setHeaders(array(
  'accept' => 'application/json',
  'content-type' => 'application/json',
  'authorization' => 'Bearer eyJpdiI6IjVnWUhxUlwvMFZwNTJOR0IwZjhZR1Z3PT0iLCJ2YWx1ZSI6InVuOHVRSVFZdk5aSCtIZVVRS3U2Q085OUFycXFWMTRZSWpBNEF4YXVMOTNNbEYxVitKQkVGYnBPMjl3Sm5jenc4SDIrbVB3cHp3NE45d3JXSFNFTzNcL24rdE1nMFRIZFVCY2liTVFZTjN6RT0iLCJtYWMiOiI5M2EzNjAyZmZlYzllYTZhYjhlNTIyZDdiNGJlYjdkZTQ1NWYzNzhkNzYxMjdlZTk2YmRjOTY2MTRkYTQ4ODljIn0='
));

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```shell
curl --request POST \
  --url http://links.sbr.test/api/domains \
  --header 'accept: application/json' \
  --header 'authorization: Bearer eyJpdiI6IjVnWUhxUlwvMFZwNTJOR0IwZjhZR1Z3PT0iLCJ2YWx1ZSI6InVuOHVRSVFZdk5aSCtIZVVRS3U2Q085OUFycXFWMTRZSWpBNEF4YXVMOTNNbEYxVitKQkVGYnBPMjl3Sm5jenc4SDIrbVB3cHp3NE45d3JXSFNFTzNcL24rdE1nMFRIZFVCY2liTVFZTjN6RT0iLCJtYWMiOiI5M2EzNjAyZmZlYzllYTZhYjhlNTIyZDdiNGJlYjdkZTQ1NWYzNzhkNzYxMjdlZTk2YmRjOTY2MTRkYTQ4ODljIn0=' \
  --header 'content-type: application/json' \
  --data '{
	"name": "seebot.test",
	"url": "seebot.test",
	"status": "active",
	"default_root_url": "",
	"default_catchall_url": ""
}'
```

```javascript
var request = require("request");

var options = {
  method: 'POST',
  url: 'http://links.sbr.test/api/domains',
  headers: {
    accept: 'application/json',
    'content-type': 'application/json',
    authorization: 'Bearer eyJpdiI6IjVnWUhxUlwvMFZwNTJOR0IwZjhZR1Z3PT0iLCJ2YWx1ZSI6InVuOHVRSVFZdk5aSCtIZVVRS3U2Q085OUFycXFWMTRZSWpBNEF4YXVMOTNNbEYxVitKQkVGYnBPMjl3Sm5jenc4SDIrbVB3cHp3NE45d3JXSFNFTzNcL24rdE1nMFRIZFVCY2liTVFZTjN6RT0iLCJtYWMiOiI5M2EzNjAyZmZlYzllYTZhYjhlNTIyZDdiNGJlYjdkZTQ1NWYzNzhkNzYxMjdlZTk2YmRjOTY2MTRkYTQ4ODljIn0='
  },
  body: {
    name: 'seebot.test',
    url: 'seebot.test',
    status: 'active',
    default_root_url: '',
    default_catchall_url: ''
  },
  json: true
};

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "name": "seebot.test",
    "url": "seebot.test",
    "status": "active",
    "default_root_url": null,
    "default_catchall_url": null,
    "scope": "client",
    "id": 4
  }
}
```

This endpoint creates a new domain and associates it with the client.

### HTTP Request

`POST http://links.sbr.test/api/domains`

### Body Parameters

Parameter                    | Required                | Default                    | Description
---------------------------- | ----------------------- | -------------------------- | ---------------------------------------------------------
name                         | true                    | n/a                        | The name used to easily identify the domain.
url                          | true                    | n/a                        | The URL (without schema) used by the domain.
status                       | true                    | active                     | The status of the domain. Allowed values: active, inactive.
default_root_url             | false                   | null                       | The default URL (schema required) to be used as a redirect when the root URL is visited.
default_catchall_url         | false                   | null                       | The default URL (schema required) to be used as a catchall redirect when an unknown URL is visited.


## Update an Existing Domain

```ruby
require 'uri'
require 'net/http'

url = URI("http://links.sbr.test/api/domains/4")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Put.new(url)
request["accept"] = 'application/json'
request["content-type"] = 'application/json'
request["authorization"] = 'Bearer eyJpdiI6IjVnWUhxUlwvMFZwNTJOR0IwZjhZR1Z3PT0iLCJ2YWx1ZSI6InVuOHVRSVFZdk5aSCtIZVVRS3U2Q085OUFycXFWMTRZSWpBNEF4YXVMOTNNbEYxVitKQkVGYnBPMjl3Sm5jenc4SDIrbVB3cHp3NE45d3JXSFNFTzNcL24rdE1nMFRIZFVCY2liTVFZTjN6RT0iLCJtYWMiOiI5M2EzNjAyZmZlYzllYTZhYjhlNTIyZDdiNGJlYjdkZTQ1NWYzNzhkNzYxMjdlZTk2YmRjOTY2MTRkYTQ4ODljIn0='
request.body = "{\n\t\"name\": \"seebot.test\",\n\t\"url\": \"seebot.test\",\n\t\"status\": \"active\",\n\t\"default_root_url\": \"\",\n\t\"default_catchall_url\": \"\"\n}"

response = http.request(request)
puts response.read_body
```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$body = new http\Message\Body;
$body->append('{
	"name": "seebot.test",
	"url": "seebot.test",
	"status": "active",
	"default_root_url": "",
	"default_catchall_url": ""
}');

$request->setRequestUrl('http://links.sbr.test/api/domains/4');
$request->setRequestMethod('PUT');
$request->setBody($body);

$request->setHeaders(array(
  'accept' => 'application/json',
  'content-type' => 'application/json',
  'authorization' => 'Bearer eyJpdiI6IjVnWUhxUlwvMFZwNTJOR0IwZjhZR1Z3PT0iLCJ2YWx1ZSI6InVuOHVRSVFZdk5aSCtIZVVRS3U2Q085OUFycXFWMTRZSWpBNEF4YXVMOTNNbEYxVitKQkVGYnBPMjl3Sm5jenc4SDIrbVB3cHp3NE45d3JXSFNFTzNcL24rdE1nMFRIZFVCY2liTVFZTjN6RT0iLCJtYWMiOiI5M2EzNjAyZmZlYzllYTZhYjhlNTIyZDdiNGJlYjdkZTQ1NWYzNzhkNzYxMjdlZTk2YmRjOTY2MTRkYTQ4ODljIn0='
));

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```shell
curl --request PUT \
  --url http://links.sbr.test/api/domains/4 \
  --header 'accept: application/json' \
  --header 'authorization: Bearer eyJpdiI6IjVnWUhxUlwvMFZwNTJOR0IwZjhZR1Z3PT0iLCJ2YWx1ZSI6InVuOHVRSVFZdk5aSCtIZVVRS3U2Q085OUFycXFWMTRZSWpBNEF4YXVMOTNNbEYxVitKQkVGYnBPMjl3Sm5jenc4SDIrbVB3cHp3NE45d3JXSFNFTzNcL24rdE1nMFRIZFVCY2liTVFZTjN6RT0iLCJtYWMiOiI5M2EzNjAyZmZlYzllYTZhYjhlNTIyZDdiNGJlYjdkZTQ1NWYzNzhkNzYxMjdlZTk2YmRjOTY2MTRkYTQ4ODljIn0=' \
  --header 'content-type: application/json' \
  --data '{
	"name": "seebot.test",
	"url": "seebot.test",
	"status": "active",
	"default_root_url": "",
	"default_catchall_url": ""
}'
```

```javascript
var request = require("request");

var options = {
  method: 'PUT',
  url: 'http://links.sbr.test/api/domains/4',
  headers: {
    accept: 'application/json',
    'content-type': 'application/json',
    authorization: 'Bearer eyJpdiI6IjVnWUhxUlwvMFZwNTJOR0IwZjhZR1Z3PT0iLCJ2YWx1ZSI6InVuOHVRSVFZdk5aSCtIZVVRS3U2Q085OUFycXFWMTRZSWpBNEF4YXVMOTNNbEYxVitKQkVGYnBPMjl3Sm5jenc4SDIrbVB3cHp3NE45d3JXSFNFTzNcL24rdE1nMFRIZFVCY2liTVFZTjN6RT0iLCJtYWMiOiI5M2EzNjAyZmZlYzllYTZhYjhlNTIyZDdiNGJlYjdkZTQ1NWYzNzhkNzYxMjdlZTk2YmRjOTY2MTRkYTQ4ODljIn0='
  },
  body: {
    name: 'seebot.test',
    url: 'seebot.test',
    status: 'active',
    default_root_url: '',
    default_catchall_url: ''
  },
  json: true
};

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": 4,
    "name": "seebot.test",
    "url": "seebot.test",
    "status": "active",
    "scope": "client",
    "default_root_url": null,
    "default_catchall_url": null
  }
}
```

This endpoint updates an existing domain owned by a client.

### HTTP Request

`PUT http://links.sbr.test/api/domains/<ID>`

### URL Parameters

Parameter                    | Required                | Default                    | Description
---------------------------- | ----------------------- | -------------------------- | ---------------------------------------------------------
ID                           | true                    | n/a                        | The ID used to identify the domain.

### Body Parameters

Parameter                    | Required                | Default                    | Description
---------------------------- | ----------------------- | -------------------------- | ---------------------------------------------------------
name                         | true                    | n/a                        | The name used to easily identify the domain.
url                          | true                    | n/a                        | The URL (without schema) used by the domain.
status                       | true                    | active                     | The status of the domain. Allowed values: active, inactive.
default_root_url             | false                   | null                       | The default URL (schema required) to be used as a redirect when the root URL is visited.
default_catchall_url         | false                   | null                       | The default URL (schema required) to be used as a catchall redirect when an unknown URL is visited.


## Delete a Specific Domain

```ruby
require 'uri'
require 'net/http'

url = URI("http://links.sbr.test/api/domains/4")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Delete.new(url)
request["accept"] = 'application/json'
request["authorization"] = 'Bearer eyJpdiI6IjVnWUhxUlwvMFZwNTJOR0IwZjhZR1Z3PT0iLCJ2YWx1ZSI6InVuOHVRSVFZdk5aSCtIZVVRS3U2Q085OUFycXFWMTRZSWpBNEF4YXVMOTNNbEYxVitKQkVGYnBPMjl3Sm5jenc4SDIrbVB3cHp3NE45d3JXSFNFTzNcL24rdE1nMFRIZFVCY2liTVFZTjN6RT0iLCJtYWMiOiI5M2EzNjAyZmZlYzllYTZhYjhlNTIyZDdiNGJlYjdkZTQ1NWYzNzhkNzYxMjdlZTk2YmRjOTY2MTRkYTQ4ODljIn0='

response = http.request(request)
puts response.read_body
```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$request->setRequestUrl('http://links.sbr.test/api/domains/4');
$request->setRequestMethod('DELETE');
$request->setHeaders(array(
  'accept' => 'application/json',
  'authorization' => 'Bearer eyJpdiI6IjVnWUhxUlwvMFZwNTJOR0IwZjhZR1Z3PT0iLCJ2YWx1ZSI6InVuOHVRSVFZdk5aSCtIZVVRS3U2Q085OUFycXFWMTRZSWpBNEF4YXVMOTNNbEYxVitKQkVGYnBPMjl3Sm5jenc4SDIrbVB3cHp3NE45d3JXSFNFTzNcL24rdE1nMFRIZFVCY2liTVFZTjN6RT0iLCJtYWMiOiI5M2EzNjAyZmZlYzllYTZhYjhlNTIyZDdiNGJlYjdkZTQ1NWYzNzhkNzYxMjdlZTk2YmRjOTY2MTRkYTQ4ODljIn0='
));

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```shell
curl --request DELETE \
  --url http://links.sbr.test/api/domains/4 \
  --header 'accept: application/json' \
  --header 'authorization: Bearer eyJpdiI6IjVnWUhxUlwvMFZwNTJOR0IwZjhZR1Z3PT0iLCJ2YWx1ZSI6InVuOHVRSVFZdk5aSCtIZVVRS3U2Q085OUFycXFWMTRZSWpBNEF4YXVMOTNNbEYxVitKQkVGYnBPMjl3Sm5jenc4SDIrbVB3cHp3NE45d3JXSFNFTzNcL24rdE1nMFRIZFVCY2liTVFZTjN6RT0iLCJtYWMiOiI5M2EzNjAyZmZlYzllYTZhYjhlNTIyZDdiNGJlYjdkZTQ1NWYzNzhkNzYxMjdlZTk2YmRjOTY2MTRkYTQ4ODljIn0='
```

```javascript
var request = require("request");

var options = {
  method: 'DELETE',
  url: 'http://links.sbr.test/api/domains/4',
  headers: {
    accept: 'application/json',
    authorization: 'Bearer eyJpdiI6IjVnWUhxUlwvMFZwNTJOR0IwZjhZR1Z3PT0iLCJ2YWx1ZSI6InVuOHVRSVFZdk5aSCtIZVVRS3U2Q085OUFycXFWMTRZSWpBNEF4YXVMOTNNbEYxVitKQkVGYnBPMjl3Sm5jenc4SDIrbVB3cHp3NE45d3JXSFNFTzNcL24rdE1nMFRIZFVCY2liTVFZTjN6RT0iLCJtYWMiOiI5M2EzNjAyZmZlYzllYTZhYjhlNTIyZDdiNGJlYjdkZTQ1NWYzNzhkNzYxMjdlZTk2YmRjOTY2MTRkYTQ4ODljIn0='
  }
};

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

> The above command returns no content with a 204 response on success.

This endpoint deletes a domain (and all associated links).

### HTTP Request

`DELETE http://links.sbr.test/api/domains/<ID>`

### URL Parameters

Parameter                    | Required                | Default                    | Description
---------------------------- | ----------------------- | -------------------------- | ---------------------------------------------------------
ID                           | true                    | n/a                        | The ID used to identify the domain.

















# Links

## Get All Links

```ruby
require 'uri'
require 'net/http'

url = URI("http://links.sbr.test/api/links")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Get.new(url)
request["accept"] = 'application/json'
request["content-type"] = 'application/json'
request["authorization"] = 'Bearer eyJpdiI6IjVnWUhxUlwvMFZwNTJOR0IwZjhZR1Z3PT0iLCJ2YWx1ZSI6InVuOHVRSVFZdk5aSCtIZVVRS3U2Q085OUFycXFWMTRZSWpBNEF4YXVMOTNNbEYxVitKQkVGYnBPMjl3Sm5jenc4SDIrbVB3cHp3NE45d3JXSFNFTzNcL24rdE1nMFRIZFVCY2liTVFZTjN6RT0iLCJtYWMiOiI5M2EzNjAyZmZlYzllYTZhYjhlNTIyZDdiNGJlYjdkZTQ1NWYzNzhkNzYxMjdlZTk2YmRjOTY2MTRkYTQ4ODljIn0='

response = http.request(request)
puts response.read_body
```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$request->setRequestUrl('http://links.sbr.test/api/links');
$request->setRequestMethod('GET');
$request->setHeaders(array(
  'accept' => 'application/json',
  'content-type' => 'application/json',
  'authorization' => 'Bearer eyJpdiI6IjVnWUhxUlwvMFZwNTJOR0IwZjhZR1Z3PT0iLCJ2YWx1ZSI6InVuOHVRSVFZdk5aSCtIZVVRS3U2Q085OUFycXFWMTRZSWpBNEF4YXVMOTNNbEYxVitKQkVGYnBPMjl3Sm5jenc4SDIrbVB3cHp3NE45d3JXSFNFTzNcL24rdE1nMFRIZFVCY2liTVFZTjN6RT0iLCJtYWMiOiI5M2EzNjAyZmZlYzllYTZhYjhlNTIyZDdiNGJlYjdkZTQ1NWYzNzhkNzYxMjdlZTk2YmRjOTY2MTRkYTQ4ODljIn0='
));

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```shell
curl --request GET \
  --url http://links.sbr.test/api/links \
  --header 'accept: application/json' \
  --header 'authorization: Bearer eyJpdiI6IjVnWUhxUlwvMFZwNTJOR0IwZjhZR1Z3PT0iLCJ2YWx1ZSI6InVuOHVRSVFZdk5aSCtIZVVRS3U2Q085OUFycXFWMTRZSWpBNEF4YXVMOTNNbEYxVitKQkVGYnBPMjl3Sm5jenc4SDIrbVB3cHp3NE45d3JXSFNFTzNcL24rdE1nMFRIZFVCY2liTVFZTjN6RT0iLCJtYWMiOiI5M2EzNjAyZmZlYzllYTZhYjhlNTIyZDdiNGJlYjdkZTQ1NWYzNzhkNzYxMjdlZTk2YmRjOTY2MTRkYTQ4ODljIn0=' \
  --header 'content-type: application/json'
```

```javascript
var request = require("request");

var options = {
  method: 'GET',
  url: 'http://links.sbr.test/api/links',
  headers: {
    accept: 'application/json',
    'content-type': 'application/json',
    authorization: 'Bearer eyJpdiI6IjVnWUhxUlwvMFZwNTJOR0IwZjhZR1Z3PT0iLCJ2YWx1ZSI6InVuOHVRSVFZdk5aSCtIZVVRS3U2Q085OUFycXFWMTRZSWpBNEF4YXVMOTNNbEYxVitKQkVGYnBPMjl3Sm5jenc4SDIrbVB3cHp3NE45d3JXSFNFTzNcL24rdE1nMFRIZFVCY2liTVFZTjN6RT0iLCJtYWMiOiI5M2EzNjAyZmZlYzllYTZhYjhlNTIyZDdiNGJlYjdkZTQ1NWYzNzhkNzYxMjdlZTk2YmRjOTY2MTRkYTQ4ODljIn0='
  }
};

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

> The above command returns JSON structured like this:

```json

```

This endpoint retrieves all links available to the client.

### HTTP Request

`GET https://links.seebot.run/api/links`

### Query Parameters

Parameter                    | Required                | Default                    | Description
---------------------------- | ----------------------- | -------------------------- | ---------------------------------------------------------
page                         | false                   | 1                          | The current page of results to retrieve.
per_page                     | false                   | 25                         | The number of results to pull back. Allowed values: 25, 50, 100, -1 (for all)
sort                         | false                   | desc                       | The order for record sorting.
order                        | false                   | id                         | The field for sorting records. Allowed values: id, name, path, redirect, status


## Get a Link By ID

```ruby
require 'uri'
require 'net/http'

url = URI("http://links.sbr.test/api/links/7")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Get.new(url)
request["accept"] = 'application/json'
request["content-type"] = 'application/json'
request["authorization"] = 'Bearer eyJpdiI6IjVnWUhxUlwvMFZwNTJOR0IwZjhZR1Z3PT0iLCJ2YWx1ZSI6InVuOHVRSVFZdk5aSCtIZVVRS3U2Q085OUFycXFWMTRZSWpBNEF4YXVMOTNNbEYxVitKQkVGYnBPMjl3Sm5jenc4SDIrbVB3cHp3NE45d3JXSFNFTzNcL24rdE1nMFRIZFVCY2liTVFZTjN6RT0iLCJtYWMiOiI5M2EzNjAyZmZlYzllYTZhYjhlNTIyZDdiNGJlYjdkZTQ1NWYzNzhkNzYxMjdlZTk2YmRjOTY2MTRkYTQ4ODljIn0='

response = http.request(request)
puts response.read_body
```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$request->setRequestUrl('http://links.sbr.test/api/links/7');
$request->setRequestMethod('GET');
$request->setHeaders(array(
  'accept' => 'application/json',
  'content-type' => 'application/json',
  'authorization' => 'Bearer eyJpdiI6IjVnWUhxUlwvMFZwNTJOR0IwZjhZR1Z3PT0iLCJ2YWx1ZSI6InVuOHVRSVFZdk5aSCtIZVVRS3U2Q085OUFycXFWMTRZSWpBNEF4YXVMOTNNbEYxVitKQkVGYnBPMjl3Sm5jenc4SDIrbVB3cHp3NE45d3JXSFNFTzNcL24rdE1nMFRIZFVCY2liTVFZTjN6RT0iLCJtYWMiOiI5M2EzNjAyZmZlYzllYTZhYjhlNTIyZDdiNGJlYjdkZTQ1NWYzNzhkNzYxMjdlZTk2YmRjOTY2MTRkYTQ4ODljIn0='
));

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```shell
curl --request GET \
  --url http://links.sbr.test/api/links/7 \
  --header 'accept: application/json' \
  --header 'authorization: Bearer eyJpdiI6IjVnWUhxUlwvMFZwNTJOR0IwZjhZR1Z3PT0iLCJ2YWx1ZSI6InVuOHVRSVFZdk5aSCtIZVVRS3U2Q085OUFycXFWMTRZSWpBNEF4YXVMOTNNbEYxVitKQkVGYnBPMjl3Sm5jenc4SDIrbVB3cHp3NE45d3JXSFNFTzNcL24rdE1nMFRIZFVCY2liTVFZTjN6RT0iLCJtYWMiOiI5M2EzNjAyZmZlYzllYTZhYjhlNTIyZDdiNGJlYjdkZTQ1NWYzNzhkNzYxMjdlZTk2YmRjOTY2MTRkYTQ4ODljIn0=' \
  --header 'content-type: application/json'
```

```javascript
var request = require("request");

var options = {
  method: 'GET',
  url: 'http://links.sbr.test/api/links/7',
  headers: {
    accept: 'application/json',
    'content-type': 'application/json',
    authorization: 'Bearer eyJpdiI6IjVnWUhxUlwvMFZwNTJOR0IwZjhZR1Z3PT0iLCJ2YWx1ZSI6InVuOHVRSVFZdk5aSCtIZVVRS3U2Q085OUFycXFWMTRZSWpBNEF4YXVMOTNNbEYxVitKQkVGYnBPMjl3Sm5jenc4SDIrbVB3cHp3NE45d3JXSFNFTzNcL24rdE1nMFRIZFVCY2liTVFZTjN6RT0iLCJtYWMiOiI5M2EzNjAyZmZlYzllYTZhYjhlNTIyZDdiNGJlYjdkZTQ1NWYzNzhkNzYxMjdlZTk2YmRjOTY2MTRkYTQ4ODljIn0='
  }
};

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": 7,
    "name": "Test Link",
    "path": "testing",
    "redirect": "https:\/\/seebot.run",
    "status": "active",
    "health_status": "unknown",
    "health_checked_at": null,
    "domain_id": 4,
    "generated_url": "http:\/\/seebot.test\/testing",
    "tags": [
      {
        "id": 1,
        "name": "Important",
        "color": "#C0382B",
        "status": "active",
        "pivot": {
          "link_id": 7,
          "tag_id": 1
        }
      },
      {
        "id": 2,
        "name": "Special",
        "color": "#8E43AD",
        "status": "active",
        "pivot": {
          "link_id": 7,
          "tag_id": 2
        }
      }
    ],
    "domain": {
      "id": 4,
      "name": "seebot.test",
      "url": "seebot.test",
      "status": "deleted",
      "scope": "client",
      "default_root_url": null,
      "default_catchall_url": null
    }
  }
}
```

This endpoint retrieves a link owned by a client.

### HTTP Request

`GET http://links.sbr.test/api/links/<ID>`

### URL Parameters

Parameter                    | Required                | Default                    | Description
---------------------------- | ----------------------- | -------------------------- | ---------------------------------------------------------
ID                           | true                    | n/a                        | The ID used to identify the link.


## Create a New Link

```ruby
require 'uri'
require 'net/http'

url = URI("http://links.sbr.test/api/links")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Post.new(url)
request["accept"] = 'application/json'
request["content-type"] = 'application/json'
request["authorization"] = 'Bearer eyJpdiI6IjVnWUhxUlwvMFZwNTJOR0IwZjhZR1Z3PT0iLCJ2YWx1ZSI6InVuOHVRSVFZdk5aSCtIZVVRS3U2Q085OUFycXFWMTRZSWpBNEF4YXVMOTNNbEYxVitKQkVGYnBPMjl3Sm5jenc4SDIrbVB3cHp3NE45d3JXSFNFTzNcL24rdE1nMFRIZFVCY2liTVFZTjN6RT0iLCJtYWMiOiI5M2EzNjAyZmZlYzllYTZhYjhlNTIyZDdiNGJlYjdkZTQ1NWYzNzhkNzYxMjdlZTk2YmRjOTY2MTRkYTQ4ODljIn0='
request.body = "{\n\t\"name\": \"Test Link\",\n\t\"path\": \"testing\",\n\t\"redirect\": \"https://seebot.run\",\n\t\"domain_id\": 4,\n\t\"status\": \"active\",\n\t\"tags\": [1,2]\n}"

response = http.request(request)
puts response.read_body
```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$body = new http\Message\Body;
$body->append('{
	"name": "Test Link",
	"path": "testing",
	"redirect": "https://seebot.run",
	"domain_id": 4,
	"status": "active",
	"tags": [1,2]
}');

$request->setRequestUrl('http://links.sbr.test/api/links');
$request->setRequestMethod('POST');
$request->setBody($body);

$request->setHeaders(array(
  'accept' => 'application/json',
  'content-type' => 'application/json',
  'authorization' => 'Bearer eyJpdiI6IjVnWUhxUlwvMFZwNTJOR0IwZjhZR1Z3PT0iLCJ2YWx1ZSI6InVuOHVRSVFZdk5aSCtIZVVRS3U2Q085OUFycXFWMTRZSWpBNEF4YXVMOTNNbEYxVitKQkVGYnBPMjl3Sm5jenc4SDIrbVB3cHp3NE45d3JXSFNFTzNcL24rdE1nMFRIZFVCY2liTVFZTjN6RT0iLCJtYWMiOiI5M2EzNjAyZmZlYzllYTZhYjhlNTIyZDdiNGJlYjdkZTQ1NWYzNzhkNzYxMjdlZTk2YmRjOTY2MTRkYTQ4ODljIn0='
));

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```shell
curl --request POST \
  --url http://links.sbr.test/api/links \
  --header 'accept: application/json' \
  --header 'authorization: Bearer eyJpdiI6IjVnWUhxUlwvMFZwNTJOR0IwZjhZR1Z3PT0iLCJ2YWx1ZSI6InVuOHVRSVFZdk5aSCtIZVVRS3U2Q085OUFycXFWMTRZSWpBNEF4YXVMOTNNbEYxVitKQkVGYnBPMjl3Sm5jenc4SDIrbVB3cHp3NE45d3JXSFNFTzNcL24rdE1nMFRIZFVCY2liTVFZTjN6RT0iLCJtYWMiOiI5M2EzNjAyZmZlYzllYTZhYjhlNTIyZDdiNGJlYjdkZTQ1NWYzNzhkNzYxMjdlZTk2YmRjOTY2MTRkYTQ4ODljIn0=' \
  --header 'content-type: application/json' \
  --data '{
	"name": "Test Link",
	"path": "testing",
	"redirect": "https://seebot.run",
	"domain_id": 4,
	"status": "active",
	"tags": [1,2]
}'
```

```javascript
var request = require("request");

var options = {
  method: 'POST',
  url: 'http://links.sbr.test/api/links',
  headers: {
    accept: 'application/json',
    'content-type': 'application/json',
    authorization: 'Bearer eyJpdiI6IjVnWUhxUlwvMFZwNTJOR0IwZjhZR1Z3PT0iLCJ2YWx1ZSI6InVuOHVRSVFZdk5aSCtIZVVRS3U2Q085OUFycXFWMTRZSWpBNEF4YXVMOTNNbEYxVitKQkVGYnBPMjl3Sm5jenc4SDIrbVB3cHp3NE45d3JXSFNFTzNcL24rdE1nMFRIZFVCY2liTVFZTjN6RT0iLCJtYWMiOiI5M2EzNjAyZmZlYzllYTZhYjhlNTIyZDdiNGJlYjdkZTQ1NWYzNzhkNzYxMjdlZTk2YmRjOTY2MTRkYTQ4ODljIn0='
  },
  body: {
    name: 'Test Link',
    path: 'testing',
    redirect: 'https://seebot.run',
    domain_id: 4,
    status: 'active',
    tags: [1, 2]
  },
  json: true
};

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

> The above command returns JSON structured like this:

```json
{
  "id": 7,
  "name": "Test Link",
  "path": "testing",
  "redirect": "https:\/\/seebot.run",
  "status": "active",
  "health_status": "unknown",
  "health_checked_at": null,
  "domain_id": 4,
  "generated_url": "http:\/\/seebot.test\/testing",
  "domain": {
    "id": 4,
    "name": "seebot.test",
    "url": "seebot.test",
    "status": "deleted",
    "scope": "client",
    "default_root_url": null,
    "default_catchall_url": null
  }
}
```

This endpoint creates a new link and associates it with the domain specified.

### HTTP Request

`POST http://links.sbr.test/api/links`

### Body Parameters

Parameter                    | Required                | Default                    | Description
---------------------------- | ----------------------- | -------------------------- | ---------------------------------------------------------
name                         | true                    | n/a                        | The name used to easily identify the link.
path                         | true                    | n/a                        | The path used to identify the the link to be redirected. Value after the root of the domain. Must be unique.
redirect                     | true                    | n/a                        | The URL (with schema) to redirect visitors to when visiting the specified path.
domain_id                    | true                    | n/a                        | The Domain ID the link will be associated with.
status                       | true                    | active                     | The status of the link. Allowed values: active, inactive.
tags                         | false                   | []                         | Array of Tag IDs that will be associated with the link.


## Update an Existing Link

```ruby
require 'uri'
require 'net/http'

url = URI("http://links.sbr.test/api/links/7")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Put.new(url)
request["accept"] = 'application/json'
request["content-type"] = 'application/json'
request["authorization"] = 'Bearer eyJpdiI6IjVnWUhxUlwvMFZwNTJOR0IwZjhZR1Z3PT0iLCJ2YWx1ZSI6InVuOHVRSVFZdk5aSCtIZVVRS3U2Q085OUFycXFWMTRZSWpBNEF4YXVMOTNNbEYxVitKQkVGYnBPMjl3Sm5jenc4SDIrbVB3cHp3NE45d3JXSFNFTzNcL24rdE1nMFRIZFVCY2liTVFZTjN6RT0iLCJtYWMiOiI5M2EzNjAyZmZlYzllYTZhYjhlNTIyZDdiNGJlYjdkZTQ1NWYzNzhkNzYxMjdlZTk2YmRjOTY2MTRkYTQ4ODljIn0='
request.body = "{\n\t\"name\": \"Test Link\",\n\t\"path\": \"testing\",\n\t\"redirect\": \"https://seebot.run\",\n\t\"domain_id\": 4,\n\t\"status\": \"active\",\n\t\"tags\": [1,2]\n}"

response = http.request(request)
puts response.read_body
```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$body = new http\Message\Body;
$body->append('{
	"name": "Test Link",
	"path": "testing",
	"redirect": "https://seebot.run",
	"domain_id": 4,
	"status": "active",
	"tags": [1,2]
}');

$request->setRequestUrl('http://links.sbr.test/api/links/7');
$request->setRequestMethod('PUT');
$request->setBody($body);

$request->setHeaders(array(
  'accept' => 'application/json',
  'content-type' => 'application/json',
  'authorization' => 'Bearer eyJpdiI6IjVnWUhxUlwvMFZwNTJOR0IwZjhZR1Z3PT0iLCJ2YWx1ZSI6InVuOHVRSVFZdk5aSCtIZVVRS3U2Q085OUFycXFWMTRZSWpBNEF4YXVMOTNNbEYxVitKQkVGYnBPMjl3Sm5jenc4SDIrbVB3cHp3NE45d3JXSFNFTzNcL24rdE1nMFRIZFVCY2liTVFZTjN6RT0iLCJtYWMiOiI5M2EzNjAyZmZlYzllYTZhYjhlNTIyZDdiNGJlYjdkZTQ1NWYzNzhkNzYxMjdlZTk2YmRjOTY2MTRkYTQ4ODljIn0='
));

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```shell
curl --request PUT \
  --url http://links.sbr.test/api/links/7 \
  --header 'accept: application/json' \
  --header 'authorization: Bearer eyJpdiI6IjVnWUhxUlwvMFZwNTJOR0IwZjhZR1Z3PT0iLCJ2YWx1ZSI6InVuOHVRSVFZdk5aSCtIZVVRS3U2Q085OUFycXFWMTRZSWpBNEF4YXVMOTNNbEYxVitKQkVGYnBPMjl3Sm5jenc4SDIrbVB3cHp3NE45d3JXSFNFTzNcL24rdE1nMFRIZFVCY2liTVFZTjN6RT0iLCJtYWMiOiI5M2EzNjAyZmZlYzllYTZhYjhlNTIyZDdiNGJlYjdkZTQ1NWYzNzhkNzYxMjdlZTk2YmRjOTY2MTRkYTQ4ODljIn0=' \
  --header 'content-type: application/json' \
  --data '{
	"name": "Test Link",
	"path": "testing",
	"redirect": "https://seebot.run",
	"domain_id": 4,
	"status": "active",
	"tags": [1,2]
}'
```

```javascript
var request = require("request");

var options = {
  method: 'PUT',
  url: 'http://links.sbr.test/api/links/7',
  headers: {
    accept: 'application/json',
    'content-type': 'application/json',
    authorization: 'Bearer eyJpdiI6IjVnWUhxUlwvMFZwNTJOR0IwZjhZR1Z3PT0iLCJ2YWx1ZSI6InVuOHVRSVFZdk5aSCtIZVVRS3U2Q085OUFycXFWMTRZSWpBNEF4YXVMOTNNbEYxVitKQkVGYnBPMjl3Sm5jenc4SDIrbVB3cHp3NE45d3JXSFNFTzNcL24rdE1nMFRIZFVCY2liTVFZTjN6RT0iLCJtYWMiOiI5M2EzNjAyZmZlYzllYTZhYjhlNTIyZDdiNGJlYjdkZTQ1NWYzNzhkNzYxMjdlZTk2YmRjOTY2MTRkYTQ4ODljIn0='
  },
  body: {
    name: 'Test Link',
    path: 'testing',
    redirect: 'https://seebot.run',
    domain_id: 4,
    status: 'active',
    tags: [1, 2]
  },
  json: true
};

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

> The above command returns JSON structured like this:

```json
{
  "id": 7,
  "name": "Test Link",
  "path": "testing",
  "redirect": "https:\/\/seebot.run",
  "status": "active",
  "health_status": "unknown",
  "health_checked_at": null,
  "domain_id": 4,
  "generated_url": "http:\/\/seebot.test\/testing",
  "domain": {
    "id": 4,
    "name": "seebot.test",
    "url": "seebot.test",
    "status": "deleted",
    "scope": "client",
    "default_root_url": null,
    "default_catchall_url": null
  }
}
```

This endpoint updates an existing link owned by a client.

### HTTP Request

`PUT http://links.sbr.test/api/links/<ID>`

### URL Parameters

Parameter                    | Required                | Default                    | Description
---------------------------- | ----------------------- | -------------------------- | ---------------------------------------------------------
ID                           | true                    | n/a                        | The ID used to identify the link.

### Body Parameters

Parameter                    | Required                | Default                    | Description
---------------------------- | ----------------------- | -------------------------- | ---------------------------------------------------------
name                         | true                    | n/a                        | The name used to easily identify the link.
path                         | true                    | n/a                        | The path used to identify the the link to be redirected. Value after the root of the domain.
redirect                     | true                    | n/a                        | The URL (with schema) to redirect visitors to when visiting the specified path.
domain_id                    | true                    | n/a                        | The Domain ID the link will be associated with.
status                       | true                    | active                     | The status of the link. Allowed values: active, inactive.
tags                         | false                   | []                         | Array of Tag IDs that will be associated with the link.


## Delete a Specific Link

```ruby
require 'uri'
require 'net/http'

url = URI("http://links.sbr.test/api/links/7")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Delete.new(url)
request["accept"] = 'application/json'
request["authorization"] = 'Bearer eyJpdiI6IjVnWUhxUlwvMFZwNTJOR0IwZjhZR1Z3PT0iLCJ2YWx1ZSI6InVuOHVRSVFZdk5aSCtIZVVRS3U2Q085OUFycXFWMTRZSWpBNEF4YXVMOTNNbEYxVitKQkVGYnBPMjl3Sm5jenc4SDIrbVB3cHp3NE45d3JXSFNFTzNcL24rdE1nMFRIZFVCY2liTVFZTjN6RT0iLCJtYWMiOiI5M2EzNjAyZmZlYzllYTZhYjhlNTIyZDdiNGJlYjdkZTQ1NWYzNzhkNzYxMjdlZTk2YmRjOTY2MTRkYTQ4ODljIn0='

response = http.request(request)
puts response.read_body
```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$request->setRequestUrl('http://links.sbr.test/api/links/7');
$request->setRequestMethod('DELETE');
$request->setHeaders(array(
  'accept' => 'application/json',
  'authorization' => 'Bearer eyJpdiI6IjVnWUhxUlwvMFZwNTJOR0IwZjhZR1Z3PT0iLCJ2YWx1ZSI6InVuOHVRSVFZdk5aSCtIZVVRS3U2Q085OUFycXFWMTRZSWpBNEF4YXVMOTNNbEYxVitKQkVGYnBPMjl3Sm5jenc4SDIrbVB3cHp3NE45d3JXSFNFTzNcL24rdE1nMFRIZFVCY2liTVFZTjN6RT0iLCJtYWMiOiI5M2EzNjAyZmZlYzllYTZhYjhlNTIyZDdiNGJlYjdkZTQ1NWYzNzhkNzYxMjdlZTk2YmRjOTY2MTRkYTQ4ODljIn0='
));

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```shell
curl --request DELETE \
  --url http://links.sbr.test/api/links/7 \
  --header 'accept: application/json' \
  --header 'authorization: Bearer eyJpdiI6IjVnWUhxUlwvMFZwNTJOR0IwZjhZR1Z3PT0iLCJ2YWx1ZSI6InVuOHVRSVFZdk5aSCtIZVVRS3U2Q085OUFycXFWMTRZSWpBNEF4YXVMOTNNbEYxVitKQkVGYnBPMjl3Sm5jenc4SDIrbVB3cHp3NE45d3JXSFNFTzNcL24rdE1nMFRIZFVCY2liTVFZTjN6RT0iLCJtYWMiOiI5M2EzNjAyZmZlYzllYTZhYjhlNTIyZDdiNGJlYjdkZTQ1NWYzNzhkNzYxMjdlZTk2YmRjOTY2MTRkYTQ4ODljIn0='
```

```javascript
var request = require("request");

var options = {
  method: 'DELETE',
  url: 'http://links.sbr.test/api/links/7',
  headers: {
    accept: 'application/json',
    authorization: 'Bearer eyJpdiI6IjVnWUhxUlwvMFZwNTJOR0IwZjhZR1Z3PT0iLCJ2YWx1ZSI6InVuOHVRSVFZdk5aSCtIZVVRS3U2Q085OUFycXFWMTRZSWpBNEF4YXVMOTNNbEYxVitKQkVGYnBPMjl3Sm5jenc4SDIrbVB3cHp3NE45d3JXSFNFTzNcL24rdE1nMFRIZFVCY2liTVFZTjN6RT0iLCJtYWMiOiI5M2EzNjAyZmZlYzllYTZhYjhlNTIyZDdiNGJlYjdkZTQ1NWYzNzhkNzYxMjdlZTk2YmRjOTY2MTRkYTQ4ODljIn0='
  }
};

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

> The above command returns no content with a 204 response on success.

This endpoint deletes a link.

### HTTP Request

`DELETE http://links.sbr.test/api/links/<ID>`

### URL Parameters

Parameter                    | Required                | Default                    | Description
---------------------------- | ----------------------- | -------------------------- | ---------------------------------------------------------
ID                           | true                    | n/a                        | The ID used to identify the link.

