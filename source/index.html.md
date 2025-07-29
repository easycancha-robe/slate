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

# Bookings

<aside class="success">
Context - These services apply to a specific club, which will be also informed at the moment of enabled the API, and will be part of the api URL (CLUBID Parameter)
</aside>

## Get Bookings for a specific period (and optional for a specific sport)

```shell
curl "https://www.easycancha.com/api/clubs/<CLUBID>/bookingsReport" \
  -H "apikey: customerrandomapikey"
```

> The above command returns JSON structured like this:

```json
{
    "error": false,
    "code": 0,
    "bookings": [
        {
            "id": "22215493",
            "courtId": 697,
            "sportId": 3,
            "sportName": "Futbolito",
            "courtName": "Cancha 2",
            "localDate": "2025-06-10",
            "localStartTime": "08:00",
            "localEndTime": "09:00",
            "timespan": 60,
            "userId": 66,
            "userFirstName": "Roberto",
            "userLastName": "De Campos Wichrowski",
            "userEmail": "robertodecampos@gmail.com",
            "userPhone": "+56998868135",
            "userBirthDate": "1979-09-09",
            "userFoidCountry": "CL",
            "userFoidType": "NI",
            "status": "BOOKED",
            "comments": null,
            "waived": "N",
            "bookedBy": "club",
            "amount": 25000,
            "amountPaid": 0,
            "ancillariesAmount": 62000,
            "ancillariesAmountPaid": 0,
            "totalAmount": 87000,
            "totalAmountPaid": 0,
            "discountAmount": 0,
            "customerCodes": "Socio",
            "ancillaries": [
            {
                "clubAncillaryId": "48",
                "quantity": 3,
                "name": "Terraza",
                "detail": "1 hora y media"
            },
            {
                "clubAncillaryId": "142",
                "quantity": 1,
                "name": "Luz",
                "detail": null
            }
            ]
        },
        {
            "id": "20611829",
            "courtId": 974,
            "sportId": 7,
            "sportName": "Padel",
            "courtName": "Cancha 1",
            "localDate": "2025-06-10",
            "localStartTime": "09:00",
            "localEndTime": "10:00",
            "timespan": 60,
            "userId": 77771,
            "userFirstName": "Emiliano",
            "userLastName": "Castellucci",
            "userEmail": "emilianocastellucci90@hotmail.com",
            "userPhone": "+56963337955",
            "userBirthDate": "1990-10-03",
            "userFoidCountry": "CL",
            "userFoidType": "NI",
            "status": "BOOKED",
            "comments": null,
            "waived": "N",
            "bookedBy": "club",
            "amount": 12000,
            "amountPaid": 0,
            "ancillariesAmount": null,
            "ancillariesAmountPaid": null,
            "totalAmount": 12000,
            "totalAmountPaid": 0,
            "discountAmount": 0,
            "customerCodes": "Socio"
        }
    ]
}       
```

This endpoint retrieves all bookings between fromIsoDate and toIsoDate (included).
You can get a list of all booking, or you can query by sportId and get specific information for just one sport.

### HTTP Request

`GET https://www.easycancha.com/api/clubs/<CLUBID>/bookingsReport`

### URL Parameters

Parameter | Description
--------- | -----------
CLUBID | Club identifier

### QUERY Parameters
Parameter | Description | Mandatory
--------- | ----------- | ---------
fromIsoDate | from Date (included) in YYYY-MM-DD format | Y
toIsoDate | to Date (included) in YYYY-MM-DD format | Y
sportId | sportId to filter | N

### Object bookings description

Field | Type | Description
--------- | ----------- | -----------
id | number | booking id
courtId | number | court id
sportId | number | sport id
sportName | string | sport name
courtName | string | court name
localDate | string | booking local date in YYYY-MM-DD format
localStartTime | string | booking local start time in HH:mm:ss format
localEndTime | string | booking local end time in HH:mm:ss format
timespan | number | duration of the booking
userId | number | user id
userFirstName | string | user first name
userLastName | string | user last name
userEmail | string | user email
userPhone | string | user phone
userBirthDate | string | user birth date in YYYY-MM-DD format
userFoidCountry | string | user document country ISO 3166-1 alpha-2
userFoidType | string | user document type, NI for Identification Number, PP for passport, and could be others depending on the country
userFoidNumber | string | user document number
status | string | status of the booking. Can be one of BOOKED, PARTIALLY_PAID, PAID , USED, CANCELLED, EXCHANGED
comments | string | comments of the bookings
waived | string | "Y" or "N" depending if the booking was waived by the club for changes / cancellations
bookedBy | string | "club" or "user" depending if the booking was made by the club or the user
amount | number | booking total amount
amountPaid | number | booking paid amount
ancillariesAmount | number | ancillaries total amount
ancillariesAmountPaid | number | ancillaries paid amount
totalAmount | number | total amount (booking + ancillaries)
totalAmountPaid | number | total paid amount (booking + ancillaries)
discountAmount | number | discount amount
customerCodes | string | customer codes associated with the booking
ancillaries | array | array of ancillary items

### Object ancillaries description

Field | Type | Description
--------- | ----------- | -----------
clubAncillaryId | number | unique id of ancillary for club
quantity | number | quantity
name | string | name of ancillary
detail | string | detaill of ancillary

# Access Control

<aside class="success">
Context - These services apply to a specific club, which will be also informed at the moment of enabled the API, and will be part of the api URL (CLUBID Parameter)
</aside>


## Get Customer Code Enabled users

```shell
curl "https://www.easycancha.com/api/clubs/<CLUBID>/customerCodes/<CUSTOMERCODEID>/getCustomers" \
  -H "apikey: customerrandomapikey"
```

> The above command returns JSON structured like this:

```json
{
    "error": false,
    "code": 0,
    "customers": [
        {
            "firstName": "Roberto",
            "lastName": "de Campos Wichrowski",
            "fullName": "Roberto de Campos Wichrowski",
            "foidCountry": "CL",
            "foidType": "NI",
            "foidNumber": "14543789K",
            "memberId": null
        },
        {
            "firstName": "Patricio",
            "lastName": "Cordero",
            "fullName": "Patricio Cordero",
            "foidCountry": "CL",
            "foidType": "NI",
            "foidNumber": "154455671",
            "memberId": "554345"
        }
    ]
}
```

This endpoint retrieves all users that have a specific customer code enabled that should be able to acces the facilities.
You can get a list of all customers, or you can query by foid_country / foid_type / foid_number and get specific information for just one customer.

### HTTP Request

`GET https://www.easycancha.com/api/clubs/<CLUBID>/customerCodes/<CUSTOMERCODEID>/getCustomers`

### URL Parameters

Parameter | Description
--------- | -----------
CLUBID | Club identifier
CUSTOMERCODEID | Specific customer code to retrieve

### QUERY Parameters
Parameter | Description | Mandatory
--------- | ----------- | ---------
foid_country | user document country ISO 3166-1 alpha-2 | N
foid_type | user document type, NI for Identification Number, PP for passport, and could be others depending on the country | N
foid_number | user document number | N

### Object User description

Field | Type | Description
--------- | ----------- | -----------
firstName | string | user first name
lastName | string | user last name
fullName | string | user full name
foidCountry | string | user document country ISO 3166-1 alpha-2
foidType | string | user document type, NI for Identification Number, PP for passport, and could be others depending on the country
foidNumber | string | user document number
memberId | string | user member ID

## Get Bookings

```shell
curl "https://www.easycancha.com/api/clubs/<CLUBID>/getBookings" \
  -H "apikey: customerrandomapikey"
```

> The above command returns JSON structured like this:

```json
{
    "error": false,
    "code": 0,
    "bookings": [
        {
            "firstName": "Roberto",
            "lastName": "de Campos Wichrowski",
            "foidCountry": "CL",
            "foidType": "NI",
            "foidNumber": "145437377",
            "bookingId": 11,
            "sportName": "Padel",
            "localStartDateTime": "2023-11-20 12:00:00",
            "localEndDateTime": "2023-11-20 13:00:00"
        },
        {
            "firstName": "Daniela",
            "lastName": "Baytelman",
            "foidCountry": "CL",
            "foidType": "NI",
            "foidNumber": "130278914",
            "bookingId": 12,
            "sportName": "Padel",
            "localStartDateTime": "2023-11-20 13:00:00",
            "localEndDateTime": "2023-11-20 14:00:00"
        }
    ],
    "activity_bookings": [
        {
            "firstName": "Roberto",
            "lastName": "de Campos Wichrowski",
            "fullName": "Roberto de Campos Wichrowski",
            "foidCountry": "CL",
            "foidType": "NI",
            "foidNumber": "145437377",
            "bookingId": 282254,
            "category": "Membresías",
            "name": "Black",
            "localStartDateTime": "2025-04-24 00:00:00",
            "localEndDateTime": "2025-05-23 00:00:00"
        },
        {
            "firstName": "Daniela",
            "lastName": "Baytelman",
            "fullName": "Daniela Baytelman",
            "foidCountry": "CL",
            "foidType": "NI",
            "foidNumber": "130278914",
            "bookingId": 282254,
            "category": "Gimnasio",
            "name": "Personal Trainer",
            "localStartDateTime": "2025-04-24 00:00:00",
            "localEndDateTime": "2025-05-23 00:00:00"
        }
    ]
}
```

This endpoint retrieves all bookings for the current day and this information should be used to grant access to acces the facilities.
You can get a list of all booking for the day, or you can query by foid_country / foid_type / foid_number and get specific information for just one customer.

### HTTP Request

`GET https://www.easycancha.com/api/clubs/<CLUBID>/getBookings`

### URL Parameters

Parameter | Description
--------- | -----------
CLUBID | Club identifier

### QUERY Parameters
Parameter | Description | Mandatory
--------- | ----------- | ---------
foid_country | user document country ISO 3166-1 alpha-2 | N
foid_type | user document type, NI for Identification Number, PP for passport, and could be others depending on the country | N
foid_number | user document number | N

### Object bookings description

Field | Type | Description
--------- | ----------- | -----------
firstName | string | user first name
lastName | string | user last name
foidCountry | string | user document country ISO 3166-1 alpha-2
foidType | string | user document type, NI for Identification Number, PP for passport, and could be others depending on the country
foidNumber | string | user document number

### Object activity_bookings description

Field | Type | Description
--------- | ----------- | -----------
firstName | string | user first name
lastName | string | user last name
foidCountry | string | user document country ISO 3166-1 alpha-2
foidType | string | user document type, NI for Identification Number, PP for passport, and could be others depending on the country
foidNumber | string | user document number
