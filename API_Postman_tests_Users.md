> # Раздел 5. Users
> результаты тестирования [Fake REST API](https://fakerestapi.azurewebsites.net/index.html) по [таблице тест-кейсов](https://github.com/morynthe/API-testing/blob/main/TestIT_export_FakeRestApi_Users.xlsm) с использованием Postman

## 1) 5.1 Users : получение списка пользователей * GET ​/api​/v1​/Users 200 OK
- **URL** https://fakerestapi.azurewebsites.net/api/v1/Users
- **Ожидаемый результат:** код HTTPS ответа: `200 Success` - успешное получениe ответа со списком пользователей
- **Заголовки запроса:** 
`User-Agent: PostmanRuntime/7.32.3
Accept: */*
Cache-Control: no-cache
Postman-Token: 9bee2a61-3e76-47db-a991-62abe1c8bade
Host: fakerestapi.azurewebsites.net
Accept-Encoding: gzip, deflate, br
Connection: keep-alive`
- **Тело запроса** `-`
- **Заголовки ответа**
`Content-Type: application/json; charset=utf-8; v=1.0
Date: Thu, 15 Jun 2023 11:30:45 GMT
Server: Kestrel
Transfer-Encoding: chunked
api-supported-versions: 1.0`
- **Тело ответа** 
```
[
    {
        "id": 1, 
        "userName": "User 1", 
        "password": "Password1"
    },
                  ...
    {
        "id": 10, 
        "userName": "User 10", 
        "password": "Password10"
    }
]
```

## 2) 5.2 Users : обновление данных пользователя под id:7 * POST ​/api​/v1​/Users 200 OK
- **URL:**  https://fakerestapi.azurewebsites.net/api/v1/Users
- **Ожидаемый результат:** код HTTPS ответа: `200 - Success` - успешное обновление данных пользователя под id:7
- **Заголовки запроса:** 
` Content-Type: application/json
User-Agent: PostmanRuntime/7.32.3
Accept: */*
Cache-Control: no-cache
Postman-Token: 545210f2-1162-48a0-8c2c-1109ece6abd4
Host: fakerestapi.azurewebsites.net
Accept-Encoding: gzip, deflate, br
Connection: keep-alive `
- **Тело запроса:** 
```
{
  "id": 7,
  "userName": "7",
  "password": "7"
}
```
- **Заголовки ответа:**
`Content-Type: application/json; charset=utf-8; v=1.0
Date: Thu, 15 Jun 2023 14:47:30 GMT
Server: Kestrel
Transfer-Encoding: chunked
api-supported-versions: 1.0`
- **Тело ответа:** 
```
{
  "id": 7,
  "userName": "7",
  "password": "7"
}
```
## 3) 5.2 Users : обновление данных пользователя под invalid id * POST ​/api​/v1​/Users 400 surpass
- **URL:**  https://fakerestapi.azurewebsites.net/api/v1/Users
- **Ожидаемый результат:** код HTTPS ответа: `400 - Error: Bad Request` - данные не могут быть обработаны
- **Заголовки запроса:** 
`Content-Type: application/json
User-Agent: PostmanRuntime/7.32.3
Accept: */*
Cache-Control: no-cache
Postman-Token: 2be5e535-bb8f-4ab8-b15a-4f9fc87a791d
Host: fakerestapi.azurewebsites.net
Accept-Encoding: gzip, deflate, br
Connection: keep-alive`
- **Тело запроса:** 
```
{
  "id": 0,
  "userName": "string",
  "password": "string"
}
```
- **Заголовки ответа:**
`Content-Type: application/problem+json; charset=utf-8
Date: Thu, 15 Jun 2023 14:48:27 GMT
Server: Kestrel
Transfer-Encoding: chunked`
- **Тело ответа:** 
```
{
    "type": "https://tools.ietf.org/html/rfc7231#section-6.5.1",
    "title": "One or more validation errors occurred.",
    "status": 400,
    "traceId": "00-3cb5da0bde6cde4899f8548891a6268f-3c3ba4ee2f0c8744-00",
    "errors": {
        "$.id": [
            "The JSON value could not be converted to System.Int32. Path: $.id | LineNumber: 1 | BytePositionInLine: 18."
        ]
    }
}
```
## 4) 5.2. Users : создание данных пользователя под id:11 * POST ​/api​/v1​/Users 201 none (bug)
- **URL:**  https://fakerestapi.azurewebsites.net/api/v1/Users
- **Ожидаемый результат:** код HTTPS ответа -> `201 - Created` - создание данных пользователя под id:11
- **Заголовки запроса:** 
`Content-Type: application/json
User-Agent: PostmanRuntime/7.32.3
Accept: */*
Cache-Control: no-cache
Postman-Token: bbdf14be-97ce-46a2-8dfe-951c93182e3e
Host: fakerestapi.azurewebsites.net
Accept-Encoding: gzip, deflate, br
Connection: keep-alive`
- **Тело запроса:** 
```
{
  "id": 11,
  "userName": "11",
  "password": "11"
}
```
- **Заголовки ответа:**
`Content-Type: application/json; charset=utf-8; v=1.0
Date: Thu, 15 Jun 2023 14:46:40 GMT
Server: Kestrel
Transfer-Encoding: chunked
api-supported-versions: 1.0`
- **Тело ответа:** 
```
{
  "id": 11,
  "userName": "11",
  "password": "11"
}
```
## 5) 5.2 Users : обновление данных пользователя под id в теле * POST ​/api​/v1​/Users 400 symbol
- **URL:**  https://fakerestapi.azurewebsites.net/api/v1/Users
- **Ожидаемый результат:** код HTTPS ответа: `400 - Error: Bad Request` - введенное значение не может быть обработано, а обновления не могут быть применены
- **Заголовки запроса:** 
`Content-Type: application/json
User-Agent: PostmanRuntime/7.32.3
Accept: */*
Cache-Control: no-cache
Postman-Token: 11ab20ac-0c61-4f30-8830-c5908e048e83
Host: fakerestapi.azurewebsites.net
Accept-Encoding: gzip, deflate, br
Connection: keep-alive`
- **Тело запроса:** 
```
{
  "id": 0,
  "userName": "string",
  "password": "string"
}
```
- **Заголовки ответа:**
`Content-Type: application/problem+json; charset=utf-8
Date: Thu, 15 Jun 2023 14:51:12 GMT
Server: Kestrel
Transfer-Encoding: chunked`
- **Тело ответа:** 
```
{
    "type": "https://tools.ietf.org/html/rfc7231#section-6.5.1",
    "title": "One or more validation errors occurred.",
    "status": 400,
    "traceId": "00-e90de062d7dcae4e81f2a8dca0e3d995-c9970ef29138d04b-00",
    "errors": {
        "$.id": [
            "'@' is invalid within a number, immediately after a sign character ('+' or '-'). Expected a digit ('0'-'9'). Path: $.id | LineNumber: 1 | BytePositionInLine: 9."
        ]
    }
}
```
## 6) 5.2 Users : обновление данных пользователя без тела * POST ​/api​/v1​/Users 400 null body 
- **URL:**  https://fakerestapi.azurewebsites.net/api/v1/Users
- **Ожидаемый результат:** код HTTPS ответа: `400 - Error: Bad Request` - нет (содержания) тела запроса
- **Заголовки запроса:** 
`Content-Type: application/json
User-Agent: PostmanRuntime/7.32.3
Accept: */*
Cache-Control: no-cache
Postman-Token: e9471683-e95a-4176-b26d-3d26b399a57f
Host: fakerestapi.azurewebsites.net
Accept-Encoding: gzip, deflate, br
Connection: keep-alive`
- **Тело запроса:** `удалено`
- **Заголовки ответа:**
`Content-Type: application/problem+json; charset=utf-8
Date: Thu, 15 Jun 2023 14:52:47 GMT
Server: Kestrel
Transfer-Encoding: chunked`
- **Тело ответа:** 
```
{
    "type": "https://tools.ietf.org/html/rfc7231#section-6.5.1",
    "title": "One or more validation errors occurred.",
    "status": 400,
    "traceId": "00-4f7056506dc7ca42b0168eb284622e94-d8a53404856c2e40-00",
    "errors": {
        "": [
            "A non-empty request body is required."
        ]
    }
}
```
## 7) 5.2. Users : обновление данных пользователя под id:-7 * POST ​/api​/v1​/Users 400 neg. (bug)
- **URL:**  https://fakerestapi.azurewebsites.net/api/v1/Users
- **Ожидаемый результат:** код HTTPS ответа: `400 - Error: Bad Request` - запрос с отрицательным значением id пользователя не обрабатывается сервером
- **Заголовки запроса:** 
`Content-Type: application/json
User-Agent: PostmanRuntime/7.32.3
Accept: */*
Cache-Control: no-cache
Postman-Token: a007d7ae-cfb4-41e8-bc84-0070d72880f0
Host: fakerestapi.azurewebsites.net
Accept-Encoding: gzip, deflate, br
Connection: keep-alive`
- **Тело запроса:** 
```
{
    "id": -7,
    "userName": "string",
    "password": "string"
}
```
- **Заголовки ответа:**
`Content-Type: application/json; charset=utf-8; v=1.0
Date: Thu, 15 Jun 2023 20:38:27 GMT
Server: Kestrel
Transfer-Encoding: chunked
api-supported-versions: 1.0`
- **Тело ответа:** 
```
{
    "id": -7,
    "userName": "string",
    "password": "string"
}
```

## 8) 5.3 Users : получение данных пользователя под id:7 * GET ​/api​/v1​/Users​/{id} 200 OK
- **URL:** https://fakerestapi.azurewebsites.net/api/v1/Users/{{user_ok}}
- **Ожидаемый результат:** код HTTPS ответа: `200 Success` - успешное получениe ответа с данными пользователя под id:7 (username, password) 
- **Заголовки запроса:** 
`Content-Type: application/json
User-Agent: PostmanRuntime/7.32.3
Accept: */*
Cache-Control: no-cache
Postman-Token: 1f9bd674-6397-4418-bb24-b62f1f4c227f
Host: fakerestapi.azurewebsites.net
Accept-Encoding: gzip, deflate, br
Connection: keep-alive`
- **Тело запроса:** `-`
- **Заголовки ответа:**
`Content-Type: application/problem+json; charset=utf-8
Date: Thu, 15 Jun 2023 13:52:13 GMT
Server: Kestrel
Transfer-Encoding: chunked`
- **Тело ответа:** 
```
{
    "id": 7,
    "userName": "User 7",
    "password": "Password7"
}
```
## 9) 5.3 Users : получение данных пользователя под invalid id *GET ​/api​/v1​/Users​/{id} 400 surpass
- **URL:** https://fakerestapi.azurewebsites.net/api/v1/Users/{{user_surpass}}
- **Ожидаемый результат:** код HTTPS ответа: `400 - Error: Bad Request` - введенное значение id невалидное 
- **Заголовки запроса:** 
`User-Agent: PostmanRuntime/7.32.3
Accept: */*
Cache-Control: no-cache
Postman-Token: 8caa2fa3-49be-4e57-8e38-2d0c1fdb1685
Host: fakerestapi.azurewebsites.net
Accept-Encoding: gzip, deflate, br
Connection: keep-alive`
- **Тело запроса:** `-`
- **Заголовки ответа:**
`Content-Type: application/problem+json; charset=utf-8; v=1.0
Date: Thu, 15 Jun 2023 13:46:50 GMT
Server: Kestrel
Transfer-Encoding: chunked`
- **Тело ответа:** 
```
{
    "type": "https://tools.ietf.org/html/rfc7231#section-6.5.1",
    "title": "One or more validation errors occurred.",
    "status": 400,
    "traceId": "00-0e7807c2db36cf49bd41660a6c13c10d-36cc6afabe579343-00",
    "errors": {
        "id": [
            "The value '2147483648' is not valid."
        ]
    }
}
```
## 10) 5.3 Users : получение данных пользователя под id:11 * GET ​/api​/v1​/Users​/{id} 404 none 
- **URL:** https://fakerestapi.azurewebsites.net/api/v1/Users/{{user_none}}
- **Ожидаемый результат:** код HTTPS ответа: `404 - Error: Not Found` - пользователь под id:11 не найден  
- **Заголовки запроса:** 
`User-Agent: PostmanRuntime/7.32.3
Accept: */*
Cache-Control: no-cache
Postman-Token: e6ceee64-34f0-483a-af49-1da888e3739b
Host: fakerestapi.azurewebsites.net
Accept-Encoding: gzip, deflate, br
Connection: keep-alive`
- **Тело запроса:** `-`
- **Заголовки ответа:**
`Content-Type: application/problem+json; charset=utf-8; v=1.0
Date: Thu, 15 Jun 2023 13:47:20 GMT
Server: Kestrel
Transfer-Encoding: chunked
api-supported-versions: 1.0`
- **Тело ответа:** 
```
{
    "type": "https://tools.ietf.org/html/rfc7231#section-6.5.4",
    "title": "Not Found",
    "status": 404,
    "traceId": "00-8b4fe036dab3444499dc7edfed8646d6-ce9b72f616a1894c-00"
}
```
## 11) 5.3 Users : получение данных пользователя под id:-7 * GET ​/api​/v1​/Users​/{id} 404 neg.  
- **URL:** https://fakerestapi.azurewebsites.net/api/v1/Users/{{user_neg.}}
- **Ожидаемый результат:** код HTTPS ответа: `404 - Error: Not Found` - неприемлиемое значение параметра
- **Заголовки запроса:** 
`User-Agent: PostmanRuntime/7.32.3
Accept: */*
Cache-Control: no-cache
Postman-Token: e6ceee64-34f0-483a-af49-1da888e3739b
Host: fakerestapi.azurewebsites.net
Accept-Encoding: gzip, deflate, br
Connection: keep-alive`
- **Тело запроса:** `-`
- **Заголовки ответа:**
`Content-Type: application/problem+json; charset=utf-8; v=1.0
Date: Thu, 15 Jun 2023 13:47:20 GMT
Server: Kestrel
Transfer-Encoding: chunked
api-supported-versions: 1.0`
- **Тело ответа:** 
```
{
    "type": "https://tools.ietf.org/html/rfc7231#section-6.5.4",
    "title": "Not Found",
    "status": 404,
    "traceId": "00-8b4fe036dab3444499dc7edfed8646d6-ce9b72f616a1894c-00"
}
```

## 12) 5.4 Users : изменение данных старого пользователя под id:7 *PUT ​/api​/v1​/Users​/{id} 200 OK
- **URL:**  https://fakerestapi.azurewebsites.net/api/v1/Users/{{user_ok}}
- **Ожидаемый результат:** код HTTPS ответа: `200 - Success` - успешное обновление данных пользователя под id:7
- **Заголовки запроса:** 
`Content-Type: application/json
User-Agent: PostmanRuntime/7.32.3
Accept: */*
Cache-Control: no-cache
Postman-Token: 050e57b1-4762-4c7a-aabe-5e1a1e0702c2
Host: fakerestapi.azurewebsites.net
Accept-Encoding: gzip, deflate, br
Connection: keep-alive`
- **Тело запроса:** 
```
{
    "id": 7,
    "userName": "7",
    "password": "7"
}
```
- **Заголовки ответа:**
`Content-Type: application/json; charset=utf-8; v=1.0
Date: Thu, 15 Jun 2023 13:50:54 GMT
Server: Kestrel
Transfer-Encoding: chunked
api-supported-versions: 1.0`
- **Тело ответа:** 
```
{
    "id": 7,
    "userName": "7",
    "password": "7"
}
```
## 13) 5.4 Users : изменение данных пользователя под invalid id *PUT ​/api​/v1​/Users​/{id} 400 surpass
- **URL:**  https://fakerestapi.azurewebsites.net/api/v1/Users/{{user_surpass}}
- **Ожидаемый результат:** код HTTPS ответа: `400 - Error: Bad Request` - введенное значение id невалидное
- **Заголовки запроса:** 
`Content-Type: application/json
User-Agent: PostmanRuntime/7.32.3
Accept: */*
Cache-Control: no-cache
Postman-Token: 1f9bd674-6397-4418-bb24-b62f1f4c227f
Host: fakerestapi.azurewebsites.net
Accept-Encoding: gzip, deflate, br
Connection: keep-alive`
- **Тело запроса:** 
```
{
  "id": 0,
  "userName": "string",
  "password": "string"
}
```
- **Заголовки ответа:**
`Content-Type: application/problem+json; charset=utf-8
Date: Thu, 15 Jun 2023 13:52:13 GMT
Server: Kestrel
Transfer-Encoding: chunked`
- **Тело ответа:** 
```
{
    "type": "https://tools.ietf.org/html/rfc7231#section-6.5.1",
    "title": "One or more validation errors occurred.",
    "status": 400,
    "traceId": "00-e54e9536bedd8c429057fc39e78a2408-6e937e3a50eaf246-00",
    "errors": {
        "id": [
            "The value '2147483648' is not valid."
        ]
    }
}
```
## 14) 5.4. Users : внесение данных нового пользователя под id:11 * PUT ​/api​/v1​/Users​/{id} 201 none (bug)
- **URL:**  https://fakerestapi.azurewebsites.net/api/v1/Users/{{user_none}}
- **Ожидаемый результат:** код HTTPS ответа -> `201 - Created` - изменение данных пользователя под id:11
- **Заголовки запроса:** 
`Content-Type: application/json
User-Agent: PostmanRuntime/7.32.3
Accept: */*
Cache-Control: no-cache
Postman-Token: 545210f2-1162-48a0-8c2c-1109ece6abd4
Host: fakerestapi.azurewebsites.net
Accept-Encoding: gzip, deflate, br
Connection: keep-alive`
- **Тело запроса:** 
```
{
    "id": 11,
    "userName": "11",
    "password": "11"
}
```
- **Заголовки ответа:**
`Content-Type: application/json; charset=utf-8; v=1.0
Date: Thu, 15 Jun 2023 13:50:54 GMT
Server: Kestrel
Transfer-Encoding: chunked
api-supported-versions: 1.0`
- **Тело ответа:** 
```
{
    "id": 11,
    "userName": "11",
    "password": "11"
}
```
## 15) 5.4 Users : изменение данных пользователя под id в теле * PUT ​/api​/v1​/Users​/{id} 400 symbol
- **URL:**  https://fakerestapi.azurewebsites.net/api/v1/Users/{{user_symbol}}
- **Ожидаемый результат:** код HTTPS ответа: `400 - Error: Bad Request` - введенное значение не может быть обработано, а изменения не могут быть внесены
- **Заголовки запроса:** 
`Content-Type: application/json
User-Agent: PostmanRuntime/7.32.3
Accept: */*
Cache-Control: no-cache
Postman-Token: cbd6bbb0-004a-47fb-add0-7b0e320090be
Host: fakerestapi.azurewebsites.net
Accept-Encoding: gzip, deflate, br
Connection: keep-alive`
- **Тело запроса:** 
```
{
  "id": 0,
  "userName": "string",
  "password": "string"
}
```
- **Заголовки ответа:**
`Content-Type: application/problem+json; charset=utf-8
Date: Thu, 15 Jun 2023 13:56:02 GMT
Server: Kestrel
Transfer-Encoding: chunked`
- **Тело ответа:** 
```
{
    "type": "https://tools.ietf.org/html/rfc7231#section-6.5.1",
    "title": "One or more validation errors occurred.",
    "status": 400,
    "traceId": "00-4df5c669c891e64db00883572bd33b0a-24e6630ee074a54f-00",
    "errors": {
        "id": [
            "The value '-@' is not valid."
        ]
    }
}
```
## 16) 5.4 Users : изменение данных пользователя без тела * PUT ​/api​/v1​/Users​/{id} 400 null body
- **URL:**  https://fakerestapi.azurewebsites.net/api/v1/Users/{{user_null}}
- **Ожидаемый результат:** код HTTPS ответа: `400 - Error: Bad Request` - нет (содержания) тела запроса
- **Заголовки запроса:** 
`Content-Type: application/json
User-Agent: PostmanRuntime/7.32.3
Accept: */*
Cache-Control: no-cache
Postman-Token: 81372e41-54d1-4e03-bb3d-62ef99ad4549
Host: fakerestapi.azurewebsites.net
Accept-Encoding: gzip, deflate, br
Connection: keep-alive`
- **Тело запроса:** `удалено`
- **Заголовки ответа:**
`Content-Type: application/json; charset=utf-8; v=1.0
Date: Thu, 15 Jun 2023 13:57:15 GMT
Server: Kestrel
Transfer-Encoding: chunked`
- **Тело ответа:** 
```
{
    "type": "https://tools.ietf.org/html/rfc7231#section-6.5.1",
    "title": "One or more validation errors occurred.",
    "status": 400,
    "traceId": "00-e9248a587d79674aa4c21edbcabd6a82-c4cd664a33103049-00",
    "errors": {
        "": [
            "A non-empty request body is required."
        ]
    }
}
```
## 17) 5.4. Users : изменение данных пользователя под id:-7 * PUT ​/api​/v1​/Users​/{id} 400 neg. (bug)
- **URL:**  https://fakerestapi.azurewebsites.net/api/v1/Users/{{user_neg.}}
- **Ожидаемый результат:** код HTTPS ответа: `400 - Error: Bad Request` - запрос с отрицательным значением id пользователя не обрабатывается сервером 
- **Заголовки запроса:** 
`Content-Type: application/json
User-Agent: PostmanRuntime/7.32.3
Accept: */*
Cache-Control: no-cache
Postman-Token: e7e6cba9-cabb-4d5d-b756-6d18a8ca0d0c
Host: fakerestapi.azurewebsites.net
Accept-Encoding: gzip, deflate, br
Connection: keep-alive`
- **Тело запроса:** 
```
{
    "id": -7,
    "userName": "string",
    "password": "string"
}
```
- **Заголовки ответа:**
`Content-Type: application/json; charset=utf-8; v=1.0
Date: Thu, 15 Jun 2023 13:58:07 GMT
Server: Kestrel
Transfer-Encoding: chunked
api-supported-versions: 1.0`
- **Тело ответа:** 
```
{
    "id": -7,
    "userName": "string",
    "password": "string"
}
```

## 18) 5.5 Users : удаление пользователя под id:7 * DELETE ​/api​/v1​/Users​/{id} 200 OK 
- **URL:**  https://fakerestapi.azurewebsites.net/api/v1/Users/{{user_ok}}
- **Ожидаемый результат:** код HTTPS ответа: `200 - Success` - успешное удаление пользователя под id:7
- **Заголовки запроса:** 
`User-Agent: PostmanRuntime/7.32.3
Accept: */*
Cache-Control: no-cache
Postman-Token: 3e121546-aa7d-4c96-b745-bde1e92369c4
Host: fakerestapi.azurewebsites.net
Accept-Encoding: gzip, deflate, br
Connection: keep-alive`
- **Тело запроса:** `-`
- **Заголовки ответа:**
`Content-Length: 0
Date: Thu, 15 Jun 2023 14:00:14 GMT
Server: Kestrel
api-supported-versions: 1.0`
- **Тело ответа:** `-`
## 19) 5.5 Users : удаление пользователя под invalid id * DELETE ​/api​/v1​/Users​/{id} 400 surpass 
- **URL:**  https://fakerestapi.azurewebsites.net/api/v1/Users/{{user_surpass}}
- **Ожидаемый результат:** код HTTPS ответа: `400 - Error: Bad Request` - введенное значение id невалидное
- **Заголовки запроса:** 
`User-Agent: PostmanRuntime/7.32.3
Accept: */*
Cache-Control: no-cache
Postman-Token: 7c541dd3-39cf-470a-8912-423adbfd9f30
Host: fakerestapi.azurewebsites.net
Accept-Encoding: gzip, deflate, br
Connection: keep-alive`
- **Тело запроса:** `-`
- **Заголовки ответа:**
`Content-Length: 0
Date: Thu, 15 Jun 2023 14:02:34 GMT
Server: Kestrel
api-supported-versions: 1.0`
- **Тело ответа:** 
```
{
    "type": "https://tools.ietf.org/html/rfc7231#section-6.5.1",
    "title": "One or more validation errors occurred.",
    "status": 400,
    "traceId": "00-55cf97c208271f439a2dd54f3ad6f167-a26e32fbbe2ff148-00",
    "errors": {
        "id": [
            "The value '2147483648' is not valid."
        ]
    }
}
```
## 20) 5.5. Users : удаление пользователя под id:11 * DELETE ​/api​/v1​/Users​/{id} 404 none (bug)
- **URL:**  https://fakerestapi.azurewebsites.net/api/v1/Users/{{user_none}}
- **Ожидаемый результат:** код HTTPS ответа -> `404 - Error: Not Found` - пользователь под id:11 не найден
- **Заголовки запроса:** 
`User-Agent: PostmanRuntime/7.32.3
Accept: */*
Cache-Control: no-cache
Postman-Token: 7c541dd3-39cf-470a-8912-423adbfd9f30
Host: fakerestapi.azurewebsites.net
Accept-Encoding: gzip, deflate, br
Connection: keep-alive`
- **Тело запроса:** `-`
- **Заголовки ответа:**
`Content-Length: 0
Date: Thu, 15 Jun 2023 14:20:36 GMT
Server: Kestrel
api-supported-versions: 1.0`
- **Тело ответа:** `-`
## 21) 5.5. Users : удаление пользователя под id:-7 * DELETE ​/api​/v1​/Users​/{id} 400 neg. (bug)
- **URL:**  https://fakerestapi.azurewebsites.net/api/v1/Users/{{user_neg.}}
- **Ожидаемый результат:** код HTTPS ответа -> `400 - Error: Bad Request` - запрос с отрицательным значением id пользователя не обрабатывается сервером 
- **Заголовки запроса:** 
`User-Agent: PostmanRuntime/7.32.3
Accept: */*
Cache-Control: no-cache
Postman-Token: 7c541dd3-39cf-470a-8912-423adbfd9f30
Host: fakerestapi.azurewebsites.net
Accept-Encoding: gzip, deflate, br
Connection: keep-alive`
- **Тело запроса:** `-`
- **Заголовки ответа:**
`Content-Length: 0
Date: Thu, 15 Jun 2023 14:20:36 GMT
Server: Kestrel
api-supported-versions: 1.0`
- **Тело ответа:** `-`
