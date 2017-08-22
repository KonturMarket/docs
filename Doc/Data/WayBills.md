Накладные
=========

**Получение входящей накладной по Id**

Request:  
`GET v1/shops/{shopId}/wayBills/in/{wayBillId}`

Response:
```javascript
{
    "id": "aa7e47db-08ba-4fee-96f1-8bdb7af12643",
    "date": "15.07.2017",
    "number": "1337",
    "contractorId": "81ef5dfb-d788-4687-9a88-09f48fa3ced4",
    "shopId": "b1851d1d-eca1-40cf-8e87-48dccdeef0f2",
    "receiveDate": "16.07.2017",
    "products":
    [
    	{
            "productId": "c8a1638a-1eab-4c3b-b998-af6f775f916f",
            "quantity": 2.00,
            "buyPrice": 100.00,
            "totalBuySum": 200.00
    	},
        ...
    ]
}
```

Response errors:
```javascript
{
    "errorCode": 404,
    "errorType": "wayBillNotFound",
    "decription": "Накладная не найдена"
}
```

**Получение всех входящих накладных по Id магазина**

Requests:  
`GET v1/shops/{shopId}/wayBills/in?pageId=aa7e47db-08ba-4fee-96f1-8bdb7af12642&pageSize=1000`

Response:

```javascript
{
    "nextPageId": "2017_c65263ec-70da-45e3-844c-14e213320ef6",
    "wayBills":
    [
        {
            "id": "aa7e47db-08ba-4fee-96f1-8bdb7af12643",
            "date": "15.07.2017",
            "number": "1337",
            "contractorId": "81ef5dfb-d788-4687-9a88-09f48fa3ced4",
            "shopId": "b1851d1d-eca1-40cf-8e87-48dccdeef0f2",
            "receiveDate": "16.07.2017",
            "products":
            [
                {
                    "productId": "c8a1638a-1eab-4c3b-b998-af6f775f916f",
                    "quantity": 2.00,
                    "buyPrice": 100.00,
                    "totalBuySum": 200.00
                },
                ...
            ]
        },
        ...
    ]
}
```

Response errors:
```javascript
{
    "errorCode": 400,
    "errorType": "bigPageSize",
    "decription": "Размер страницы не может быть больше 1000"
}

{
    "errorCode": 400,
    "errorType": "wrongPageSize",
    "decription": "Размер страницы не может быть меньше 1"
}
```

**Получение исходящей накладной по Id**

Request:  
`GET v1/shops/{shopId}/wayBills/out/{wayBillId}`

Response:
```javascript
{
    "id": "aa7e47db-08ba-4fee-96f1-8bdb7af12643",
    "date": "15.07.2017",
    "number": "1337",
    "contractorId": "81ef5dfb-d788-4687-9a88-09f48fa3ced4",
    "shopId": "b1851d1d-eca1-40cf-8e87-48dccdeef0f2",
    "shippingDate": "16.07.2017",
    "products":
    [
    	{
            "productId": "c8a1638a-1eab-4c3b-b998-af6f775f916f",
            "quantity": 2.00,
            "sellPrice": 100.00,
            "sumWithNds": 200.00
    	},
        ...
    ]
}
```

Response errors:
```javascript
{
    "errorCode": 404,
    "errorType": "wayBillNotFound",
    "decription": "Накладная не найдена"
}
```

**Получение всех исходящих накладных по Id магазина**

Request:  
`GET v1/shops/{shopId}/wayBills/out?pageId=aa7e47db-08ba-4fee-96f1-8bdb7af12642&pageSize=1000`

Response:
```javascript
{
    "nextPageId": "2017_c65263ec-70da-45e3-844c-14e213320ef6",
    "wayBills":
    [
        {
            "id": "aa7e47db-08ba-4fee-96f1-8bdb7af12643",
            "date": "15.07.2017",
            "number": "1337",
            "contractorId": "81ef5dfb-d788-4687-9a88-09f48fa3ced4",
            "shopId": "b1851d1d-eca1-40cf-8e87-48dccdeef0f2",
            "shippingDate": "16.07.2017",
            "products":
            [
                {
                    "productId": "c8a1638a-1eab-4c3b-b998-af6f775f916f",
                    "quantity": 2.00,
                    "sellPrice": 100.00,
                    "sumWithNds": 200.00
                },
                ...
            ]
        },
        ...
    ]
}
```

Response errors:
```javascript
{
    "errorCode": 400,
    "errorType": "bigPageSize",
    "decription": "Размер страницы не может быть больше 1000"
}

{
    "errorCode": 400,
    "errorType": "wrongPageSize",
    "decription": "Размер страницы не может быть меньше 1"
}
```