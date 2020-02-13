---
title: SeeBotRun - Shortener API

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - ruby
  - php
  - javascript

toc_footers:

includes:
  - domains
  - tags
  - links
  - reports
  - errors

search: true
---





# Introduction

The SeeBotRun Shortener API is a REST API designed to provide a clear, concise pathway into a client's account.





# Authentication

> To authorize, use this code:

```ruby
require 'uri'
require 'net/http'

url = URI("http://portal.seebot.run/api/auth/login")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Post.new(url)
request["content-type"] = 'application/json'
request["accept"] = 'application/json'
request.body = "{\n\t\"email\": \"test@example.com\",\n\t\"password\": \"testingtest\"\n}"

response = http.request(request)
puts response.read_body
```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$body = new http\Message\Body;
$body->append('{
	"email": "test@example.com",
	"password": "testingtest"
}');

$request->setRequestUrl('http://portal.seebot.run/api/auth/login');
$request->setRequestMethod('POST');
$request->setBody($body);

$request->setHeaders(array(
  'content-type' => 'application/json',
  'accept' => 'application/json'
));

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```shell
curl --request POST \
  --url http://portal.seebot.run/api/auth/login \
  --header 'accept: application/json' \
  --header 'content-type: application/json' \
  --data '{
	"email": "test@example.com",
	"password": "testingtest"
}'
```

```javascript
var request = require("request");

var options = {
  method: 'POST',
  url: 'http://portal.seebot.run/api/auth/login',
  headers: {
    'content-type': 'application/json',
    accept: 'application/json'
  },
  body: {email: 'test@example.com', password: 'testingtest'},
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
  "access_token": "##YourAPITokenHere##",
  "expires_at": "2020-02-14 05:45:21",
  "user": {
    "id": 1,
    "first_name": "Test",
    "last_name": "User",
    "email": "test@example.com",
    "client_id": 2,
    "is_admin": 0,
    "account_level": "admin",
    "permissions": {
      "chat": true,
      "text": true,
      "links": true
    },
    "client": {
      "id": 2,
      "name": "Testing Client",
      "parent_id": 1
    }
  }
}
```

To obtain access, you must first have an active account, as well as a username/password provided.  Authentication is performed against the username/password for a given user account, and returns an access token to be used as a bearer token on all API requests.

API tokens have a rolling expiration, and if not used, will expire after two hours.

When used in requests, you'll want to set the Authorization header with each request.

`Authorization: Bearer ##YourAPITokenHere##`

<aside class="notice">
You must replace <code>##YourAPITokenHere##</code> with the provided API token on all API requests to any app specific endpoints.
</aside>






