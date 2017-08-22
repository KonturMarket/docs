Реквизиты торговых точек
========================

**Получение списка магазинов по организации**

Request:  
`GET v1/organizations/{organizationId}/shops`

Response:
```javascript
[
    {
        "id": "b74a3979-c645-49ab-8572-e9db43e3cbab",
        "address": "Maloprudnaya 5",
        "name": "Magaz 1",
    },
    {
        "id": "cffa3985-4545-49ab-fe72-e9def3eefbde",
        "address": "Maloprudnaya 6",
        "name": "Magaz 2",
    },
    ...
]
```

**Получение реквизитов магазина**

Request:  
`GET v1/shops/{shopId}`

Response:
```javascript
{
    "id": "b74a3979-c645-49ab-8572-e9db43e3cbab",
    "address": "Maloprudnaya 5",
    "name": "Magaz",
}
```

Response errors:
```javascript
{
    "errorCode": 404,
    "errorType": "shopNotFound",
    "decription": "Магазин не найден"
}
```
