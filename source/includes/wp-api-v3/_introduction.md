# Introduction #

JD Atina Web Services Microservices 1.0.0 is fully integrated microservices to allow consume JDE Web Services in a simpe way.

Easy to install and easy to use.

JD ATINA Microservices is made up of a series of the following services:

* JD Atina Web Service Microservice
* JD Atina Rest-API Microservice 

We included additional connectors to allow third-party software to connect to JD Atina Web Service Microservice directly

* JD Atina Mule 3 CE Connector

For other third-party software the user can use a simple https connectors.

![JD Atina Services](images/atina_main.png)

We provide additional tools to allow:

* JD Atina Generate Configuration Files Tool.
* JD Atina Generate Jars Files Tool.
* JD Atina Test Connections Tool.

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
* Credentials management.
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


## Request/Response Format ##

The default response format is JSON. Requests with a message-body use plain JSON to set or update resource attributes. Successful requests will return a `200 OK` HTTP status.

Some general information about responses:

* Dates are returned in ISO8601 format: `YYYY-MM-DDTHH:MM:SS`
* Resource IDs are returned as integers.
* Any decimal monetary amount, such as prices or totals, will be returned as strings with two decimal places.
* Other amounts, such as item counts, are returned as integers.
* Blank fields are generally included as `null` or emtpy string instead of being omitted.


### Tools ###

Some useful tools you can use to access the API include:
 
- [Postman](https://www.getpostman.com/) - Cross-platform REST client, available for Mac, Windows, and Linux. 

