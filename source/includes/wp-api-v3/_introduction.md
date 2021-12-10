# Introduction #

JD Atina Web Services Microservices 1.0.0 is fully integrated with the WordPress [REST](http://en.wikipedia.org/wiki/Representational_State_Transfer) API. This allows WC data to be created, read, updated, and deleted using requests in JSON format and using WordPress REST API Authentication methods and standard HTTP verbs which are understood by most HTTP clients.

JD ATINA Microservices is made up of a series of the following services:

* JD Atina Web Service Microservice
* JD Atina Rest-API Microservice 

We included additional connectors to allow third-party software to connect to JD Atina Web Service Microservice directly

* JD Atina Mule 3 CE Connector

For other third-party software the user can use a simple https connectors.

![JD Atina Services(images/atina_main.png)

We provide additional tools to allow:

* JD Atina Generate Configuration Files.
* Generate Jars Files Tools.
* Test Connections Tool.

![JD Atina settings](images/atina_tools.png)


The current JD Atina REST WS API integration version is `v1`

The following table shows API versions present in each major version of JD Atina Web Services Microservices:

| API Version | JD Atina WS Microservices Version     | Documentation             |
|-------------|---------------------------------------|---------------------------|
| `v1`        | 1.0.0                                 | -                         |


## JD ATINA Web Service Microservice ##

It's a simple Microservice used to consume JDE Web Services directly to Enterprise Service Logic instead use JDE Applications Server.

It allows third party sofware to connect to JDE Web Services to share logic and data.

It provides:

* Access to JDE Web Services.
* Session management.
* Connection pooling.
* Metadata introspection


![JD Atina WS Microservices](images/atina_ws_microservices.png)

JD ATINA Web Service Microservice is deployed with dockers.

![JD Atina WS Microservices Arquitecture](images/atina_ws_aquitecture.png)

## JD ATINA Rest API Microservice ##

It's a simple Microservice used to epose JDE Web Services as Rest API.

Any third party sofware with HTTP Connector can consume JDE Web Services with json data.

![JD Atina Rest Api Microservices](images/atina_rest-api.png)

## JD Atina Mule 3 CE Connector ##

It's a Mule CE connector to consume Web Service from Mulesoft Applications.

![JD Atina Rest Api Microservices](images/atina_mule_3_connector.png)

Mule 4 is in development.

## Implementations ##

The following implementation steps need to be performed before working with JD Web Service Microservice:

* Set up a configuration

* Start JD Web Services Microservice / JDE Rest API Microservice

* Install Mulesoft JDE WS Community Edition Connector 3.


## Requirements to consume Web Services using JD Atina WS Microservices ##

To use the latest version of the JD Atina REST WS API you will need:

* JD Atina Web Services Microservices 1.0.0+ running.
* Oracle JD Edwards EnterpriseOne HTML Client credential: User, Pasword, Environment and Role.
* You may access the API over either HTTP or HTTPS, but *HTTPS is recommended where possible*.


## Requirements to install JD Atina WS Microservices ##

* Oracle JD Edwards EnterpriseOne Server Manager credential: jde admin user, Pasword and url for Server Manager Ex. http://server:8999/manage/

* Following folder inside JDE Deployment Server:

| Folder                      | Comment                                                    |
|-----------------------------|-------------------------------------------------------------|
| `//Deplo/E920/MISC`                                               | JDBC Drivers          |
| `//Deplo/E920/system/Classes`                                     | JDE jars files        |
| `//Deplo/E920/system/JAS/webclient.ear/webclient.war/WEB-INF/lib` | JDE Client HTTP       |
| `//Deplo/E920/DV920/java/sbfjars`                                 | JDE WS                |


* [Docker](  https://docs.docker.com/get-docker/ "Docker"). JD Atina Web Service Microserver run under Docker container.

## Addionals Prerequisites to use JD Generate Configuration Files and JD Generate Jars Files Tools ##

* JDK 8 installed with JAVA_HOME configured appropriately (It not requires for docker version)

* Apache Maven 3.8.1+

> ![Tip](images/note-icon.png) 
    Verify Maven is using the Java you expect
    If you have multiple JDK’s installed it is not certain Maven will pick up the expected java and you could end up with unexpected results. 
    You can verify which JDK Maven uses by running mvn --version.


## Request/Response Format ##

The default response format is JSON. Requests with a message-body use plain JSON to set or update resource attributes. Successful requests will return a `200 OK` HTTP status.

Some general information about responses:

* Dates are returned in ISO8601 format: `YYYY-MM-DDTHH:MM:SS`
* Resource IDs are returned as integers.
* Any decimal monetary amount, such as prices or totals, will be returned as strings with two decimal places.
* Other amounts, such as item counts, are returned as integers.
* Blank fields are generally included as `null` or emtpy string instead of being omitted.

### JSONP Support ###

The JD Atina REST WS API supports JSONP by default. JSONP responses use the `application/javascript` content-type. You can specify the callback using the `?_jsonp` parameter for `GET` requests to have the response wrapped in a JSON function:

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-get">GET</i>
		<h6>/wp-json/wc/v3?_jsonp=callback</h6>
	</div>
</div>

```shell
curl https://example.com/wp-json/wc/v3/products/tags/34?_jsonp=tagDetails \
	-u consumer_key:consumer_secret
```

```javascript
JD Atina Web Services Microservices.get("products/tags/34?_jsonp=tagDetails")
  .then((response) => {
    console.log(response.data);
  })
  .catch((error) => {
    console.log(error.response.data);
  });
```

```php
<?php print_r($woocommerce->get('products/tags/34', ['_jsonp' => 'tagDetails'])); ?>
```

```python
print(wcapi.get("products/tags/34?_jsonp=tagDetails").json())
```

```ruby
woocommerce.get("products/tags/34", _jsonp: "tagDetails").parsed_response
```

> Response:

```
/**/tagDetails({"id":34,"name":"Leather Shoes","slug":"leather-shoes","description":"","count":0,"_links":{"self":[{"href":"https://example.com/wp-json/wc/v3/products/tags/34"}],"collection":[{"href":"https://example.com/wp-json/wc/v3/products/tags"}]}})%
```

## Errors ##

Occasionally you might encounter errors when accessing the REST API. There are four possible types:

| Error Code                  | Error Type                                                  |
|-----------------------------|-------------------------------------------------------------|
| `400 Bad Request`           | Invalid request, e.g. using an unsupported HTTP method      |
| `401 Unauthorized`          | Authentication or permission error, e.g. incorrect API keys |
| `404 Not Found`             | Requests to resources that don't exist or are missing       |
| `500 Internal Server Error` | Server error                                                |

> JD Atina REST WS API error example:

```json
{
  "code": "rest_no_route",
  "message": "No route was found matching the URL and request method",
  "data": {
    "status": 404
  }
}
```

> JD Atina REST Web Services API error example:

```json
{
  "code": "woocommerce_rest_term_invalid",
  "message": "Resource doesn't exist.",
  "data": {
    "status": 404
  }
}
```

Errors return both an appropriate HTTP status code and response object which contains a `code`, `message` and `data` attribute.

## Parameters ##

Almost all endpoints accept optional parameters which can be passed as a HTTP query string parameter, e.g. `GET /orders?status=completed`. All parameters are documented along each endpoint.

## Pagination ##

Requests that return multiple items will be paginated to 10 items by default. This default can be changed by the site administrator by changing the `posts_per_page` option. Alternatively the items per page can be specified with the `?per_page` parameter:

`GET /orders?per_page=15`

You can specify further pages with the `?page` parameter:

`GET /orders?page=2`

You may also specify the offset from the first resource using the `?offset` parameter:

`GET /orders?offset=5`

Page number is 1-based and omitting the `?page` parameter will return the first page.

The total number of resources and pages are always included in the `X-WP-Total` and `X-WP-TotalPages` HTTP headers.

### Link Header ###

Pagination info is included in the [Link Header](http://tools.ietf.org/html/rfc5988). It's recommended that you follow these values instead of building your own URLs where possible.

```
Link: <https://www.example.com/wp-json/wc/v3/products?page=2>; rel="next",
<https://www.example.com/wp-json/wc/v3/products?page=3>; rel="last"`
```

The possible `rel` values are:

|  Value  |                       Description                        |
|---------|----------------------------------------------------------|
| `next`  | Shows the URL of the immediate next page of results.     |
| `last`  | Shows the URL of the last page of results.               |
| `first` | Shows the URL of the first page of results.              |
| `prev`  | Shows the URL of the immediate previous page of results. |

## Libraries and Tools ##

### Official libraries ###

- [JavaScript](https://www.npmjs.com/package/@woocommerce/woocommerce-rest-api) Library
- [PHP](https://packagist.org/packages/automattic/woocommerce) Library
- [Python](https://pypi.python.org/pypi/JD Atina Web Services Microservices) Library
- [Ruby](https://rubygems.org/gems/woocommerce_api) Library

```javascript
// Install:
// npm install --save @woocommerce/woocommerce-rest-api

// Setup:
const JD Atina Web Services MicroservicesRestApi = require("@woocommerce/woocommerce-rest-api").default;
// import JD Atina Web Services MicroservicesRestApi from "@woocommerce/woocommerce-rest-api"; // Supports ESM

const JD Atina Web Services Microservices = new JD Atina Web Services MicroservicesRestApi({
  url: 'http://example.com', // Your store URL
  consumerKey: 'consumer_key', // Your consumer key
  consumerSecret: 'consumer_secret', // Your consumer secret
  version: 'wc/v3' // JD Atina Web Services Microservices JD Atina REST WS API version
});
```

```php
<?php
// Install:
// composer require automattic/woocommerce

// Setup:
require __DIR__ . '/vendor/autoload.php';

use Automattic\JD Atina Web Services Microservices\Client;

$woocommerce = new Client(
    'http://example.com', // Your store URL
    'consumer_key', // Your consumer key
    'consumer_secret', // Your consumer secret
    [
        'wp_api' => true, // Enable the JD Atina REST WS API integration
        'version' => 'wc/v3' // JD Atina Web Services Microservices JD Atina REST WS API version
    ]
);
?>
```

```python
# Install:
# pip install woocommerce

# Setup:
from woocommerce import API

wcapi = API(
    url="http://example.com", # Your store URL
    consumer_key="consumer_key", # Your consumer key
    consumer_secret="consumer_secret", # Your consumer secret
    wp_api=True, # Enable the JD Atina REST WS API integration
    version="wc/v3" # JD Atina Web Services Microservices JD Atina REST WS API version
)
```

```ruby
# Install:
# gem install woocommerce_api

# Setup:
require "woocommerce_api"

woocommerce = JD Atina Web Services Microservices::API.new(
  "https://example.com", # Your store URL
  "consumer_key", # Your consumer key
  "consumer_secret", # Your consumer secret
  {
    wp_api: true, # Enable the JD Atina REST WS API integration
    version: "wc/v3" # JD Atina Web Services Microservices JD Atina REST WS API version
  }
)
```

<aside class="notice">
	Use the tabs in the top-right corner of this page to see how to install and use each library.
</aside>

### Third party libraries ###

- [Java](https://github.com/icoderman/wc-api-java) Library
- [.NET](https://github.com/XiaoFaye/JD Atina Web Services Microservices.NET) Library
- [Android](https://github.com/gilokimu/WooDroid) Library

<aside class="notice">
	Note that we don't offer support for third party libraries, so if you have questions about how use any of this libraries you should contact the respective authors.
</aside>

### Tools ###

Some useful tools you can use to access the API include:

- [Insomnia](https://insomnia.rest) - Cross-platform GraphQL and REST client, available for Mac, Windows, and Linux.
- [Postman](https://www.getpostman.com/) - Cross-platform REST client, available for Mac, Windows, and Linux.
- [RequestBin](https://requestbin.com) - Allows you test webhooks.
- [Hookbin](https://hookbin.com/) - Another tool to test webhooks.

## Learn more ##

Learn more about the REST API checking the <a href="https://developer.wordpress.org/rest-api/">official WordPress REST API documentation</a>.
