# Reports

## Get All Reports

```ruby
require 'uri'
require 'net/http'

url = URI("http://links.seebot.run/api/reports?domain_id=4")

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

$request->setRequestUrl('http://links.seebot.run/api/reports');
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
  --url 'http://links.seebot.run/api/reports?domain_id=4' \
  --header 'accept: application/json' \
  --header 'authorization: Bearer ##YourAPITokenHere##' \
  --header 'content-type: application/json'
```

```javascript
var request = require("request");

var options = {
  method: 'GET',
  url: 'http://links.seebot.run/api/reports',
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
      "id": 31,
      "name": "Testing Report",
      "type": "health_check_export",
      "parameters": {
        "date_end": "2020-02-13",
        "date_start": "2020-02-13"
      },
      "schedule": {
        "run_at": "2020-02-13 05:46:12",
        "recurring": false
      },
      "domain_id": 4,
      "status": "scheduled"
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

This endpoint retrieves all reports available to the client for the given domain. Status will indicate the current status of the report during processing, values include: scheduled, running, completed, error, inactive.

### HTTP Request

`GET https://links.seebot.run/api/reports`

### Query Parameters

Parameter                    | Required                | Default                    | Description
---------------------------- | ----------------------- | -------------------------- | ---------------------------------------------------------
domain_id                    | true                    | n/a                        | The Domain ID used to retrieve reports. Required to return reports.
page                         | false                   | 1                          | The current page of results to retrieve.
per_page                     | false                   | 25                         | The number of results to pull back. Allowed values: 25, 50, 100, -1 (for all)
sort                         | false                   | desc                       | The order for record sorting.
order                        | false                   | id                         | The field for sorting records. Allowed values: id, name, type, status


## Get a Report By ID

```ruby
require 'uri'
require 'net/http'

url = URI("http://links.seebot.run/api/reports/31")

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

$request->setRequestUrl('http://links.seebot.run/api/reports/31');
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
  --url http://links.seebot.run/api/reports/31 \
  --header 'accept: application/json' \
  --header 'authorization: Bearer ##YourAPITokenHere##' \
  --header 'content-type: application/json'
```

```javascript
var request = require("request");

var options = {
  method: 'GET',
  url: 'http://links.seebot.run/api/reports/31',
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
    "id": 31,
    "name": "Testing Report",
    "type": "health_check_export",
    "parameters": {
      "date_end": "2020-02-13",
      "date_start": "2020-02-13"
    },
    "schedule": {
      "run_at": "2020-02-13 05:46:12",
      "recurring": false
    },
    "domain_id": 4,
    "status": "scheduled"
  }
}
```

This endpoint retrieves a report owned by a client.

### HTTP Request

`GET http://links.seebot.run/api/reports/<ID>`

### URL Parameters

Parameter                    | Required                | Default                    | Description
---------------------------- | ----------------------- | -------------------------- | ---------------------------------------------------------
ID                           | true                    | n/a                        | The ID used to identify the report.


## Create a New Report

```ruby
require 'uri'
require 'net/http'

url = URI("http://links.seebot.run/api/reports")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Post.new(url)
request["accept"] = 'application/json'
request["content-type"] = 'application/json'
request["authorization"] = 'Bearer ##YourAPITokenHere##'
request.body = "{\n\t\"name\": \"Testing Report\",\n\t\"domain_id\": 4,\n\t\"type\": \"health_check_export\",\n\t\"parameters\": {\n\t\t\"date_start\": \"2020-02-13\",\n\t\t\"date_end\": \"2020-02-13\"\n\t}\n}"

response = http.request(request)
puts response.read_body
```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$body = new http\Message\Body;
$body->append('{
	"name": "Testing Report",
	"domain_id": 4,
	"type": "health_check_export",
	"parameters": {
		"date_start": "2020-02-13",
		"date_end": "2020-02-13"
	}
}');

$request->setRequestUrl('http://links.seebot.run/api/reports');
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
  --url http://links.seebot.run/api/reports \
  --header 'accept: application/json' \
  --header 'authorization: Bearer ##YourAPITokenHere##' \
  --header 'content-type: application/json' \
  --data '{
	"name": "Testing Report",
	"domain_id": 4,
	"type": "health_check_export",
	"parameters": {
		"date_start": "2020-02-13",
		"date_end": "2020-02-13"
	}
}'
```

```javascript
var request = require("request");

var options = {
  method: 'POST',
  url: 'http://links.seebot.run/api/reports',
  headers: {
    accept: 'application/json',
    'content-type': 'application/json',
    authorization: 'Bearer ##YourAPITokenHere##'
  },
  body: {
    name: 'Testing Report',
    domain_id: 4,
    type: 'health_check_export',
    parameters: {date_start: '2020-02-13', date_end: '2020-02-13'}
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
  "id": 31,
  "name": "Testing Report",
  "type": "health_check_export",
  "parameters": {
    "date_end": "2020-02-13",
    "date_start": "2020-02-13"
  },
  "schedule": {
    "run_at": "2020-02-13 05:46:12",
    "recurring": false
  },
  "domain_id": 4,
  "status": "scheduled"
}
```

This endpoint creates a new report and schedules it for processing.

### HTTP Request

`POST http://links.seebot.run/api/reports`

### Body Parameters

Parameter                    | Required                | Default                    | Description
---------------------------- | ----------------------- | -------------------------- | ---------------------------------------------------------
name                         | true                    | n/a                        | The name used to easily identify the report.
domain_id                    | true                    | n/a                        | The Domain ID the report will be associated with.
type                         | true                    | n/a                        | The type of report to be run. Allowed values: hit_miss_summary, browser_summary, os_summary, request_details_export, miss_details_export, health_check_export
parameters                   | true                    | {}                         | Object of parameters specific to each report.

### Report Parameters

Parameter                    | Type                    | Description
---------------------------- | ----------------------- | ---------------------------------------------------------
date_start                   | Date                    | Date to start pulling data from. Supported format: YYYY-MM-DD.
date_end                     | Date                    | Date to finish pulling data from. Supported format: YYYY-MM-DD.
group_by                     | String                  | Date range to group data by. Supported values: day, month, week, year.
link_ids                     | Array                   | Array of Link IDs to filter results by.

### Report Parameters By Type

Parameter                    | Hit/Miss Summary | Browser Summary | OS Summary | Request Details | Miss Details | Health Check
---------------------------- | ---------------- | --------------- | ---------- | --------------- | ------------ | ---------------
date_start                   | X                | X               | X          | X               | X            |
date_end                     | X                | X               | X          | X               | X            |
group_by                     | X                | X               | X          |                 |              |
link_ids                     | X                | X               | X          | X               |              |



## Delete a Specific Report

```ruby
require 'uri'
require 'net/http'

url = URI("http://links.seebot.run/api/reports/31")

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

$request->setRequestUrl('http://links.seebot.run/api/reports/31');
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
  --url http://links.seebot.run/api/reports/31 \
  --header 'accept: application/json' \
  --header 'authorization: Bearer ##YourAPITokenHere##'
```

```javascript
var request = require("request");

var options = {
  method: 'DELETE',
  url: 'http://links.seebot.run/api/reports/31',
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

This endpoint deletes a report.

### HTTP Request

`DELETE http://links.seebot.run/api/reports/<ID>`

### URL Parameters

Parameter                    | Required                | Default                    | Description
---------------------------- | ----------------------- | -------------------------- | ---------------------------------------------------------
ID                           | true                    | n/a                        | The ID used to identify the report.

