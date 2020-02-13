# Links

## Get All Links

```ruby
require 'uri'
require 'net/http'

url = URI("http://links.seebot.run/api/links?domain_id=4")

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

$request->setRequestUrl('http://links.seebot.run/api/links');
$request->setRequestMethod('GET');
$request->setQuery(new http\QueryString(array(
  'domain_id' => '4'
)));

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
  --url 'http://links.seebot.run/api/links?domain_id=4' \
  --header 'accept: application/json' \
  --header 'authorization: Bearer ##YourAPITokenHere##' \
  --header 'content-type: application/json'
```

```javascript
var request = require("request");

var options = {
  method: 'GET',
  url: 'http://links.seebot.run/api/links',
  qs: {domain_id: '4'},
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
      },
      "tags": [
        {
          "id": 1,
          "name": "Important",
          "color": "#C0382B",
          "status": "active"
        },
        {
          "id": 2,
          "name": "Special",
          "color": "#8E43AD",
          "status": "active"
        }
      ]
    }
  ],
  "meta": {
    "total": 1,
    "count": 1,
    "page": 1,
    "pages": 1,
    "per_page": 25,
    "order": "id",
    "sort": "DESC"
  }
}
```

This endpoint retrieves all links available to the client.

### HTTP Request

`GET https://links.seebot.run/api/links`

### Query Parameters

Parameter                    | Required                | Default                    | Description
---------------------------- | ----------------------- | -------------------------- | ---------------------------------------------------------
domain_id                    | true                    | n/a                        | The Domain ID used to retrieve links. Required to return links.
page                         | false                   | 1                          | The current page of results to retrieve.
per_page                     | false                   | 25                         | The number of results to pull back. Allowed values: 25, 50, 100, -1 (for all)
sort                         | false                   | desc                       | The order for record sorting.
order                        | false                   | id                         | The field for sorting records. Allowed values: id, name, path, redirect, status


## Get a Link By ID

```ruby
require 'uri'
require 'net/http'

url = URI("http://links.seebot.run/api/links/7")

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

$request->setRequestUrl('http://links.seebot.run/api/links/7');
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
  --url http://links.seebot.run/api/links/7 \
  --header 'accept: application/json' \
  --header 'authorization: Bearer ##YourAPITokenHere##' \
  --header 'content-type: application/json'
```

```javascript
var request = require("request");

var options = {
  method: 'GET',
  url: 'http://links.seebot.run/api/links/7',
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

`GET http://links.seebot.run/api/links/<ID>`

### URL Parameters

Parameter                    | Required                | Default                    | Description
---------------------------- | ----------------------- | -------------------------- | ---------------------------------------------------------
ID                           | true                    | n/a                        | The ID used to identify the link.


## Create a New Link

```ruby
require 'uri'
require 'net/http'

url = URI("http://links.seebot.run/api/links")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Post.new(url)
request["accept"] = 'application/json'
request["content-type"] = 'application/json'
request["authorization"] = 'Bearer ##YourAPITokenHere##'
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

$request->setRequestUrl('http://links.seebot.run/api/links');
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
  --url http://links.seebot.run/api/links \
  --header 'accept: application/json' \
  --header 'authorization: Bearer ##YourAPITokenHere##' \
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
  url: 'http://links.seebot.run/api/links',
  headers: {
    accept: 'application/json',
    'content-type': 'application/json',
    authorization: 'Bearer ##YourAPITokenHere##'
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

`POST http://links.seebot.run/api/links`

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

url = URI("http://links.seebot.run/api/links/7")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Put.new(url)
request["accept"] = 'application/json'
request["content-type"] = 'application/json'
request["authorization"] = 'Bearer ##YourAPITokenHere##'
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

$request->setRequestUrl('http://links.seebot.run/api/links/7');
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
  --url http://links.seebot.run/api/links/7 \
  --header 'accept: application/json' \
  --header 'authorization: Bearer ##YourAPITokenHere##' \
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
  url: 'http://links.seebot.run/api/links/7',
  headers: {
    accept: 'application/json',
    'content-type': 'application/json',
    authorization: 'Bearer ##YourAPITokenHere##'
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

`PUT http://links.seebot.run/api/links/<ID>`

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

url = URI("http://links.seebot.run/api/links/7")

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

$request->setRequestUrl('http://links.seebot.run/api/links/7');
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
  --url http://links.seebot.run/api/links/7 \
  --header 'accept: application/json' \
  --header 'authorization: Bearer ##YourAPITokenHere##'
```

```javascript
var request = require("request");

var options = {
  method: 'DELETE',
  url: 'http://links.seebot.run/api/links/7',
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

This endpoint deletes a link.

### HTTP Request

`DELETE http://links.seebot.run/api/links/<ID>`

### URL Parameters

Parameter                    | Required                | Default                    | Description
---------------------------- | ----------------------- | -------------------------- | ---------------------------------------------------------
ID                           | true                    | n/a                        | The ID used to identify the link.

