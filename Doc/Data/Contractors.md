Реквизиты контрагентов
======================

**Получение реквизитов контрагента**

Request:  
`GET v1/shops/{shopId}/contractors/{contractorId}`

Response:
```javascript
{
    "id": "b74a3979-c645-49ab-8572-e9db43e3cbab",
    "inn": "6699000000",
    "kpp": "669901001",
    "name": "Organization",
    "address": "Lenina 1"
}
```

Response errors:
```javascript
{
    "errorCode": 404,
    "errorType": "contractorNotFound",
    "decription": "Контрагент не найден"
}
```

**Получение списка контрагентов**

Request:  
`GET v1/shops/{shopId}/contractors`

Response:
```javascript
[
    {
        "id": "b74a3979-c645-49ab-8572-e9db43e3cbab",
        "inn": "6699000000",
        "kpp": "669901001",
        "name": "Organization",
        "address": "Lenina 1"
    },
    ...
]
```