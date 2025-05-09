---
title: API Reference

language_tabs: # must be one of https://github.com/rouge-ruby/rouge/wiki/List-of-supported-languages-and-lexers
  - shell

toc_footers:
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true

code_clipboard: true

meta:
  - name: description
    content: Documentation for easycancha API
---

# Introduction

Welcome to easycancha API! You can use our API to access easycancha API endpoints, which can get information on bookings, customers and other resources in our database.

We have language bindings in Shell! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

This example API documentation page was created with [Slate](https://github.com/slatedocs/slate). Feel free to edit it and use it as a base for your own API's documentation.

# Authentication

> To authorize, use this code:

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here" \
  -H "apikey: customerrandomapikey"
```

> Make sure to replace `customerrandomapikey` with your API key.

easycancha uses API keys to allow access to the API. You can request a new API key to contacto@easycancha.com.

easycancha expects for the API key to be included in all API requests to the server in a header that looks like the following:

`apikey: customerrandomapikey`

<aside class="notice">
You must replace <code>customerrandomapikey</code> with your personal API key.
</aside>

# Users

<aside class="success">
Context - These services apply to a specific club, which will be also informed at the moment of enabled the API, and will be part of the api URL (CLUBID Parameter)
</aside>


## Get All Users

```shell
curl "https://www.easycancha.com/api/clubs/<CLUBID>/usersReport" \
  -H "apikey: customerrandomapikey"
```

> The above command returns JSON structured like this:

```json
{
    "error": false,
    "code": 0,
    "users": [
        {
            "userId": 66,
            "firstName": "Roberto",
            "lastName": "de Campos Wichrowski",
            "email": "roberto.decampos@easycancha.com",
            "phone": "+56996666332",
            "birthDate": "1979-09-09",
            "age": 45,
            "gender": "M",
            "foidCountry": "CL",
            "foidType": "NI",
            "foidNumber": "14543789K",
            "emailConfirmed": true,
            "webEnrolledDate": "2016-10-07",
            "memberId": null,
            "blocked": false,
            "comments": "Este cliente es muy responsable."
        },
        {
            "userId": 597410,
            "firstName": "Patricio",
            "lastName": "Cordero",
            "email": "patricio.cordero@easycancha.com",
            "phone": "+56976633559",
            "birthDate": "1982-11-16",
            "age": 42,
            "gender": "M",
            "foidCountry": "CL",
            "foidType": "NI",
            "foidNumber": "154455671",
            "emailConfirmed": true,
            "webEnrolledDate": "2022-12-22",
            "memberId": null,
            "blocked": false,
            "comments": null
        }
    ]
}
```

This endpoint retrieves all users for a specific club.

### HTTP Request

`GET https://www.easycancha.com/api/clubs/<CLUBID>/usersReport`

### URL Parameters

Parameter | Description
--------- | -----------
CLUBID | Club identifier

### Object User description

Field | Type | Description
--------- | ----------- | -----------
userId | integer | Unique user identifier
firstName | string | user first name
lastName | string | user last name
email | string | user email
phone | string | user phone in international format + and numbers (ie. +56977087296)
birthDate | string | user birth date in YYYY-MM-DD format
age | integer | user age
gender | string | user gender M for Male or F for Female
foidCountry | string | user document country ISO 3166-1 alpha-2
foidType | string | user document type, NI for Identification Number, PP for passport, and could be others depending on the country
foidNumber | string | user document number
emailConfirmed | boolean | indicator if the user has confirmed his email
webEnrolledDate | string | date that the user has enrolled in the app / web in YYYY-MM-DD format
memberId | string | user member Id
blocked | boolean | indicator if the user is blocked for this club
comments | string | comments associated with the user

# Transactions

<aside class="success">
Context - These services apply to a specific club, which will be also informed at the moment of enabled the API, and will be part of the api URL (CLUBID Parameter)
</aside>

## Get Transactions for a specific date range

```shell
curl "https://www.easycancha.com/api/clubs/<CLUBID>/transactionsReport/<FROMISODATE>/<TOISODATE>" \
  -H "apikey: customerrandomapikey"
```

> The above command returns JSON structured like this:

```json
{
    "error": false,
    "code": 0,
    "transactionsReport": [
        {
            "payment": {
                "localTransactionDateTime": "2024-05-02 16:48:43",
                "name": "TARJETA DE DÉBITO",
                "code": "DEBIT_CARD",
                "paymentIdentifier": "711157",
                "paymentUserFoidCountry": "CL",
                "paymentUserFoidType": "NI",
                "paymentUserFoidNumber": "192256585",
                "paymentUserFirstName": "Juan Carlos",
                "paymentUserLastName": "Rojas",
                "paymentUserPhone": "+56934516165",
                "paymentUserEmail": "juancarlos.rojas@easycancha.com",
                "amount": 30000,
                "paymentCurrencyName": "Pesos chilenos",
                "collector": "Juan Carlos Rojas",
                "last4digits": null,
                "authCode": null,
                "boletas": "",
                "dtesType": null,
                "dtes": null,
                "extra_info": null
            },
            "products": [
                {
                    "productId": 5,
                    "productTransactionId": 402535,
                    "transactionCategory": "Padel",
                    "transactionDetail": "Tarro de pelotas",
                    "transactionSubDetail": null,
                    "transactionDate": "2024-05-02",
                    "transactionTime": "17:30",
                    "userFoidCountry": "CL",
                    "userFoidType": "NI",
                    "userFoidNumber": "192256585",
                    "userFirstName": "Juan Carlos",
                    "userLastName": "Rojas",
                    "userGender": "M",
                    "userType": "SOCIO",
                    "productQuantity": 1,
                    "productAmount": 3000,
                    "fedegolfFee": null,
                    "asociacionFee": null,
                    "otherFee": null,
                    "fedegolfRealFee": null,
                    "fedegolfBoleta": null,
                    "currencyName": "Pesos chilenos",
                    "comments": null
                },
                {
                    "productId": 1,
                    "productTransactionId": 15485185,
                    "transactionCategory": "Padel",
                    "transactionDetail": "Cancha",
                    "transactionSubDetail": "Cancha 1",
                    "transactionDate": "2024-05-02",
                    "transactionTime": "17:30",
                    "userFoidCountry": "CL",
                    "userFoidType": "NI",
                    "userFoidNumber": "192256585",
                    "userFirstName": "Juan Carlos",
                    "userLastName": "Rojas",
                    "userGender": "M",
                    "userType": "SOCIO",
                    "productQuantity": 1,
                    "productAmount": 27000,
                    "fedegolfFee": null,
                    "asociacionFee": null,
                    "otherFee": null,
                    "fedegolfRealFee": null,
                    "fedegolfBoleta": null,
                    "currencyName": "Pesos chilenos",
                    "comments": "pago 10mil"
                }
            ]
        },
        {
            "payment": {
                "localTransactionDateTime": "2024-05-07 10:32:58",
                "name": "EFECTIVO",
                "code": "CASH",
                "paymentIdentifier": "515237",
                "paymentUserFoidCountry": "CL",
                "paymentUserFoidType": "NI",
                "paymentUserFoidNumber": "188857485",
                "paymentUserFirstName": "Obriel Elías",
                "paymentUserLastName": "Muga Molina",
                "paymentUserPhone": "+56976863563",
                "paymentUserEmail": "obriel.muga@easycancha.com",
                "amount": 4500,
                "paymentCurrencyName": "Pesos chilenos",
                "collector": "Obriel Muga",
                "last4digits": null,
                "authCode": null,
                "boletas": "",
                "dtesType": null,
                "dtes": null,
                "extra_info": null
            },
            "products": [
                {
                    "productId": 7,
                    "productTransactionId": 2035,
                    "transactionCategory": "Pack de cupones",
                    "transactionDetail": "Prueba de Pack 4",
                    "transactionSubDetail": null,
                    "transactionDate": "2024-05-07",
                    "transactionTime": "14:32",
                    "userFoidCountry": "CL",
                    "userFoidType": "NI",
                    "userFoidNumber": "188857485",
                    "userFirstName": "Obriel Elías",
                    "userLastName": "Muga Molina",
                    "userGender": "M",
                    "userType": "SOCIO",
                    "productQuantity": 1,
                    "productAmount": 4500,
                    "fedegolfFee": null,
                    "asociacionFee": null,
                    "otherFee": null,
                    "fedegolfRealFee": null,
                    "fedegolfBoleta": null,
                    "currencyName": "Pesos chilenos",
                    "comments": null
                }
            ]
        }
    ]
}
```

This endpoint retrieves all payments for the specified club / period with all products associated with that payment.

### HTTP Request

`GET https://www.easycancha.com/api/clubs/<CLUBID>/transactionsReport/<FROMISODATE>/<TOISODATE>`

<aside class="warning">
Maximum period for query is 1 month
</aside>


### URL Parameters

Parameter | Description
--------- | -----------
CLUBID | Club identifier
FROMISODATE | from Date (included) in YYYY-MM-DD format
TOISODATE | to Date (included) in YYYY-MM-DD format

### Object Payment description

Field | Type | Description
--------- | ----------- | -----------
localTransactionDateTime | string | local transaction date time in format YYYY-MM-DD HH:mm:ss
name | string | name of the form of payment
paymentIdentifier | string | id payment transaction
paymentUserFoidCountry | string | payment user document country ISO 3166-1 alpha-2
paymentUserFoidType | string | payment user document type, NI for Identification Number, PP for passport, and could be others depending on the country
paymentUserFoidNumber | string | payment user document number
paymentUserFirstName | string | payment user first name
paymentUserLastName | string | payment user last name
paymentUserPhone | string | payment user phone in international format + and numbers (ie. +56977087296)
paymentUserEmail | string | payment user email
amount | decimal | payment amount in local currency
paymentCurrencyName | string | name of the local currency
collector | string | collector of the payment. If payment was made online: ONLINE, if payment was made through SASS, name of the admin
last4digits | string | last 4 digits in case of card payments
authCode | string | authorization code in case of card payments
boletas | string | invoices manually entered through admin
dtesType | string | invoice types if invoices issued automatically if club has invoicing integration separated by ,
dtes | string | invoices issued automatically if club has invoicing integration separated by ,
extra_info | string | extra information about the payment

### Object Product description

Field | Type | Description
--------- | ----------- | -----------
productId | integer | product Id, 1 for courts, 2 for activities, 3 for other products, 5 for ancillaries, 7 for coupon pack
productTransactionId | integer | product transaction id
transactionCategory | string | product category
transactionDetail | string | product name
transactionSubDetail | string | product specific name
transactionDate | string | product date in YYYY-MM-DD format
transactionTime | string | product time in HH:mm format
userFoidCountry | string | user document country ISO 3166-1 alpha-2
userFoidType | string | user document type, NI for Identification Number, PP for passport, and could be others depending on the country
userFoidNumber | string | user document number
userFirstName | string | user first name
userLastName | string | user last name
userGender | string | user gender M for Male or F for Female
userType | string | customer type user for the booking
productAmount | decimal | product amount in local currency
fedegolfFee | decimal | not used
asociacionFee | decimal | not used
fedegolfRealFee | decimal | not used
fedegolfBoleta | integer | not used
currencyName | string name of the local currency
comments | string | comments for the booking

