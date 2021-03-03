# Granatum API
**Granatum Solutions** - Облачный сервис, объединяющий инструменты для интерактивного общения и 
групповой работы с методологией эффективного взаимодействия в онлайне.  
Мы предоставляем возможность самостоятельно создать интеграцию вашей системы с granatum,
а также получать данные об активности пользователей и обрабатывать их на своей стороне.  
**API открывается только по персональному запросу.**  
После открытия доступа к API, вам будет предоставлен секретный ключ.  
Для получения дополнительной информации обратитесь к клиент-менеджеру:
[info@granatum.solutions](mailto:info@granatum.solutions)  
## Авторизация
Для авторизации необходимо посылать "Ключ API" с каждым запросом в заголовке **Authorization**
```
Authorization: {api_key}
```
Запрос и ответ передается в формате JSON.
## OpenAPI спецификация
OpenAPI представляет собой формализованную спецификацию и полноценный фреймворк для описания, создания, использования и
визуализации веб-сервисов.  
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
  "additionalProperties": {},
  "coursePermissions": {
    "courseId": "USER",
    "anotherCourseId": "COURSE_ADMIN"
  }
}
```
#### Ответ
```json
{
  "email": "string",
  "password": "string"
}
```

## Сброс пароля
#### Запрос
**POST /reset**
```json
{
  "id": "userID"
}
```
#### Ответ
```json
{
  "id": "userID",
  "password": "new-password"
}

```

## Предоставление доступа к курсу

#### Запрос

**POST /courses/{id}/users**

```json
{
  "accountIds": [
    "userID1",
    "userID2"
  ],
  "role": "USER"
}
```

#### Ответ

**200 OK**

## Удаление пользователей из курса

#### Запрос

**DELETE /courses/{id}/users?userId=userID1&role=USER**

#### Ответ

**200 OK**


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