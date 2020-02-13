# Domains

## Get All Domains

```ruby
require 'uri'
require 'net/http'

url = URI("http://links.seebot.run/api/domains")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Get.new(url)
request["accept"] = 'application/json'
request["content-type"] = 'application/json'
request["authorization"] = 'Bearer ##YourAPITokenHere##'

response = http.request(request)
puts response.read_body
```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$request->setRequestUrl('http://links.seebot.run/api/domains');
$request->setRequestMethod('GET');
$request->setHeaders(array(
  'accept' => 'application/json',
  'content-type' => 'application/json',
  'authorization' => 'Bearer ##YourAPITokenHere##'
));

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```shell
curl --request GET \
  --url http://links.seebot.run/api/domains \
  --header 'accept: application/json' \
  --header 'authorization: Bearer ##YourAPITokenHere##' \
  --header 'content-type: application/json'
```

```javascript
var request = require("request");

var options = {
  method: 'GET',
  url: 'http://links.seebot.run/api/domains',
  headers: {
    accept: 'application/json',
    'content-type': 'application/json',
    authorization: 'Bearer ##YourAPITokenHere##'
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

url = URI("http://links.seebot.run/api/domains/4")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Get.new(url)
request["accept"] = 'application/json'
request["content-type"] = 'application/json'
request["authorization"] = 'Bearer ##YourAPITokenHere##'

response = http.request(request)
puts response.read_body
```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$request->setRequestUrl('http://links.seebot.run/api/domains/4');
$request->setRequestMethod('GET');
$request->setHeaders(array(
  'accept' => 'application/json',
  'content-type' => 'application/json',
  'authorization' => 'Bearer ##YourAPITokenHere##'
));

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```shell
curl --request GET \
  --url http://links.seebot.run/api/domains/4 \
  --header 'accept: application/json' \
  --header 'authorization: Bearer ##YourAPITokenHere##' \
  --header 'content-type: application/json'
```

```javascript
var request = require("request");

var options = {
  method: 'GET',
  url: 'http://links.seebot.run/api/domains/4',
  headers: {
    accept: 'application/json',
    'content-type': 'application/json',
    authorization: 'Bearer ##YourAPITokenHere##'
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

`GET http://links.seebot.run/api/domains/<ID>`

### URL Parameters

Parameter                    | Required                | Default                    | Description
---------------------------- | ----------------------- | -------------------------- | ---------------------------------------------------------
ID                           | true                    | n/a                        | The ID used to identify the domain.



## Create a New Domain

```ruby
require 'uri'
require 'net/http'

url = URI("http://links.seebot.run/api/domains")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Post.new(url)
request["accept"] = 'application/json'
request["content-type"] = 'application/json'
request["authorization"] = 'Bearer ##YourAPITokenHere##'
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

$request->setRequestUrl('http://links.seebot.run/api/domains');
$request->setRequestMethod('POST');
$request->setBody($body);

$request->setHeaders(array(
  'accept' => 'application/json',
  'content-type' => 'application/json',
  'authorization' => 'Bearer ##YourAPITokenHere##'
));

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```shell
curl --request POST \
  --url http://links.seebot.run/api/domains \
  --header 'accept: application/json' \
  --header 'authorization: Bearer ##YourAPITokenHere##' \
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
  url: 'http://links.seebot.run/api/domains',
  headers: {
    accept: 'application/json',
    'content-type': 'application/json',
    authorization: 'Bearer ##YourAPITokenHere##'
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

`POST http://links.seebot.run/api/domains`

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

url = URI("http://links.seebot.run/api/domains/4")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Put.new(url)
request["accept"] = 'application/json'
request["content-type"] = 'application/json'
request["authorization"] = 'Bearer ##YourAPITokenHere##'
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

$request->setRequestUrl('http://links.seebot.run/api/domains/4');
$request->setRequestMethod('PUT');
$request->setBody($body);

$request->setHeaders(array(
  'accept' => 'application/json',
  'content-type' => 'application/json',
  'authorization' => 'Bearer ##YourAPITokenHere##'
));

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```shell
curl --request PUT \
  --url http://links.seebot.run/api/domains/4 \
  --header 'accept: application/json' \
  --header 'authorization: Bearer ##YourAPITokenHere##' \
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
  url: 'http://links.seebot.run/api/domains/4',
  headers: {
    accept: 'application/json',
    'content-type': 'application/json',
    authorization: 'Bearer ##YourAPITokenHere##'
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

`PUT http://links.seebot.run/api/domains/<ID>`

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

url = URI("http://links.seebot.run/api/domains/4")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Delete.new(url)
request["accept"] = 'application/json'
request["authorization"] = 'Bearer ##YourAPITokenHere##'

response = http.request(request)
puts response.read_body
```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$request->setRequestUrl('http://links.seebot.run/api/domains/4');
$request->setRequestMethod('DELETE');
$request->setHeaders(array(
  'accept' => 'application/json',
  'authorization' => 'Bearer ##YourAPITokenHere##'
));

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```shell
curl --request DELETE \
  --url http://links.seebot.run/api/domains/4 \
  --header 'accept: application/json' \
  --header 'authorization: Bearer ##YourAPITokenHere##'
```

```javascript
var request = require("request");

var options = {
  method: 'DELETE',
  url: 'http://links.seebot.run/api/domains/4',
  headers: {
    accept: 'application/json',
    authorization: 'Bearer ##YourAPITokenHere##'
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

`DELETE http://links.seebot.run/api/domains/<ID>`

### URL Parameters

Parameter                    | Required                | Default                    | Description
---------------------------- | ----------------------- | -------------------------- | ---------------------------------------------------------
ID                           | true                    | n/a                        | The ID used to identify the domain.
