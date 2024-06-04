## SQL-запросы:
## Ограничение выборки
1. Вывод первых 20-ти записей из таблицы `track`. Итоговая таблица содержит только два поля: `name` и `unit_price`.

```
SELECT name,
       unit_price
FROM track
LIMIT 20 OFFSET 0;

```

## Изменение типов данных
1. Выгрузка из таблицы `track` полей `milliseconds` и `bytes` в формате строк.

```
SELECT
       CAST (bytes AS varchar),
       CAST (milliseconds AS varchar)
FROM track;

```

2. Выгрузка из таблицы `invoice` поля `total` в формате целого числа.

```
SELECT CAST(total AS integer)
FROM invoice;

```

3. Выгрузка из таблицы `staff` дат дней рождения сотрудников.

```
SELECT CAST (birth_date AS date)
FROM staff;

```

## Срез данных с помощью оператора WHERE
1. Фильтрация значений таблицы `invoice_line`, где треки дороже 0.99.

```
SELECT *
FROM invoice_line
WHERE unit_price > 0.99;

```

2. Вывод записей только о тех покупателях, которые живут в Бразилии.

```
SELECT first_name,
       last_name,
       city
FROM client
WHERE country = 'Brazil'

```
3. Вывод даты, где и когда совершали самые крупные покупки. Фильтрация записей, где значение поля `total` больше или равно 8.

```
SELECT billing_address,
       CAST(invoice_date AS date )
FROM invoice
WHERE total >= 8;

```

## Срез данных с помощью логических операторов

1. Фильтрация данных о счетах в трёх городах: Дублине, Лондоне или Париже. Значение `total` должно быть больше или равно 5, а значение `customer_id` должно равняться 40 или 46.

```
SELECT total,
       customer_id
FROM invoice
WHERE (billing_city = 'Dublin'
     OR billing_city = 'London'
     OR billing_city = 'Paris')
     AND total >= 5
     AND (customer_id = 40
     OR customer_id = 46);

```

2. Выгрузка названий фильмов из таблицы `movie`, стоимость аренды которых не превышает двух долларов, а срок аренды составляет больше шести дней. Выгруженные фильмы не должны относиться к рейтингам PG и PG-13.

```
SELECT title
FROM movie
WHERE rental_rate <= 2
     AND rental_duration > 6
     AND NOT rating = 'PG'
     AND NOT rating = 'PG-13';

```
3. Выгрузка адресов и городов оформления заказов, сделанных в сентябре 2009 года. Данные о заказах должны быть, оформлены во всех странах, кроме США и Бразилии. Стоимость заказа должна быть больше двух долларов.

```
SELECT billing_address,
       billing_city
FROM invoice
WHERE invoice_date BETWEEN '2009-09-01 00:00:00' AND '2009-09-30 00:00:00'
AND NOT (billing_country = 'USA'
OR billing_country = 'Brazil')
AND total > 2;

```

## Операторы IN, LIKE, BETWEEN

1.Выгрузка из таблицы все названия плейлистов, в которых есть подстрока `Classic`.

```
SELECT name
FROM playlist
WHERE name LIKE '%Classic%'

```
