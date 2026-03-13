---
title: DB Schema
---

## База данных

PostgreSQL 15. Схема `public`.

## Таблицы

### users

| Поле | Тип | Описание |
|------|-----|----------|
| id | UUID | Первичный ключ |
| phone | VARCHAR(20) | Номер телефона (уникальный) |
| email | VARCHAR(255) | Email адрес |
| kyc_status | ENUM | `PENDING`, `VERIFIED`, `REJECTED` |
| created_at | TIMESTAMPTZ | Дата создания |

### transactions

| Поле | Тип | Описание |
|------|-----|----------|
| id | UUID | Первичный ключ |
| user_id | UUID | FK → users.id |
| amount | NUMERIC(15,2) | Сумма в копейках |
| currency | CHAR(3) | ISO 4217 код валюты |
| status | ENUM | `PENDING`, `SUCCESS`, `FAILED`, `REFUNDED` |
| created_at | TIMESTAMPTZ | Дата создания |

## Индексы

```sql
CREATE INDEX idx_transactions_user_id ON transactions(user_id);
CREATE INDEX idx_transactions_status ON transactions(status);
CREATE INDEX idx_users_phone ON users(phone);
```
