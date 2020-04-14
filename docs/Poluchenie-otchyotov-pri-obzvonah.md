---
tags: [callback_url-autocalls]
---

# Получение отчётов в обзвонах

Если Вы указали в параметре callback_url полный URL Вашей системы, то при каждой смене статуса обзвона, а также при каждом звонке абоненту Вы будете получать POST запросы.

POST запрос будет содержать JSON и иметь соответствующий HEADER Content-Type: application/json.

При любой смене статуса обзвона Вы получите следующий запрос:

```json
{
  "autocall":{
    "id": 9,
    "client_id": "1239543",
    "name": "test",
    "date_from": "2020-03-17 00:00:00",
    "time_from": "12:00:00",
    "time_to": "18:00:00",
    "max_tries": 2,
    "tries_interval": 60,
    "type": "regular",
    "sms": false,
    "sms_unanswered": false,
    "text": null,
    "text_unanswered": null,
    "audio_id": [
      "6"
    ],
    "list_id": [
      13,
      12,
      8
    ],
    "scenario_id": null,
    "max_cost": "5.44",
    "final_cost": null,
    "processed": 0,
    "speeches": 0,
    "lifetime": false,
    "record": false,
    "status": "running",
    "comment": null,
    "callback_url": "https://example.com/reports",
    "finished_at": null,
    "created_at": "2020-03-17 15:30:45",
    "updated_at": "2020-03-17 15:30:45",
    "calls_count": 5,
    "processed_percentage": 0,
    "counters": {
      "success_percentage": 0,
      "success": 0,
      "recalled": 0,
      "no_answer": 0,
      "busy": 0,
      "error": 0,
      "spam": 0,
      "tries": 0,
      "duration": 0,
      "total": 5
    }
  }
}
```

При смене статусов звонков в этом обзвоне Вы получите следующий запрос:

```json
{
  "call":{
      "id": 35,
      "autocall_id": 9,
      "number": "+77010000001",
      "extra": "Тимофеев А.Р.",
      "lock": false,
      "tries": 2,
      "date_tries": [
        "2020-04-14 09:00:00", "2020-04-14 10:00:00"
      ],
      "status_tries": [
        "busy","success"
      ],
      "last_try_at": "2020-04-14 10:00:00",
      "duration": 6,
      "r_duration": 0,
      "status": "success",
      "data": [],
      "created_at": "2020-04-14 04:50:29",
      "updated_at": "2020-04-14 10:00:00"
  }
}
```
