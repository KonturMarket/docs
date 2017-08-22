Акты списания и постановок
==========================

**Константы**

```javascript
var ChargeOnType = {
    "none":        "None",        //Не указана
    "changeGrade": "ChangeGrade", //Пересортица
    "overage":     "Overage",     //Излишки
};

var WriteOffType = {
    "none":        "None",        //Не указана
    "changeGrade": "ChangeGrade", //Пересортица
    "lack":        "Lack",        //Недостача
    "writeDown":   "WriteDown",   //Уценка
    "damage":      "Damage",      //Порча
    "loss":        "Loss",        //Потери
    "other":       "Other",       //Иные цели
    "selling":     "Selling"      //Реализация
}; 
```

**Получение акта постановки по Id**

Request:  
`GET v1/shops/{shopId}/acts/chargeOn/{actId}`

Response:
```javascript
{
    "id": "8401c638-884e-4c73-871d-ef10c3024ca0",
    "date": "15.07.2017",
    "number": "1337",
    "shopId": "b1851d1d-eca1-40cf-8e87-48dccdeef0f2",
    "note": "Нашли ящик водки",
    "chargeOnType": "overage",
    "products":
    [
    	{
            "productId": "c8a1638a-1eab-4c3b-b998-af6f775f916f",
            "quantity": 2.00
    	},
        ...
    ]
}
```

Response errors:
```javascript
{
    "errorCode": 404,
    "errorType": "actNotFound",
    "decription": "Акт не найден"
}
```

**Получение всех актов постановки по Id магазина**

Request:  
`GET v1/shops/{shopId}/acts/chargeOn?pageId=8401c638-884e-4c73-871d-ef10c3024c9f&pageSize=1000`

Response:
```javascript
{
    "nextPageId": "c65263ec-70da-45e3-844c-14e213320ef6",
    "acts":
    [
        {
            "id": "8401c638-884e-4c73-871d-ef10c3024ca0",
            "date": "15.07.2017",
            "number": "1337",
            "shopId": "b1851d1d-eca1-40cf-8e87-48dccdeef0f2",
            "note": "Нашли ящик водки",
            "chargeOnType": "overage",
            "products":
            [
                {
                    "productId": "c8a1638a-1eab-4c3b-b998-af6f775f916f",
                    "quantity": 2.00
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
    "errorType": "tooMuchCount",
    "decription": "Запрошено слишком большое количество. Можно запрашивать максимум 1000 элементов за раз"
}
```

**Получение акта списания по Id**

Request:  
`GET v1/shops/{shopId}/acts/writeOff/{actId}`  

Response:
```javascript
{
    "id": "7396f560-d2df-4ab6-8bd1-4b1c90c053c0",
    "date": "15.07.2017",
    "number": "1337",
    "shopId": "b1851d1d-eca1-40cf-8e87-48dccdeef0f2",
    "note": "Украли ящик водки",
    "writeOffType": "loss",
    "products":
    [
        {
            "productId": "c8a1638a-1eab-4c3b-b998-af6f775f916f",
            "quantity": 2.00
        },
        ...
    ]
}
```

Response errors:
```javascript
{
    "errorCode": 404,
    "errorType": "actNotFound",
    "decription": "Акт не найден"
}
```

**Получение всех актов списания по Id магазина**

Request:  
`GET v1/shops/{shopId}/acts/writeOff?pageId=7396f560-d2df-4ab6-8bd1-4b1c90c053bf&pageSize=1000`  

Response:

```javascript
{
    "nextPageId": "c65263ec-70da-45e3-844c-14e213320ef6",
    "acts":
    [
        {
            "id": "7396f560-d2df-4ab6-8bd1-4b1c90c053c0",
            "date": "15.07.2017",
            "number": "1337",
            "shopId": "b1851d1d-eca1-40cf-8e87-48dccdeef0f2",
            "note": "Украли ящик водки",
            "writeOffType": "loss",
            "products":
            [
                {
                    "productId": "c8a1638a-1eab-4c3b-b998-af6f775f916f",
                    "quantity": 2.00
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
    "errorType": "tooMuchCount",
    "decription": "Запрошено слишком большое количество. Можно запрашивать максимум 1000 элементов за раз"
}
```