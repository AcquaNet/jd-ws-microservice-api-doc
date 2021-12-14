# Metadata #

Metadata APIs provide information about all available web services on the microservice.

## Operations ##
 
This API lets you retrieve and view a simple list of available web services endpoints.

### HTTP request ###

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-get">GET</i>
		<h6>/metadata/operations</h6>
	</div>
</div>

```cURL
curl --location --request GET 'https://192.168.99.100/metadata/operations' \
--header 'Token: eyJhbGciOiJIUzI1NiJ9.eyJqdGkiOiIxMjMxMjMxIiwiaWF0IjoxNjM5NDkyOTM1LCJzdWIiOiJTdWJqZWN0IiwiaXNzIjoiSXNzdWUiLCJ1c2VyIjoiSkRFIiwicGFzc3dvcmQiOiJtb2R1czIwMjAhIiwiZW52aXJvbm1lbnQiOiJKRFY5MjAiLCJyb2xlIjoiKkFMTCIsInNlc3Npb25JZCI6MjQ4OTUxNDg3LCJleHAiOjE2Mzk0OTU5MzV9.Wt2G9jT4L9ut5gZUc3FlHrXohVW5abNvCpvx3pDqQPs' \
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
    "oracle.e1.bssv.JPR01020.RI_CustomerManager.getCustomerCreditInfo",
    "oracle.e1.bssv.JP000040.FinancialComplianceManager.getAgingCompanyConstants",
    "oracle.e1.bssv.JP420000.SalesOrderManager.getSalesOrder",
    "oracle.e1.bssv.JP410000.InventoryManager.getCalculatedAvailability",
...
    "oracle.e1.bssv.JP080020.EmployeeManager.processPendingEmployee"
]
```

## Get Input Parameters for a Web Service##
 
This API lets you retrieve parameters required by the web services including the type.

### HTTP request ###

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-get">GET</i>
		<h6>/metadata/parameters-input/<web-service></h6>
	</div>
</div>

```cURL
curl --location --request GET 'https://192.168.99.100/metadata/parameters-input/oracle.e1.bssv.JP010000.AddressBookManager.getAddressBook' \
--header 'Token: eyJhbGciOiJIUzI1NiJ9.eyJqdGkiOiIxMjMxMjMxIiwiaWF0IjoxNjM5NDkzMjc2LCJzdWIiOiJTdWJqZWN0IiwiaXNzIjoiSXNzdWUiLCJ1c2VyIjoiSkRFIiwicGFzc3dvcmQiOiJtb2R1czIwMjAhIiwiZW52aXJvbm1lbnQiOiJKRFY5MjAiLCJyb2xlIjoiKkFMTCIsInNlc3Npb25JZCI6MjQ4OTUxNDg3LCJleHAiOjE2Mzk0OTYyNzZ9.aWmIwz0S3jtcOna_YawvUSKNjT1ZRg6-cB40iymiCF8' \
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
    "businessUnit: <java.lang.String>",
    "address: <oracle.e1.bssv.JP010000.valueobject.GetAddress>",
    ".countyCode: <java.lang.String>",
    ".countryCode: <java.lang.String>",
    ".postalCode: <java.lang.String>",
    ".stateCode: <java.lang.String>",
    "categoryCodesAddressBook: <oracle.e1.bssv.JP010000.valueobject.CategoryCodesAddressBook>",
    ".categoryCode013: <java.lang.String>",
    ".categoryCode012: <java.lang.String>",
    ".categoryCode011: <java.lang.String>",
    ".categoryCode010: <java.lang.String>",
    ".categoryCode030: <java.lang.String>",
    ".categoryCode019: <java.lang.String>",
    ".categoryCode018: <java.lang.String>",
    ".categoryCode017: <java.lang.String>",
    ".categoryCode016: <java.lang.String>",
    ".categoryCode015: <java.lang.String>",
    ".categoryCode014: <java.lang.String>",
    ".categoryCode002: <java.lang.String>",
    ".categoryCode024: <java.lang.String>",
    ".categoryCode001: <java.lang.String>",
    ".categoryCode023: <java.lang.String>",
    ".categoryCode022: <java.lang.String>",
    ".categoryCode021: <java.lang.String>",
    ".categoryCode020: <java.lang.String>",
    ".categoryCode009: <java.lang.String>",
    ".categoryCode008: <java.lang.String>",
    ".categoryCode007: <java.lang.String>",
    ".categoryCode029: <java.lang.String>",
    ".categoryCode006: <java.lang.String>",
    ".categoryCode028: <java.lang.String>",
    ".categoryCode005: <java.lang.String>",
    ".categoryCode027: <java.lang.String>",
    ".categoryCode004: <java.lang.String>",
    ".categoryCode026: <java.lang.String>",
    ".categoryCode003: <java.lang.String>",
    ".categoryCode025: <java.lang.String>",
    "entityName: <java.lang.String>",
    "entityTypeCode: <java.lang.String>",
    "languageCode: <java.lang.String>",
    "industryClassificationCode: <java.lang.String>",
    "entity: <oracle.e1.bssv.util.J0100010.valueobject.Entity>",
    ".entityTaxId: <java.lang.String>",
    ".entityLongId: <java.lang.String>",
    ".entityId: <java.lang.Integer>"
]
```

## Get Output Parameters for a Web Service##
 
This API lets you retrieve parameters required by the web services including the type.

### HTTP request ###

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-get">GET</i>
		<h6>/metadata/parameters-output/<web-service></h6>
	</div>
</div>

```cURL
curl --location --request GET 'https://192.168.99.100/metadata/parameters-output/oracle.e1.bssv.JP420000.SalesOrderManager.getItemListPrice' \
--header 'Token: eyJhbGciOiJIUzI1NiJ9.eyJqdGkiOiIxMjMxMjMxIiwiaWF0IjoxNjM5NDkzNjE4LCJzdWIiOiJTdWJqZWN0IiwiaXNzIjoiSXNzdWUiLCJ1c2VyIjoiSkRFIiwicGFzc3dvcmQiOiJtb2R1czIwMjAhIiwiZW52aXJvbm1lbnQiOiJKRFY5MjAiLCJyb2xlIjoiKkFMTCIsInNlc3Npb25JZCI6MjQ4OTUxNDg3LCJleHAiOjE2Mzk0OTY2MTh9.2i1lLAPWarArD3oU5WINydpMMGkeRorOBhI-URJkw8c' \
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
    "e1MessageList: <oracle.e1.bssvfoundation.util.E1MessageList>",
    ".messagesAsString: <java.lang.String>",
    ".E1Messages: List <oracle.e1.bssvfoundation.util.E1Message>",
    "..messageType: <java.lang.Integer>",
    "..callObjError: <com.jdedwards.system.kernel.CallObjectErrorItem>",
    "...fileName: <java.lang.String>",
    "...dditem: <java.lang.String>",
    "...alphaDescription: <java.lang.String>",
    "...errorId: <java.lang.Integer>",
    "...errorID: <java.lang.Integer>",
    "...lineNumber: <java.lang.Integer>",
    "...glossaryText: <java.lang.String>",
    "...subText: <java.lang.String>",
    "...errorLevel: <java.lang.Integer>",
    "..messagePrefix: <java.lang.String>",
    "..message: <java.lang.String>",
    "showItemListPrice: List <oracle.e1.bssv.JP420000.valueobject.ItemListPriceRecord>",
    ".lotGrade: <java.lang.String>",
    ".location: <java.lang.String>",
    ".lotNumber: <java.lang.String>",
    ".lotPotency: <java.math.BigDecimal>",
    ".priceList: <java.math.BigDecimal>"
]
```

## Get Payload Input for a Web Service##
 
This API lets you retrieve a template to use as a payload to invoke a web service.

### HTTP request ###

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-get">GET</i>
		<h6>/metadata/payload-input/<web-service></h6>
	</div>
</div>

```cURL
curl --location --request GET 'https://192.168.99.100/metadata/payload-input/oracle.e1.bssv.JP010000.AddressBookManager.getAddressBook' \
--header 'Token: eyJhbGciOiJIUzI1NiJ9.eyJqdGkiOiIxMjMxMjMxIiwiaWF0IjoxNjM5NDkzNjE4LCJzdWIiOiJTdWJqZWN0IiwiaXNzIjoiSXNzdWUiLCJ1c2VyIjoiSkRFIiwicGFzc3dvcmQiOiJtb2R1czIwMjAhIiwiZW52aXJvbm1lbnQiOiJKRFY5MjAiLCJyb2xlIjoiKkFMTCIsInNlc3Npb25JZCI6MjQ4OTUxNDg3LCJleHAiOjE2Mzk0OTY2MTh9.2i1lLAPWarArD3oU5WINydpMMGkeRorOBhI-URJkw8c' \
--header 'Accept: application/json' \
--header 'Content-Type: application/json' \
--header 'Accept-Encoding: gzip, deflate, br' \
--header 'TransactionId: 0' \
--data-raw '{}
'
```
 
> JSON response example:

```json
{
    "businessUnit": "java.lang.String",
    "address": {
        "countyCode": "java.lang.String",
        "countryCode": "java.lang.String",
        "postalCode": "java.lang.String",
        "stateCode": "java.lang.String"
    },
    "categoryCodesAddressBook": {
        "categoryCode013": "java.lang.String",
        "categoryCode012": "java.lang.String",
        "categoryCode011": "java.lang.String",
        "categoryCode010": "java.lang.String",
        "categoryCode030": "java.lang.String",
        "categoryCode019": "java.lang.String",
        "categoryCode018": "java.lang.String",
        "categoryCode017": "java.lang.String",
        "categoryCode016": "java.lang.String",
        "categoryCode015": "java.lang.String",
        "categoryCode014": "java.lang.String",
        "categoryCode002": "java.lang.String",
        "categoryCode024": "java.lang.String",
        "categoryCode001": "java.lang.String",
        "categoryCode023": "java.lang.String",
        "categoryCode022": "java.lang.String",
        "categoryCode021": "java.lang.String",
        "categoryCode020": "java.lang.String",
        "categoryCode009": "java.lang.String",
        "categoryCode008": "java.lang.String",
        "categoryCode007": "java.lang.String",
        "categoryCode029": "java.lang.String",
        "categoryCode006": "java.lang.String",
        "categoryCode028": "java.lang.String",
        "categoryCode005": "java.lang.String",
        "categoryCode027": "java.lang.String",
        "categoryCode004": "java.lang.String",
        "categoryCode026": "java.lang.String",
        "categoryCode003": "java.lang.String",
        "categoryCode025": "java.lang.String"
    },
    "entityName": "java.lang.String",
    "entityTypeCode": "java.lang.String",
    "languageCode": "java.lang.String",
    "industryClassificationCode": "java.lang.String",
    "entity": {
        "entityTaxId": "java.lang.String",
        "entityLongId": "java.lang.String",
        "entityId": "java.lang.Integer"
    }
}
```

## Get Payload Output for a Web Service##
 
This API lets you retrieve a sample response returned by a web service.

### HTTP request ###

<div class="api-endpoint">
	<div class="endpoint-data">
		<i class="label label-get">GET</i>
		<h6>/metadata/payload-output/<web-service></h6>
	</div>
</div>

```cURL
curl --location --request GET 'https://192.168.99.100/metadata/payload-output/oracle.e1.bssv.JP420000.SalesOrderManager.getItemListPrice' \
--header 'Token: eyJhbGciOiJIUzI1NiJ9.eyJqdGkiOiIxMjMxMjMxIiwiaWF0IjoxNjM5NDkzOTA0LCJzdWIiOiJTdWJqZWN0IiwiaXNzIjoiSXNzdWUiLCJ1c2VyIjoiSkRFIiwicGFzc3dvcmQiOiJtb2R1czIwMjAhIiwiZW52aXJvbm1lbnQiOiJKRFY5MjAiLCJyb2xlIjoiKkFMTCIsInNlc3Npb25JZCI6MjQ4OTUxNDg3LCJleHAiOjE2Mzk0OTY5MDR9.yiih3zb2CbPZyg42VP8BE5oEhZbz43tm6CqxGw3vhiM' \
--header 'Accept: application/json' \
--header 'Content-Type: application/json' \
--header 'Accept-Encoding: gzip, deflate, br' \
--header 'TransactionId: 0' \
--data-raw '{}
'
```
 
> JSON response example:

```json
{
    "e1MessageList": {
        "messagesAsString": "java.lang.String",
        "E1Messages": [
            {
                "messageType": "java.lang.Integer",
                "callObjError": {
                    "fileName": "java.lang.String",
                    "dditem": "java.lang.String",
                    "alphaDescription": "java.lang.String",
                    "errorId": "java.lang.Integer",
                    "errorID": "java.lang.Integer",
                    "lineNumber": "java.lang.Integer",
                    "glossaryText": "java.lang.String",
                    "subText": "java.lang.String",
                    "errorLevel": "java.lang.Integer"
                },
                "messagePrefix": "java.lang.String",
                "message": "java.lang.String"
            }
        ]
    },
    "showItemListPrice": [
        {
            "lotGrade": "java.lang.String",
            "location": "java.lang.String",
            "lotNumber": "java.lang.String",
            "lotPotency": "java.math.BigDecimal",
            "priceList": "java.math.BigDecimal"
        }
    ]
}
```

