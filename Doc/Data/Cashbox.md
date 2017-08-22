Информация о кассе
==================

**Получение списка касс в магазине**

Request:  
`GET v1/shops/{shopId}/cashboxes`

Response:
```javascript
[
    {
        "id": "f7cde55e-7289-4ab2-a64d-78ebbfcc5c09",
        "name": "Kassa 1"
    },
    ...
]
```

**Получение информации о кассе**

Request:  
`GET v1/shops/{shopId}/cashboxes/{cashboxId}`

Response:
```javascript
{
    "id": "f7cde55e-7289-4ab2-a64d-78ebbfcc5c09",
    "name": "Kassa 1"
}
```

Response errors:
```javascript
{
    "errorCode": 404,
    "errorType": "cashboxNotFound",
    "decription": "Касса не найдена"
}
```