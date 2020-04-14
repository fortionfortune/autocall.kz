# Получение отчётов при sms рассылках

Если Вы указали в параметре callback_url полный URL Вашей системы, то при каждой смене статуса рассылки, а также при каждой смене статуса сообщения Вы будете получать POST запросы.

POST запрос будет содержать JSON и иметь соответствующий HEADER Content-Type: application/json.

При любой смене статуса рассылки Вы получите следующий запрос:

```json
{
  "bulk":{
      "id": 9,
      "client_id": "192381",
      "name": "Test calculate",
      "status": "completed",
      "date_from": "2020-03-30 00:00:00",
      "time_from": "07:17:12",
      "text": "Тестовое сообщение",
      "segments": 1,
      "recipients": 1,
      "list_id": [
        65
      ],
      "max_cost": "8.00",
      "final_cost": "8",
      "comment": "",
      "callback_url": "https://examplce.com/reports",
      "created_at": "2020-03-30 07:17:12",
      "updated_at": "2020-03-30 07:17:12",
      "counters": {
        "total": 1,
        "queued": 0,
        "disabled": 0,
        "new": 0,
        "sent": 0,
        "delivered": 1,
        "pending": 0,
        "failed": 0,
        "expired": 0,
        "undeliverable": 0,
        "rejected": 0
      }
  }
}
```

При любой смене статуса сообщения в этой рассылке Вы получите следующий POST запрос:
```json
{
  "message":{
    "id": 30,
    "bulk_id": 9,
    "number": "+77010000001",
    "extra": "папа",
    "status": "delivered ",
    "provider": "Kcell",
    "init_time": "2020-04-14 19:42:32",
    "status_time": "2020-04-14 19:42:45",
    "created_at": "2020-04-14 19:42:01",
    "updated_at": "2020-04-14 19:42:45"
  }
}
```