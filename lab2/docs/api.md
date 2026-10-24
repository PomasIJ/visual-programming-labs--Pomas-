# API Documentation — Lab 2 (Помас)

Все эндпоинты доступны по базовому URL: `http://localhost:1880`

## 1. GET /api/text

Возвращает простой текст.

**Запрос:**
```
GET http://localhost:1880/api/text
```

**Ответ (200):**
```
Привет! Это простой текст от Помас
```

---

## 2. GET /api/info

Возвращает JSON с информацией о студенте.

**Запрос:**
```
GET http://localhost:1880/api/info
```

**Ответ (200):**
```json
{
  "name": "Помас",
  "group": "ВП",
  "year": 2026
}
```

---

## 3. GET /api/items/:id

Возвращает элемент по ID. Проверяет корректность параметра.

**Параметры:**
- `id` (path parameter) — числовой идентификатор элемента.

**Успешный запрос:**
```
GET http://localhost:1880/api/items/5
```

**Ответ (200):**
```json
{
  "id": "5",
  "name": "Item #5",
  "available": true
}
```

**Ошибка — не число:**
```
GET http://localhost:1880/api/items/abc
```

**Ответ (400):**
```json
{
  "error": "ID must be a number"
}
```

**Ошибка — ID > 100:**
```
GET http://localhost:1880/api/items/500
```

**Ответ (404):**
```json
{
  "error": "Item not found"
}
```
