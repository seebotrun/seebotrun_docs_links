# Tags

## Get All Tags

```ruby
require 'uri'
require 'net/http'

url = URI("http://links.seebot.run/api/tags")

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

$request->setRequestUrl('http://links.seebot.run/api/tags');
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
  --url http://links.seebot.run/api/tags \
  --header 'accept: application/json' \
  --header 'authorization: Bearer ##YourAPITokenHere##' \
  --header 'content-type: application/json'
```

```javascript
var request = require("request");

var options = {
  method: 'GET',
  url: 'http://links.seebot.run/api/tags',
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
      "id": 5,
      "name": "Test Tag",
      "color": "#1FBC9C",
      "status": "active"
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

This endpoint retrieves all tags available to the client.

### HTTP Request

`GET https://links.seebot.run/api/tags`

### Query Parameters

Parameter                    | Required                | Default                    | Description
---------------------------- | ----------------------- | -------------------------- | ---------------------------------------------------------
page                         | false                   | 1                          | The current page of results to retrieve.
per_page                     | false                   | 25                         | The number of results to pull back. Allowed values: 25, 50, 100, -1 (for all)
sort                         | false                   | desc                       | The order for record sorting.
order                        | false                   | id                         | The field for sorting records. Allowed values: id, name, color, status



## Get a Tag By ID

```ruby
require 'uri'
require 'net/http'

url = URI("http://links.seebot.run/api/tags/5")

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

$request->setRequestUrl('http://links.seebot.run/api/tags/5');
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
  --url http://links.seebot.run/api/tags/5 \
  --header 'accept: application/json' \
  --header 'authorization: Bearer ##YourAPITokenHere##' \
  --header 'content-type: application/json'
```

```javascript
var request = require("request");

var options = {
  method: 'GET',
  url: 'http://links.seebot.run/api/tags/5',
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
    "id": 5,
    "name": "Test Tag",
    "color": "#1FBC9C",
    "status": "active"
  }
}
```

This endpoint retrieves a tag owned by a client.

### HTTP Request

`GET http://links.seebot.run/api/tags/<ID>`

### URL Parameters

Parameter                    | Required                | Default                    | Description
---------------------------- | ----------------------- | -------------------------- | ---------------------------------------------------------
ID                           | true                    | n/a                        | The ID used to identify the tag.



## Create a New Tag

```ruby
require 'uri'
require 'net/http'

url = URI("http://links.seebot.run/api/tags")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Post.new(url)
request["accept"] = 'application/json'
request["content-type"] = 'application/json'
request["authorization"] = 'Bearer ##YourAPITokenHere##'
request.body = "{\n\t\"name\": \"Test Tag\",\n\t\"color\": \"#1FBC9C\",\n\t\"status\": \"active\"\n}"

response = http.request(request)
puts response.read_body
```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$body = new http\Message\Body;
$body->append('{
	"name": "Test Tag",
	"color": "#1FBC9C",
	"status": "active"
}');

$request->setRequestUrl('http://links.seebot.run/api/tags');
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
  --url http://links.seebot.run/api/tags \
  --header 'accept: application/json' \
  --header 'authorization: Bearer ##YourAPITokenHere##' \
  --header 'content-type: application/json' \
  --data '{
	"name": "Test Tag",
	"color": "#1FBC9C",
	"status": "active"
}'
```

```javascript
var request = require("request");

var options = {
  method: 'POST',
  url: 'http://links.seebot.run/api/tags',
  headers: {
    accept: 'application/json',
    'content-type': 'application/json',
    authorization: 'Bearer ##YourAPITokenHere##'
  },
  body: {name: 'Test Tag', color: '#1FBC9C', status: 'active'},
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
    "name": "Test Tag",
    "color": "#1FBC9C",
    "status": "active",
    "id": 5
  }
}
```

This endpoint creates a new tag and associates it with the client.

### HTTP Request

`POST http://links.seebot.run/api/tags`

### Body Parameters

Parameter                    | Required                | Default                    | Description
---------------------------- | ----------------------- | -------------------------- | ---------------------------------------------------------
name                         | true                    | n/a                        | The name used to easily identify the tag.
color                        | true                    | n/a                        | The hex color used to identify the tag in the admin UI.
status                       | true                    | active                     | The status of the tag. Allowed values: active, inactive.



## Update an Existing Tag

```ruby
require 'uri'
require 'net/http'

url = URI("http://links.seebot.run/api/tags/5")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Put.new(url)
request["accept"] = 'application/json'
request["content-type"] = 'application/json'
request["authorization"] = 'Bearer ##YourAPITokenHere##'
request.body = "{\n\t\"name\": \"Test Tag\",\n\t\"color\": \"#1FBC9C\",\n\t\"status\": \"active\"\n}"

response = http.request(request)
puts response.read_body
```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$body = new http\Message\Body;
$body->append('{
	"name": "Test Tag",
	"color": "#1FBC9C",
	"status": "active"
}');

$request->setRequestUrl('http://links.seebot.run/api/tags/5');
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
  --url http://links.seebot.run/api/tags/5 \
  --header 'accept: application/json' \
  --header 'authorization: Bearer ##YourAPITokenHere##' \
  --header 'content-type: application/json' \
  --data '{
	"name": "Test Tag",
	"color": "#1FBC9C",
	"status": "active"
}'
```

```javascript
var request = require("request");

var options = {
  method: 'PUT',
  url: 'http://links.seebot.run/api/tags/5',
  headers: {
    accept: 'application/json',
    'content-type': 'application/json',
    authorization: 'Bearer ##YourAPITokenHere##'
  },
  body: {name: 'Test Tag', color: '#1FBC9C', status: 'active'},
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
    "id": 5,
    "name": "Test Tag",
    "color": "#1FBC9C",
    "status": "active"
  }
}
```

This endpoint updates an existing tag owned by a client.

### HTTP Request

`PUT http://links.seebot.run/api/tags/<ID>`

### URL Parameters

Parameter                    | Required                | Default                    | Description
---------------------------- | ----------------------- | -------------------------- | ---------------------------------------------------------
ID                           | true                    | n/a                        | The ID used to identify the tag.

### Body Parameters

Parameter                    | Required                | Default                    | Description
---------------------------- | ----------------------- | -------------------------- | ---------------------------------------------------------
name                         | true                    | n/a                        | The name used to easily identify the tag.
color                        | true                    | n/a                        | The hex color used to identify the tag in the admin UI.
status                       | true                    | active                     | The status of the tag. Allowed values: active, inactive.



## Delete a Specific Tag

```ruby
require 'uri'
require 'net/http'

url = URI("http://links.seebot.run/api/tags/5")

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

$request->setRequestUrl('http://links.seebot.run/api/tags/5');
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
  --url http://links.seebot.run/api/tags/5 \
  --header 'accept: application/json' \
  --header 'authorization: Bearer ##YourAPITokenHere##'
```

```javascript
var request = require("request");

var options = {
  method: 'DELETE',
  url: 'http://links.seebot.run/api/tags/5',
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

This endpoint deletes a tag.

### HTTP Request

`DELETE http://links.seebot.run/api/tags/<ID>`

### URL Parameters

Parameter                    | Required                | Default                    | Description
---------------------------- | ----------------------- | -------------------------- | ---------------------------------------------------------
ID                           | true                    | n/a                        | The ID used to identify the tag.
