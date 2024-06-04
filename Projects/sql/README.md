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

2. Выгрузка адресов и городов оформления заказов, сделанных в сентябре 2009 года. Данные о заказах должны быть, оформлены во всех странах, кроме США и Бразилии. Стоимость заказа должна быть больше двух долларов.

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

2. Выгрузка адреса и страны. Страны, которые входят: США, Индия, Канада, Аргентина и Франция. Города, которые не входят: Редмонд, Лион и Дели.

```
SELECT billing_address,
       billing_country
FROM invoice
WHERE billing_country IN ('USA',
                          'India',
                          'Canada',
                          'Argentina',
                          'France')
		  AND billing_city NOT IN ('Redmond',
                                  'Lyon',
                                  'Delhi');

```

3. Выгрузка всех полей из таблицы `invoice`. Выбор только тех заказов, которые были оформлены в период с '2009-03-04' по '2012-02-09' включительно. Сумма покупки должна быть меньше 5. Из запроса исключаются страны: Канада, Бразилия и Финляндия.

```
   SELECT *
FROM invoice
WHERE invoice_date BETWEEN '2009-03-04' AND '2012-02-22'
      AND total < 5
      AND billing_country NOT IN ('Canada',
                                 'Brazil',
                                 'Finland');
```

## Условная конструкция с оператором CASE
1. Выделение категории в таблице `staff`. Категории нужно выделить на основе значений в поле `title`.
> Если в `title` встречается слово `'IT'`, в новом поле будет отображена категория `'разработка'`.<br>
Если в `title` встречается слово `'Manager'` и нет слова `'IT'`, в новом поле отобразится категория `'отдел продаж'`.<br>
Если в `title` встречается слово `'Support'`, в новом поле появится категория `'поддержка'`.

```
   SELECT last_name,
       first_name,
       title,
      CASE 
          WHEN title LIKE '%IT%' THEN 'разработка'
          WHEN title LIKE '%Manager%' AND title NOT LIKE '%IT%' THEN 'отдел продаж'
          WHEN title LIKE '%Support%' THEN 'поддержка'
      END
FROM staff;

```

## Работа с пропусками
1. Выгрузка номеров альбомов, где треки длиннее 250000 миллисекунд и в названии которых есть слово Moon, но автор трека не указан.

 ```
SELECT album_id
FROM track
WHERE milliseconds > 250000
     AND name LIKE '%Moon%'
     AND composer IS NULL;

```
