# Token #

APIs to create and view tokens.

## Create Token ##
 
To login using token will require generate a token before invoke login API.
The administrator can use this API to generate a token.

### HTTP request ###

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-get">POST</i>
		<h6>/token/create</h6>
	</div>
</div>

#### Header parameters ####

|   Parameter    |  Type  |                                                                                  Description                                                                                  |
|----------------|--------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|                                                                                                                      |
| `TransactionId`| integer| Id used to get log inside JD Atina WS Microservices. <i class="label label-info">optional</i>. Use 0 to generate a transsaction ID inside JDE Atina Microservices                                                                       |

#### Body parameters ####

JDE HTML Client Credentials.

|   Parameter    |  Type  |                                                                                  Description                                                                                  |
|----------------|--------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `user`            | string  | JDE User <i class="label label-info">mandatory</i>                                                                                                                       |
| `password`        | string  | JDE Password <i class="label label-info">mandatory</i>               
| `environment`     | string  | JDE Environment <i class="label label-info">mandatory</i>               
| `role`            | string  | JDE Role <i class="label label-info">mandatory</i>          
| `tokenExpiration`	| integer | Token expiration in milliseconds <i class="label label-info">mandatory</i>   


```cURL
curl --location --request POST 'https://192.168.99.100/token/create' \
--header 'TransactionId: 0' \
--header 'Accept: application/json' \
--header 'Content-Type: application/json' \
--data-raw '{
   "user": "JDE",
   "environment": "JDV920",
   "password": "modus2020!",
   "role": "*ALL",
   "tokenExpiration": 480000
}
'
```

#### Header parameters returned ####

|   Parameter    |  Type  |                                                                                  Description                                                                                  |
|----------------|--------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `Token`        | string | Token created                                                                                                            |
| `TransactionId`| integer| Transaction Id
| `SessionId`    | integer| 0. There is not a JDE connection yet.
| `ChannelId`    | integer| Connection Id between Rest API and WS Microservice.

 
> JSON response will be empty:

```json

```
 
## Parse Token ##
 
This API allows to see token detail.

### HTTP request ###

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-get">POST</i>
		<h6>/monitor/logs</h6>
	</div>
</div>

#### Header parameters ####

|   Parameter    |  Type  |                                                                                  Description                                                                                  |
|----------------|--------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|                                                                                                                      |
| `Token`        | string | Token to parse.     
| `TransactionId`| integer| Id used to get log inside JD Atina WS Microservices. <i class="label label-info">optional</i>. Use 0 to generate a transsaction ID inside JDE Atina Microservices                                                                       |


```cURL
curl --location --request POST 'https://192.168.99.100/token/parse' \
--header 'Token: eyJhbGciOiJIUzI1NiJ9.eyJqdGkiOiIxMjMxMjMxIiwiaWF0IjoxNjM5NTA3Mzk0LCJzdWIiOiJTdWJqZWN0IiwiaXNzIjoiSXNzdWUiLCJ1c2VyIjoiSkRFIiwicGFzc3dvcmQiOiJtb2R1czIwMjAhIiwiZW52aXJvbm1lbnQiOiJKRFY5MjAiLCJyb2xlIjoiKkFMTCIsInNlc3Npb25JZCI6MCwiZXhwIjoxNjM5NTA3ODc0fQ.Ogs48EupSc2VMFfYp10lvbdtEjE5Qk6pte9x3KKZPio' \
--header 'Accept: application/json' \
--header 'Content-Type: application/json' \
--header 'Accept-Encoding: gzip, deflate, br' \
--header 'TransactionId: 0' \
--data-raw '{}
'
```

#### Header parameters returned ####

|   Parameter    |  Type  |                                                                                  Description                                                                                  |
|----------------|--------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `Token`        | string | Token updated                                                                                                            |
| `TransactionId`| integer| Transaction Id
| `SessionId`    | integer| 0. There is not a JDE connection yet.
| `ChannelId`    | integer| Connection Id between Rest API and WS Microservice.

 
> JSON response example:

```json
{
    "user": "JDEWS",
    "password": "No informed", 
    "environment": "JDV920",
    "role": "*ALL",
    "tokenExpiration": "14/12/2021 13:13:44",
    "sessionId": 248951487
}
```
 
 
 
 

