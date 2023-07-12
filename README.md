
# Домашнее задание к занятию "12.4 «SQL. Часть 2»" - Соловьёв Андрей SYS-18

---

Работа была выполнена на виртуальной машине с Linux Lite 6.4


## Задание 1

Одним запросом получите информацию о магазине, в котором обслуживается более 300 покупателей, и выведите в результат следующую информацию:

фамилия и имя сотрудника из этого магазина;
город нахождения магазина;
количество пользователей, закреплённых в этом магазине.

Скрипт

SELECT s.first_name , s.last_name , c.city, count(c2.first_name) 
from staff s 
join address a on a.address_id = s.address_id 
join city c on c.city_id = a.city_id 
join customer c2 on c2.store_id = s.store_id 
GROUP  BY c.city, s.first_name ,s.last_name HAVING COUNT(c2.customer_id) > 300;


![Z1-1.png](https://github.com/Andrewsolo1969/12-4-hw/blob/main/img/Z1-1.png)

![Z1-2.png](https://github.com/Andrewsolo1969/12-4-hw/blob/main/img/Z2-1.png)

![diagram.png](https://github.com/Andrewsolo1969/12-4-hw/blob/main/img/diagram.png)



## Задание 2

Получите количество фильмов, продолжительность которых больше средней продолжительности всех фильмов.

Скрипт
SELECT COUNT(`length`) film_id  FROM film f  WHERE `length` > (SELECT AVG(`length`) FROM film);


![Z2.png](https://github.com/Andrewsolo1969/12-4-hw/blob/main//img/Z2.png)



## Задание 3

Получите информацию, за какой месяц была получена наибольшая сумма платежей и добавьте информацию по количеству аренд за этот месяц.


Скрипт

SELECT YEAR(payment_date) , MONTH(payment_date), COUNT(rental_id), Sum(amount) 
FROM payment p GROUP BY YEAR(payment_date) , MONTH(payment_date) order by SUM(amount) DESC LIMIT 1;

![Z3-1.png](https://github.com/Andrewsolo1969/12-4-hw/blob/main//img/Z3-1.png)

![Z3-2.png](https://github.com/Andrewsolo1969/12-4-hw/blob/main//img/Z3-2.png)




