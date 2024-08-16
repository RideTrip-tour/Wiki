# API Documentation - RideTrip_tour

## Endpoints

### 1. **GET /v1/activities**
- **Summary**: Получение списка активностей
- **Описание**: Этот эндпоинт возвращает список всех доступных активностей. Можно фильтровать активности по местоположению через параметр запроса `loc`.
- **Параметры**:
  - `loc` (query, optional): ID локации, по которому фильтруются активности.
- **Ответы**:
  - `200 OK`: Успешный ответ с JSON массивом активностей.
  - `422 Validation Error`: Ошибка валидации запроса.

#### Пример успешного ответа:
```json
{
  "status": "success",
  "result": [
    {
      "id": 1,
      "name": "Activity 1"
    },
    {
      "id": 2,
      "name": "Activity 2"
    }
  ]
}
```

---

### 2. **GET /v1/activities/{activity_id}**
- **Summary**: Получение информации об активности
- **Описание**: Этот эндпоинт возвращает информацию о конкретной активности по её ID.
- **Параметры**:
  - `activity_id` (path, required): ID активности.
- **Ответы**:
  - `200 OK`: Успешный ответ с информацией о запрашиваемой активности.
  - `422 Validation Error`: Ошибка валидации запроса.

#### Пример успешного ответа:
```json
{
  "status": "success",
  "result": {
    "id": 1,
    "name": "Activity 1"
  }
}
```

---

### 3. **GET /v1/locations**
- **Summary**: Получение списка локаций
- **Описание**: Этот эндпоинт возвращает список всех доступных локаций. Можно фильтровать локации по активности через параметр запроса `act`.
- **Параметры**:
  - `act` (query, optional): ID активности, по которому фильтруются локации.
- **Ответы**:
  - `200 OK`: Успешный ответ с JSON массивом локаций.
  - `422 Validation Error`: Ошибка валидации запроса.

#### Пример успешного ответа:
```json
{
  "status": "success",
  "result": [
    {
      "id": 1,
      "name": "Location 1"
    },
    {
      "id": 2,
      "name": "Location 2"
    }
  ]
}
```

---

### 4. **GET /v1/locations/{location_id}**
- **Summary**: Получение информации о локации
- **Описание**: Этот эндпоинт возвращает информацию о конкретной локации по её ID.
- **Параметры**:
  - `location_id` (path, required): ID локации.
- **Ответы**:
  - `200 OK`: Успешный ответ с информацией о запрашиваемой локации.
  - `422 Validation Error`: Ошибка валидации запроса.

#### Пример успешного ответа:
```json
{
  "status": "success",
  "result": {
    "id": 1,
    "name": "Location 1"
  }
}
```

---

## Компоненты

### ActivityItemResultSchema
- **status** (string): Статус ответа
- **result** (ActivitySchema | null): Данные активности или `null`

### ActivityListResultSchemas
- **status** (string): Статус ответа
- **result** (array[ActivitySchema]): Список активностей

### LocationItemResultSchema
- **status** (string): Статус ответа
- **result** (LocationSchema | null): Данные локации или `null`

### LocationListResultSchemas
- **status** (string): Статус ответа
- **result** (array[LocationSchema]): Список локаций

### ActivitySchema
- **id** (integer): Идентификатор активности
- **name** (string): Название активности

### LocationSchema
- **id** (integer): Идентификатор локации
- **name** (string): Название локации

### HTTPValidationError
- **detail** (array[ValidationError]): Список ошибок валидации

### ValidationError
- **loc** (array[string]): Местоположение ошибки
- **msg** (string): Сообщение об ошибке
- **type** (string): Тип ошибки
