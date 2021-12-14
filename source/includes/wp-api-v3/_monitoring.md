# Monitoring #

Monitoring APIs provide information about microservice.

## Connections Open ##
 
This API lets you retrieve and view a simple list of all user connected.

### HTTP request ###

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-get">GET</i>
		<h6>/monitor/connections</h6>
	</div>
</div>

```cURL
curl --location --request GET 'https://192.168.99.100/monitor/connections' \
--header 'Accept: application/json' \
--header 'Content-Type: application/json' \
--header 'Accept-Encoding: gzip, deflate, br' \
--header 'TransactionId: 0' \
--data-raw '{}
'
```
 
> JSON response example:

```json
[
{
        "Role": "*ALL",
        "Active": true,
        "User": "JDE",
        "Environment": "JDV920",
        "Tmp-Cache": "/tmp/jde/JDV920",
        "Tmp-Folder": "/tmp/jde",
        "Session": "421083912"
    }
]
```
 
## Logs ##
 
This API lets you retrieve logs giving a transaction Id.

### HTTP request ###

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-get">GET</i>
		<h6>/monitor/logs</h6>
	</div>
</div>

```cURL
curl --location --request GET 'https://192.168.99.100/monitor/logs' \
--header 'Accept: text/plain' \
--header 'Accept-Encoding: gzip, deflate, br' \
--header 'TransactionId: 20211214152930577' \
--header 'Content-Type: application/json' \
--data-raw '{}
'
```
 
> JSON response example:

```txt
12:24:41.714 [grpc-default-executor-11] INFO  c.acqua.jde.jdeconnectorserver.JDEConnectorServer - BEGIN TID: 20211214152441694======================================================================================
12:24:41.714 [grpc-default-executor-11] INFO  c.acqua.jde.jdeconnectorserver.JDEConnectorServer - JDE ATINA Connection Pool
12:24:41.714 [grpc-default-executor-11] DEBUG c.a.a.j.wsservice.JDESingleWSClient - ATINA - JDEConnectorService:  Is Connected to JDE?:false
12:24:41.715 [grpc-default-executor-11] DEBUG c.a.a.j.wsservice.JDESingleWSClient - ATINA - JDEConnectorService:  Is Connected to JDE?:false
12:24:41.715 [grpc-default-executor-11] DEBUG c.a.a.j.wsservice.JDESingleWSClient - ATINA - JDEConnectorService:  Is Connected to JDE?:false
12:24:41.736 [grpc-default-executor-11] INFO  c.acqua.jde.jdeconnectorserver.JDEConnectorServer - -------------------------------------------------------------------------------
12:24:49.409 [grpc-default-executor-11] INFO  c.acqua.jde.jdeconnectorserver.JDEConnectorServer - Starting LoggerUtil...
12:24:49.412 [grpc-default-executor-11] INFO  c.acqua.jde.jdeconnectorserver.JDEConnectorServer - Starting LoggerUtil Filter:jde_atina_server_2021-12-14
12:24:49.424 [grpc-default-executor-11] INFO  c.acqua.jde.jdeconnectorserver.JDEConnectorServer - Starting LoggerUtil Reading:jde_atina_server_2021-12-14.0.log
12:24:49.505 [grpc-default-executor-11] INFO  c.acqua.jde.jdeconnectorserver.JDEConnectorServer - Starting LoggerUtil Thread:grpc-default-executor-11 Line: 12:24:41.714 [grpc-default-executor-11] INFO  c.acqua.jde.jdeconnectorserver.JDEConnectorServer - 99999999999999999======================================================================================

```
 
 
 
 

