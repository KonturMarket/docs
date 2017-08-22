Товары
======

В товарах используются следующие константы:
```javascript
var VatRate = {
    "main": "Main",
    "preferential": "Preferential",
    "noVat": "NoVat",
};

var PriceType = {
    "fixPrice": "FixPrice",
    "withoutPrice": "WithoutPrice",
    "priceRule": "PriceRule",
};
```

**Информация о цене**

При создании или изменении товара в поле `"priceInfo"` достаточно передавать только необходимые поля в зависимости от типа `"priceType"`

`fixPrice`:
```javascript
{
    "sellPrice": 700.00,
    "buyPrice": 500.00,
    "buyPriceDate": "23.06.2017",
    "priceType": "fixPrice"
}
```

`withoutPrice`:
```javascript
{
    "buyPrice": 500.00,
    "buyPriceDate": "23.06.2017",
    "priceType": "withoutPrice"
}
```

`priceRule`:
```javascript
{
    "percent": 15,
    "dividerInKopecks": 10000,
    "buyPrice": 500.00,
    "buyPriceDate": "23.06.2017",
    "priceType": "priceRule"
}
```

**Описание ошибок**

```javascript
{
    "errorCode": 404,
    "errorType": "productNotFound",
    "decription": "Товар не найден"
}

{
    "errorCode": 400,
    "errorType": "egaisNonUnique",
    "decription": "В списке ЕГАИС кодов есть неуникальные значения"
}

{
    "errorCode": 400,
    "errorType": "egaisExists",
    "decription": "Существует товар с таким же ЕГАИС кодом"
}

{
    "errorCode": 400,
    "errorType": "barcodeNonUnique",
    "decription": "В списке баркодов есть неуникальные значения"
}

{
    "errorCode": 400,
    "errorType": "barcodeExists",
    "decription": "Существует товар с таким же баркодом"
}

{
    "errorCode": 400,
    "errorType": "incompatibleEgaisCodes",
    "decription": "Несовместимые ЕГАИС коды"
}

{
    "errorCode": 400,
    "errorType": "nonAlcoProduct",
    "decription": "Неалкогольный товар не может содержать ЕГАИС коды"
}

{
    "errorCode": 400,
    "errorType": "alcoProduct",
    "decription": "Алкогольный товар должен содержать хотя бы один ЕГАИС код"
}

{
    "errorCode": 400,
    "errorType": "repeatedIds",
    "decription": "Идентификаторы не должны повторяться"
}
```

**Получение списка товаров по магазину**

Request:  
`GET v1/shops/{shopId}/products`

Response:
```javascript
[
    {
        "id": "b74a3979-c645-49ab-8572-e9db43e3cbab",
        "name": "Becherovka",
        "nomenclature": "2",
        "barcodes": ["12345678", "87654321"],
        "egaisCodes": ["1234567890123", "1234567890120"],
        "vatRate": "main",
        "isDeleted": false,
        "weightGood": false,
        "pricesInfo": {
            "percent": 15,
            "dividerInKopecks": 10000,
            "sellPrice": 700.00,
            "buyPrice": 500.00,
            "buyPriceDate": "23.06.2017",
            "priceType": "fixPrice"
        }
    },
    ...
]
```

**Получение реквизитов товара**

Request:  
`GET v1/shops/{shopId}/products/{productId}`

Response:
```javascript
{
    "id": "b74a3979-c645-49ab-8572-e9db43e3cbab",
    "name": "Becherovka",
    "nomenclature": "2",
    "barcodes": ["12345678", "87654321"],
    "egaisCodes": ["1234567890123", "1234567890120"],
    "vatRate": "main",
    "isDeleted": false,
    "weightGood": false,
    "pricesInfo": {
        "percent": 15,
        "dividerInKopecks": 10000,
        "sellPrice": 700.00,
        "buyPrice": 500.00,
        "buyPriceDate": "23.06.2017",
        "priceType": "fixPrice"
    }
}
```

Response errors:
```javascript
{
    "errorCode": 404,
    "errorType": "productNotFound",
    "decription": "Товар не найден"
}
```

**Удаление товара**

Request:  
`DELETE v1/shops/{shopId}/products/{productId}`

Response errors:
```javascript
{
    "errorCode": 404,
    "errorType": "productNotFound",
    "decription": "Товар не найден"
}
```

**Изменение товара**

Request:  
`PUT v1/shops/{shopId}/products/{productId}`

Body:
```javascript
{
    "id": "b74a3979-c645-49ab-8572-e9db43e3cbab",
    "name": "Becherovka",
    "barcodes": ["12345678", "87654321"],
    "egaisCodes": ["1234567890123", "1234567890120"],
    "vatRate": "main",
    "isDeleted": false,
    "weightGood": false,
    "pricesInfo": {
        "percent": 15,
        "dividerInKopecks": 10000,
        "sellPrice": 700.00,
        "buyPrice": 500.00,
        "buyPriceDate": "23.06.2017",
        "priceType": "fixPrice",
    }
}
```

**Пакетное изменение товаров**

Request:  
`PUT v1/shops/{shopId}/products/batch`

Body:
```javascript
[
    {
        "id": "b74a3979-c645-49ab-8572-e9db43e3cbab",
        "name": "Becherovka",
        "barcodes": ["12345678", "87654321"],
        "egaisCodes": ["1234567890123", "1234567890120"],
        "vatRate": "main",
        "isDeleted": false,
        "weightGood": false,
        "pricesInfo": {
            "percent": 15,
            "dividerInKopecks": 10000,
            "sellPrice": 700.00,
            "buyPrice": 500.00,
            "buyPriceDate": "23.06.2017",
            "priceType": "fixPrice",
        }
    },
    ...
]
```

**Создание товара**

Request:  
`POST v1/shops/{shopId}/products`

Body:
```javascript
{
    "name": "Becherovka",
    "barcodes": ["12345678", "87654321"],
    "egaisCodes": ["1234567890123", "1234567890120"],
    "vatRate": "main",
    "weightGood": false,
    "pricesInfo": {
        "percent": 15,
        "dividerInKopecks": 10000,
        "sellPrice": 700.00,
        "buyPrice": 500.00,
        "buyPriceDate": "23.06.2017",
        "priceType": "fixPrice"
    }
}
```

Response:
```javascript
{
    "id": "b74a3979-c645-49ab-8572-e9db43e3cbab",
    "name": "Becherovka",
    "nomenclature": "2",
    "barcodes": ["12345678", "87654321"],
    "egaisCodes": ["1234567890123", "1234567890120"],
    "vatRate": "main",
    "isDeleted": false,
    "weightGood": false,
    "pricesInfo": {
        "percent": 15,
        "dividerInKopecks": 10000,
        "sellPrice": 700.00,
        "buyPrice": 500.00,
        "buyPriceDate": "23.06.2017",
        "priceType": "fixPrice"
    }
}
```

**Пакетное создание товаров**

Request:  
`POST v1/shops/{shopId}/products/batch`

Body:
```javascript
[
    {
        "name": "Becherovka",
        "barcodes": ["12345678", "87654321"],
        "egaisCodes": ["1234567890123", "1234567890120"],
        "vatRate": "main",
        "weightGood": false,
        "pricesInfo": {
            "percent": 15,
            "dividerInKopecks": 10000,
            "sellPrice": 700.00,
            "buyPrice": 500.00,
            "buyPriceDate": "23.06.2017",
            "priceType": "fixPrice"
        }
    },
    ...
]
```

Response:
```javascript
[
    {
        "id": "b74a3979-c645-49ab-8572-e9db43e3cbab",
        "name": "Becherovka",
        "nomenclature": "2",
        "barcodes": ["12345678", "87654321"],
        "egaisCodes": ["1234567890123", "1234567890120"],
        "vatRate": "main",
        "isDeleted": false,
        "weightGood": false,
        "pricesInfo": {
            "percent": 15,
            "dividerInKopecks": 10000,
            "sellPrice": 700.00,
            "buyPrice": 500.00,
            "buyPriceDate": "23.06.2017",
            "priceType": "fixPrice"
        }
    }
    ...
]
```
