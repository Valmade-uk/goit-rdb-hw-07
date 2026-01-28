# Relational Databases: Concepts and Techniques

## Тема завдання  
**Додаткові вбудовані SQL функції. Робота з часом та JSON** (MySQL).

## Структура репозиторію

```
goit-rdb-hw-05/
│
├── task_1/                # вкладений запит в операторі SELECT
├── task_2/                # вкладений запит в операторі WHERE
├── task_3/                # вкладений запит в операторі FROM
├── task_4/                # вкладений запит з використанням оператора WITH (CTE)
├── task_5/                # створення функції ділення з двома параметрами типу FLOAT
└── README.md
```
---

## Завдання та SQL-запити

### task_1 — Витягнути рік, місяць і число з `orders.date`
```sql
SELECT
  id,
  date,
  YEAR(date)  AS year,
  MONTH(date) AS month,
  DAY(date)   AS day
FROM orders;
```

### task_2 — Додати 1 день до `orders.date`
```sql
SELECT
  id,
  date,
  DATE_ADD(date, INTERVAL 1 DAY) AS date_plus_1_day
FROM orders;
```

### task_3 — Timestamp (секунди з початку епохи) для `orders.date`
```sql
SELECT
  id,
  date,
  UNIX_TIMESTAMP(date) AS unix_timestamp
FROM orders;
```

### task_4 — Порахувати кількість рядків у діапазоні дат
```sql
SELECT
  COUNT(*) AS count_rows
FROM orders
WHERE date BETWEEN '1996-07-10 00:00:00' AND '1996-10-08 00:00:00';
```

### task_5 — JSON-об’єкт `{"id": ..., "date": ...}` для кожного рядка
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
