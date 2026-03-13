---
title: API Contracts
---

## Базовый URL

```
https://api.bank.internal/v1
```

## Аутентификация

Все запросы требуют заголовка `Authorization: Bearer <token>`.

## Эндпоинты

### POST /payments

Инициировать платёж.

**Request body:**

```json
{
  "amount": 1000,
  "currency": "RUB",
  "recipient_account": "40817810...",
  "description": "Оплата услуги"
}
```

**Response:**

```json
{
  "transaction_id": "txn_abc123",
  "status": "PENDING",
  "created_at": "2026-03-11T10:00:00Z"
}
```

### GET /payments/:id

Получить статус транзакции.

## Коды ошибок

| Код | Описание |
|-----|----------|
| 400 | Неверные параметры запроса |
| 401 | Не авторизован |
| 404 | Транзакция не найдена |
| 422 | Недостаточно средств |
| 500 | Внутренняя ошибка сервера |
