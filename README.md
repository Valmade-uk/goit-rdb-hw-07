# goit-rdb-hw-07

Домашнє завдання №7 — **Додаткові вбудовані SQL функції. Робота з часом та JSON** (MySQL).

## Структура репозиторію
- `hw07.sql` — SQL-код до всіх пунктів (p1–p5)
- `screenshots/` — скріншоти виконання запитів і результатів (p1_... p5_...)

## Завдання та SQL-запити

### p1 — Витягнути рік, місяць і число з `orders.date`
```sql
SELECT
  id,
  date,
  YEAR(date)  AS year,
  MONTH(date) AS month,
  DAY(date)   AS day
FROM orders;
```

### p2 — Додати 1 день до `orders.date`
```sql
SELECT
  id,
  date,
  DATE_ADD(date, INTERVAL 1 DAY) AS date_plus_1_day
FROM orders;
```

### p3 — Timestamp (секунди з початку епохи) для `orders.date`
```sql
SELECT
  id,
  date,
  UNIX_TIMESTAMP(date) AS unix_timestamp
FROM orders;
```

### p4 — Порахувати кількість рядків у діапазоні дат
```sql
SELECT
  COUNT(*) AS count_rows
FROM orders
WHERE date BETWEEN '1996-07-10 00:00:00' AND '1996-10-08 00:00:00';
```

### p5 — JSON-об’єкт `{"id": ..., "date": ...}` для кожного рядка
```sql
SELECT
  id,
  date,
  JSON_OBJECT('id', id, 'date', date) AS json_object
FROM orders;
```

## Примітки
- СУБД: **MySQL**
- Таблиця: `orders`
- Скриншоти пронумеровані відповідно до пунктів завдання
