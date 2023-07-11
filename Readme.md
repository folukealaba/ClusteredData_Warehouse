
# ClusteredData Warehouse

This is to analyze fx deals by accepting deals and persisting in DB.


##  Run - Docker
```sh
docker-compose up
```

2 / 2

On the first run, the application will not run because MySQL database is still in the process of downloading. Please refrain from closing the application as it will automatically reconnect to synchronize with the database once the download is complete.

## Project Run
#### How to run the project
- To run the project you need docker and a java environment (19). Navigate to the project root and run
- ```shell
    docker-compose up -d
``` 
or simply run if you have make installed. the application runs on port 7070

```
 make
```



- Run this command
```sh
 mvn clean spring-boot:run
```

## PROJECT DOCUMENTATION

#### Technology Used
- SPRINGBOOT
- MYSQL
- DOCKER

# Project Packages
#### Resource
- POST - /api/v1/fxDeals - The endpoint saves fx deal to the DB
- GET - /api/v1/fxDeals - The endpoint retrieves a list of fxDeals from the DB
- GET - /api/v1/fxDeals/{id} - Get a fx deal by id

### Service and Impl
- The business logic is in the serviceImpl package in the service package. The service class is an interface that implements the serviceImpl class.

#### Model
- id - Unique id
- fromCurrency - ISO Currency from deal with Datatype: Currency
- toCurrency - ISO Currency to deal with Datatype: Currency
- dealTimeStamp - Instantaneous time with Datatype: Instant
- dealAmount - Amount with Datatype: BigDecimal

#### Logging
- Logging used to log errors and info for the service clas.

### Request body
{
"fromCurrency": "USD",
"toCurrency": "EUR",
"dealAmount": "500.0",
"timeStamp": 1642510101000
}

### Success Response to save FxDeal
```json
{
"status": "The FxDeal is saved successfully",
"message": "success",
"data": {
"id": 6,
"fromCurrency": "USD",
"toCurrency": "EUR",
"dealTimeStamp": "2023-06-21T11:54:48.449188",
"dealAmount": 500.0
}
}
```

```json --- To retrieve FxDeals
{
  "message": "successful",
  "status": "OK",
  "data": {
    "contents": [
      {
        "dealUniqueId": "114",
        "fromCurrencyISOCode": "USD",
        "toCurrencyISOCode": "NGN",
        "dealTimeStamp": "2023-07-11T16:42:04.35729",
        "dealAmount": 90.00
      },
      {
        "dealUniqueId": "111",
        "fromCurrencyISOCode": "USD",
        "toCurrencyISOCode": "NGN",
        "dealTimeStamp": "2023-07-11T16:42:09.587207",
        "dealAmount": 90.00
      },
      {
        "dealUniqueId": "1131",
        "fromCurrencyISOCode": "USD",
        "toCurrencyISOCode": "NGN",
        "dealTimeStamp": "2023-07-11T16:42:12.952732",
        "dealAmount": 90.00
      }
    ],
    "pageNumber": 3,
    "pageSize": 10
  }
}
```

### Error Response
```json
{
  "status": "error",
  "message": "The Currency ISO code is invalid",
  "data": ""
}
```

TEST
- Unit test in the test folder
