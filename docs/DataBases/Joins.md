<sub>[Главная](../../index.md) / [Базы данных](README.md) / **JOIN's** </sub>

# SQL Join's

## Входные данные
Ниже приведены две таблицы:

### 1. Customers
```sql
+----------------+-------------+
| customer_name  | customer_id |
+----------------+-------------+
| John Smith     |           1 |
| Jane Doe       |           2 |
| Michael Johnson|           3 |
| Steve Rogers   |           4 |
+----------------+-------------+
```
``customer_id`` - первичный ключ.

### 2.Orders
```sql
+------------+------------+----------------+
| order_id   | order_date | customer_id    |
+------------+------------+----------------+
|          1 | 2020-01-01 |               1|
|          2 | 2020-02-01 |               2|
|          3 | 2020-03-01 |               3|
|          4 | 2020-04-01 |               1|
+------------+------------+----------------+
```
``order_id`` - первичный ключ. 
``customer_id`` - внешний ключ, который ссылается на столбец customer_id в таблице customers.

## Типы обхединений
В SQL существует несколько типов объединений, которые можно использовать для объединения данных из нескольких таблиц.

### INNER JOIN
Этот тип соединения возвращает только те строки, которые имеют совпадающие значения в обеих таблицах.<br><br>
Запрос.
```sql
SELECT * FROM customers
INNER JOIN orders
ON customers.customer_id = orders.customer_id;
```
Результат.
```sql
+----------------+-------------+------------+------------+
| customer_name  | customer_id | order_id   | order_date |
+----------------+-------------+------------+------------+
| John Smith     |           1 |          1 | 2020-01-01 |
| Jane Doe       |           2 |          2 | 2020-02-01 |
| Michael Johnson|           3 |          3 | 2020-03-01 |
+----------------+-------------+------------+------------+
```
### LEFT JOIN (или LEFT OUTER JOIN)
Этот тип объединения возвращает все строки из левой таблицы и совпадающие строки из правой таблицы. Если совпадений нет, то для столбцов правой таблицы будут возвращены значения NULL.<br><br>
Запрос.
```sql
SELECT * FROM customers
LEFT JOIN orders
ON customers.customer_id = orders.customer_id;
```
Результат.
```sql
+----------------+-------------+------------+------------+
| customer_name  | customer_id | order_id   | order_date |
+----------------+-------------+------------+------------+
| John Smith     |           1 |          1 | 2020-01-01 |
| Jane Doe       |           2 |          2 | 2020-02-01 |
| Michael Johnson|           3 |          3 | 2020-03-01 |
| Steve Rogers   |           4 |       NULL |     NULL   |
+----------------+-------------+------------+------------+
```
### RIGHT JOIN (или RIGHT OUTER JOIN)
Этот тип объединения возвращает все строки из правой таблицы и совпадающие строки из левой таблицы. Если совпадений нет, для столбцов левой таблицы возвращаются значения NULL.<br><br>
Запрос.
```sql
SELECT * FROM customers
RIGHT JOIN orders
ON customers.customer_id = orders.customer_id;
```
Результат.
```sql
+----------------+-------------+------------+------------+
| customer_name  | customer_id | order_id   | order_date |
+----------------+-------------+------------+------------+
| John Smith     |           1 |          1 | 2020-01-01 |
| Jane Doe       |           2 |          2 | 2020-02-01 |
| Michael Johnson|           3 |          3 | 2020-03-01 |
| Peter Parker   |       NULL  |          4 | 2020-04-01 |
+----------------+-------------+------------+------------+
```

### FULL JOIN (или FULL OUTER JOIN)
Этот тип объединения возвращает все строки из обеих таблиц, включая не совпадающие строки. Если совпадения нет, для несовпадающих столбцов будут возвращены значения NULL.<br><br>
Запрос.
```sql
SELECT * FROM customers
FULL JOIN orders
ON customers.customer_id = orders.customer_id;
```
Результат.
```sql
+----------------+-------------+------------+------------+
| customer_name  | customer_id | order_id   | order_date |
+----------------+-------------+------------+------------+
| John Smith     |           1 |          1 | 2020-01-01 |
| Jane Doe       |           2 |          2 | 2020-02-01 |
| Michael Johnson|           3 |          3 | 2020-03-01 |
| Steve Rogers   |           4 |       NULL |     NULL   |
| Peter Parker   |       NULL  |          4 | 2020-04-01 |
+----------------+-------------+------------+------------+
```
### CROSS JOIN
Этот тип соединения возвращает декартово произведение двух таблиц. Он возвращает все возможные комбинации строк из двух таблиц.<br><br>
Запрос.
```sql
SELECT * FROM customers
CROSS JOIN orders;
```
Результат.
```sql
+----------------+-------------+------------+------------+
| customer_name  | customer_id | order_id   | order_date |
+----------------+-------------+------------+------------+
| John Smith     |           1 |          1 | 2020-01-01 |
| John Smith     |           1 |          2 | 2020-02-01 |
| John Smith     |           1 |          3 | 2020-03-01 |
| John Smith     |           1 |          4 | 2020-04-01 |
| Jane Doe       |           2 |          1 | 2020-01-01 |
| Jane Doe       |           2 |          2 | 2020-02-01 |
| Jane Doe       |           2 |          3 | 2020-03-01 |
| Jane Doe       |           2 |          4 | 2020-04-01 |
| Michael Johnson|           3 |          1 | 2020-01-01 |
| Michael Johnson|           3 |          2 | 2020-02-01 |
| Michael Johnson|           3 |          3 | 2020-03-01 |
| Michael Johnson|           3 |          4 | 2020-04-01 |
| Steve Rogers   |           4 |          1 | 2020-01-01 |
| Steve Rogers   |           4 |          2 | 2020-02-01 |
| Steve Rogers   |           4 |          3 | 2020-03-01 |
| Steve Rogers   |           4 |          4 | 2020-04-01 |
| Peter Parker   |       NULL  |          1 | 2020-01-01 |
| Peter Parker   |       NULL  |          2 | 2020-02-01 |
| Peter Parker   |       NULL  |          3 | 2020-03-01 |
| Peter Parker   |       NULL  |          4 | 2020-04-01 |
+----------------+-------------+------------+------------+
```
Обратите внимание, что CROSS JOIN возвращает все возможные комбинации строк из обеих таблиц, и это может быть огромным и дорогостоящим с точки зрения производительности, если таблицы большие. Поэтому лучше использовать его с осторожностью.
<br><br>
Это основные типы объединений в SQL, и приведенные здесь примеры представляют собой базовый синтаксис для каждого типа объединения. В зависимости от условий использования, вам может потребоваться дополнительная фильтрация результатов с помощью предложения WHERE.

### UNION
Есть еще один оператор не относящийся к JOIN но выполняющий похожую функцию.
UNION - это оператор SQL, который объединяет набор результатов двух или более операторов SELECT в один набор результатов. Оператор UNION исключает дублирующиеся строки из конечного набора результатов, чего нельзя сказать о JOIN.

For example, if you want to combine the customer_name column from the customers table with the order_date column from the orders table, you would use the following query:
```sql
SELECT customer_name FROM customers
UNION
SELECT order_date FROM orders;
```
As I mentioned before, the column data types of both SELECT statements need to be compatible. If the data types are not compatible, you will get an error.
Also, you can use UNION ALL instead of UNION to include duplicate rows in the final result set, if you want.
```sql
SELECT customer_name FROM customers
UNION ALL
SELECT order_date FROM orders;
```
This will return the same result as before but with duplicates.
```sql
+----------------+
| customer_name  | 
+----------------+
| John Smith     |
| Jane Doe       |
| Michael Johnson|
| Steve Rogers   |
| 2020-01-01     |
| 2020-02-01     |
| 2020-03-01     |
| 2020-04-01     |
+----------------+
```
