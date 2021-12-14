# Operation #

APIs to create and view tokens.

## Invoke Web Service ##
 
Use this API to invoke Web Services.

### HTTP request ###

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-get">POST</i>
		<h6>/operation/invoke/<web-service></h6>
	</div>
</div>

#### Header parameters ####

|   Parameter    |  Type  |                                                                                  Description                                                                                  |
|----------------|--------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|                                                                                                                      |
| `Token`        | string | Last Token returned last API invoked <i class="label label-info">mandatory</i>     
| `TransactionId`| integer| Id used to get log inside JD Atina WS Microservices. <i class="label label-info">optional</i>. Use 0 to generate a transsaction ID inside JDE Atina Microservices                                                                       |

#### Body parameters ####

Web Service Payload. Use API 

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-get">GET</i>
		<h6>/metadata/payload-input/<web-service></h6>
	</div>
</div>


```cURL
curl --location --request POST 'https://192.168.99.100/operation/invoke/oracle.e1.bssv.JP410000.InventoryManager.getItemPrice' \
--header 'Token: eyJhbGciOiJIUzI1NiJ9.eyJqdGkiOiIxMjMxMjMxIiwiaWF0IjoxNjM5NTA3Mzk0LCJzdWIiOiJTdWJqZWN0IiwiaXNzIjoiSXNzdWUiLCJ1c2VyIjoiSkRFIiwicGFzc3dvcmQiOiJtb2R1czIwMjAhIiwiZW52aXJvbm1lbnQiOiJKRFY5MjAiLCJyb2xlIjoiKkFMTCIsInNlc3Npb25JZCI6MCwiZXhwIjoxNjM5NTA3ODc0fQ.Ogs48EupSc2VMFfYp10lvbdtEjE5Qk6pte9x3KKZPio' \
--header 'Accept: application/json' \
--header 'Content-Type: application/json' \
--header 'Accept-Encoding: gzip, deflate, br' \
--header 'TransactionId: 0' \
--data-raw '{
    "item": {
        "itemId": 60003,
        "itemUOMSecondary": "",
        "itemProduct": "",
        "itemCustomer": "",
        "itemCatalog": "",
        "itemDescription": "",
        "itemFreeForm": "",
        "itemUOMPrimary": ""
    },
    "branchPlantList": "          10"
    }'
```

#### Header parameters returned ####

|   Parameter    |  Type  |                                                                                  Description                                                                                  |
|----------------|--------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `Token`        | string | Token renewed to use for next request.                                                                                                            |
| `TransactionId`| integer| Transaction Id
| `SessionId`    | integer| JDE connection Id.
| `ChannelId`    | integer| Connection Id between Rest API and WS Microservice.

 
> JSON response will be related to Web Service invoked:

```json
{}
```

