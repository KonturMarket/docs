Авторизация
-----------

В сервисе можно получить токен для доступа ко всем данным, конкретной организации или магазину. Можно получить доступ только на чтение, или на чтение и запись
В дальнейшем необходимо передавать полученный токен в заголовках всех запросов к API.

Данные
------

Нужно обеспечить доступ к следующим данным:
1. [Товары](Doc/Data/Products.md)
2. [Накладные](Doc/Data/WayBills.md)
3. [Отчеты о продажах](Doc/Data/Reports.md)
4. [Акты списаний и постановок](Doc/Data/Acts.md)
5. [Реквизиты организаций](Doc/Data/Organization.md)
6. [Реквизиты торговых точек](Doc/Data/Shops.md)
7. [Реквизиты контрагентов](Doc/Data/Contractors.md)
8. [Информация о кассе](Doc/Data/Cashbox.md)

Общие ошибки
------------

```javascript
{
    "errorCode": 401,
    "errorType": "unauthorized",
    "decription": "Необходима авторизация"
}

{
    "errorCode": 403,
    "errorType": "accessDenied",
    "decription": "Нет доступа к запрашиваемым данным"
}

{
    "errorCode": 403,
    "errorType": "requestsCountExceeded",
    "decription": "Превышено количество обращений за день"
}

{
    "errorCode": 404,
    "errorType": "shopNotFound",
    "decription": "Магазин не найден"
}

{
    "errorCode": 404,
    "errorType": "organizationNotFound",
    "decription": "Организация не найдена"
}
```