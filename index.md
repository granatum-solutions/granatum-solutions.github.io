# Granatum API

## Авторизация
Для авторизации необходимо посылать "Ключ API" с каждым запросом в заголовке **Authorization**
```
Authorization: {api_key}
```

## OpenAPI спецификация
[Swagger-UI](/swagger)  
[openapi.yaml](https://raw.githubusercontent.com/granatum-solutions/granatum-solutions.github.io/master/swagger/openapi.yaml)

# Авторизация

## Создать новый аккаунт
#### Запрос
Дополнительные поля можно послать внутри объекта **additionalProperties**  
**POST /registration**
```json
{
  "email": "string",
  "externalId": "string",
  "additionalProperties": {}
}
```
#### Ответ
```json
{
  "email": "string",
  "password": "string"
}
```

# Статистика
## Получить список всех пользователей
#### Запрос
**GET /users**
#### Ответ
```json
[
  {
    "email": "string",
    "externalId": "string",
    "active": true,
    "role": "USER",
    "additionalProperties": {}
  }
]
```

## Получить список всех курсов
#### Запрос
**GET /courses**
#### Ответ
```json
[
  {
    "id": "string",
    "name": "string"
  }
]
```

## Прогресс пользователей курса
#### Запрос
**GET /courses/{id}/users**
#### Ответ
```json
[
  {
    "email": "string",
    "sessions": [
      {
        "id": "string",
        "name": "string",
        "averageScore": 0
      }
    ]
  }
]
```
## Получить список сессий курса
#### Запрос
**GET /courses/{id}/sessions**
#### Ответ
```json
[
  {
    "id": "string",
    "name": "string",
    "description": "string",
    "courseId": "string",
    "startDate": "2020-10-19T17:49:45.632Z"
  }
]
```
## Получить список пользователей курса
#### Запрос
**GET /courses/{id}/users**
#### Ответ
```json
[
  {
    "email": "string",
    "externalId": "string",
    "active": true,
    "role": "USER",
    "additionalProperties": {}
  }
]
```
## Результаты прохождения тестов в сессии
#### Запрос
**GET /sessions/{id}/results**
#### Ответ
```json
[
  {
    "email": "string",
    "attempts": 0,
    "score": 0
  }
]
```
## Получить список пользователей сессии
#### Запрос
**GET /sessions/{id}/users**
#### Ответ
```json
[
  {
    "email": "string",
    "externalId": "string",
    "active": true,
    "role": "USER",
    "additionalProperties": {}
  }
]
```