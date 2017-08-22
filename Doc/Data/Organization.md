Реквизиты организаций
=====================
**Получение реквизитов организации**

Request:  
`GET v1/organizations/{organizationId}`

Response:
```javascript
{
    "id": "b74a3979-c645-49ab-8572-e9db43e3cbab",
    "inn": "6699000000",
    "name": "Organization",
}
```

Response errors:
```javascript
{
    "errorCode": 404,
    "errorType": "organizationNotFound",
    "decription": "Организация не найдена"
}
```