Отчет о продажах
================

**Получение отчета о продажах за день**

Request:
`GET v1/shops/{shopId}/reports/{date}`

Body:
```javascript
[
    {
        "id": "3b36a51f-5b77-49bf-92aa-638d2a1f6136",
        "date": "17.07.2017",
        "time": "10:20:32",
        "isSale": "true",
        "price": 1284.00,
        "cashboxId": "f7cde55e-7289-4ab2-a64d-78ebbfcc5c09",
        "lines": 
        [
            {
                "productId": "87bb1ba7-8f3d-408c-810d-fa2261bf097a",
                "price": 100.00,
                "count": 3.00,
                "time": "10:20:31"
            },
            ...
        ]
    },
    ...
]
```

Response errors:
```javascript
{
    "errorCode": 400,
    "errorType": "incorrectDate",
    "decription": "Неверная дата"
}
```