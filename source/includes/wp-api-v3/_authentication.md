# Authentication #

JD Atina Web Services Microservices 1.0.0 includes two ways to authenticate.

## Login with JDE User Credentials ##

The HTTP method will be POST.

You must use the /login endpoint and pass the above parameters as a header and body.

#### Header parameters ####

|   Parameter    |  Type  |                                                                                  Description                                                                                  |
|----------------|--------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `Token`        | string | Set an empty token to login using JDE User Credential. <i class="label label-info">mandatory</i>                                                                                                                       |
| `TransactionId`| integer| Id used to get log inside JD Atina WS Microservices. <i class="label label-info">optional</i>. Use 0 to generate a transsaction ID inside JDE Atina Microservices                                                                       |

#### Body parameters ####

JDE HTML Client Credentials.

|   Parameter    |  Type  |                                                                                  Description                                                                                  |
|----------------|--------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `user`         | string  | JDE User <i class="label label-info">mandatory</i>                                                                                                                       |
| `password`     | string  | JDE Password <i class="label label-info">mandatory</i>               
| `environment`  | string  | JDE Environment <i class="label label-info">mandatory</i>               
| `role`		 | string  | JDE Role <i class="label label-info">mandatory</i>            


```cURL  
curl --location --request POST 'https://192.168.99.100/login' \
--header 'Token;' \
--header 'Accept: application/json' \
--header 'Content-Type: application/json' \
--header 'TransactionId: 0' \
--data-raw '{
   "user": "JDE",
   "environment": "JDV920",
   "password": "xxxxxxx",
   "role": "*ALL"
}
'
``` 
   
> Example of JSON received with the API Keys

```
{
    "addressBookNo": "1"
}
```

Address Book Number setup for the user.

#### Header parameters returned ####

|   Parameter    |  Type  |                                                                                  Description                                                                                  |
|----------------|--------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `Token`        | string | Token created                                                                                                            |
| `TransactionId`| integer| Transaction Id
| `SessionId`    | integer| JDE Id connection.
| `ChannelId`    | integer| Connection Id between Rest API and WS Microservice.


## Login with JD Atina Token ##

To login using token will require generate a token before invoke login API.

The administrator will need to generate a token using the following API.

The HTTP method will be POST.

You must use the /token/create endpoint and pass the above parameters as a header and body.

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
   "password": "xxxxxxx",
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


The next step is use this token created to login.

The HTTP method will be POST.

You must use the /login endpoint and pass the above parameters as a header and body.

#### Header parameters ####

|   Parameter    |  Type  |                                                                                  Description                                                                                  |
|----------------|--------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `Token`        | string | Set token created. <i class="label label-info">mandatory</i>                                                                                                                       |
| `TransactionId`| integer| Id used to get log inside JD Atina WS Microservices. <i class="label label-info">optional</i>. Use 0 to generate a transsaction ID inside JDE Atina Microservices                                                                       |

#### Body parameters ####

Use an empty body
      

```cURL  
curl --location --request POST 'https://192.168.99.100/login' \
--header 'Token: eyJhbGciOiJIUzI1NiJ9.exsdsIiOiJTdWJqZWN0IiwiaXNzIjoiSXNzdWUiLCJ1c2VyIjoiSkRdW52aXJvbm1lbnQiOiJKRFY5MjAiLCJyb2xlIjdlc3Npb25JZCI6MTkwOTg5MDEzOSwiZXhwIjoxNjM5NDA3ODczfQ.YuUXk1R60YIicZjfFp9W3px_4bIpIrHSvUIYqChSxOc' \
--header 'Accept: application/json' \
--header 'Content-Type: application/json' \
--header 'TransactionId: 0' \
--data-raw '{}
``` 
   
> Example of JSON received with the API Keys

```
{
    "addressBookNo": "1"
}
```

Address Book Number setup for the user.

#### Header parameters returned ####

|   Parameter    |  Type  |                                                                                  Description                                                                                  |
|----------------|--------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `Token`        | string | New Token created. It will be next token to use.                                                                                                           |
| `TransactionId`| integer| Transaction Id
| `SessionId`    | integer| JDE Id connection.
| `ChannelId`    | integer| Connection Id between Rest API and WS Microservice.

 
 
