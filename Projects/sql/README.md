## SQL-запросы:
[- Ограничение выборки](#ограничение-выборки)<br>
[- Изменение типов данных](#изменение-типов-данных)<br>
## Ограничение выборки
1. Выгрузка из таблицы `client` поля `email`, `first_name`, `last_name`.

```
SELECT email,
       first_name,
       last_name
FROM client
```

2. Выгрузка первых четырех полей из таблицы `invoice`. Ограничение выгрузки первыми пятью записями.

```
SELECT invoice_id,
       customer_id,
       invoice_date,
       billing_address
FROM invoice
LIMIT 5  OFFSET 0;
```
3.Вывод первых 20-ти записей из таблицы `track`. Итоговая таблица должна содержать только два поля: `name` и `unit_price`.

```
SELECT name,
       unit_price
FROM track
LIMIT 20 OFFSET 0;

```

## Изменение типов данных
1. Выгрузка из таблицы `track` полей `milliseconds` и `bytes`. Оба поля должны быть строками. Использование типа данных для строк нефиксированной длины.

```
SELECT
       CAST (bytes AS varchar),
       CAST (milliseconds AS varchar)
FROM track;

```

2.Выгрузка из таблицы `invoice` поля `total`. Должна остаться только целая часть числа.

```
SELECT CAST(total AS integer)
FROM invoice;

```

3.Выгрузка из таблицы `staff` дней рождения сотрудников. На экране должна отобразиться только дата.

```
SELECT CAST (birth_date AS date)
FROM staff;

```

## Срез данных с помощью оператора WHERE
