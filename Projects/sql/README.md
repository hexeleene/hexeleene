## SQL-запросы:
[- Ограничение выборки](#ограничение-выборки)
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
