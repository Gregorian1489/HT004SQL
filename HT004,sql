-- https://drive.google.com/file/d/1TZzW8ZlDdvIfDC9C46bUeILey6opQjdu/view?usp=share_link

-- Вывести всех котиков по магазинам по id (условие соединения shops.id = cats.shops_id)

SELECT cats.name, shops.shopname
FROM cats
JOIN shops ON shops.id = cats.shops_id;

-- Вывести магазин, в котором продается кот “Murzik”

SELECT shops.shopname
FROM shops
INNER JOIN cats
ON shops.id = cats.shops_id
WHERE cats.name = "Murzik";

-- Вывести магазины, в которых НЕ продаются коты “Murzik” и “Zuza”

SELECT s.shopname 
FROM shops s
LEFT JOIN cats c ON s.id = c.shops_id AND (c.name = 'Murzik' OR c.name = 'Zuza')
WHERE c.name IS NULL; 

/*
Вывести название и цену для всех анализов, которые продавались 5 февраля 2020 и всю следующую неделю.
Есть таблица анализов Analysis:
an_id — ID анализа;
an_name — название анализа;
an_cost — себестоимость анализа;
an_price — розничная цена анализа;
an_group — группа анализов.
Есть таблица групп анализов Groups:
gr_id — ID группы;
gr_name — название группы;
gr_temp — температурный режим хранения.
Есть таблица заказов Orders:
ord_id — ID заказа;
ord_datetime — дата и время заказа;
ord_an — ID анализа.
*/

SELECT an_name, an_price
FROM Analysis
JOIN Orders ON Analysis.an_id = Orders.ord_an
WHERE ord_datetime BETWEEN '2020-02-05' AND '2020-02-12';

-- https://www.notion.so/c448e32ae1344f22b1deae7f42c8b57f 

-- Подсчитать общее количество лайков, которые получили пользователи младше 12 лет.

SELECT 
COUNT(*) AS 'Общее кол-во лайков'
FROM likes
WHERE user_id IN (
SELECT user_id 
FROM profiles
WHERE TIMESTAMPDIFF(YEAR, birthday, NOW()) < 12);

-- Определить кто больше поставил лайков (всего): мужчины или женщины.

SELECT CASE (gender)
WHEN 'm' THEN 'Мужчины'
WHEN 'f' THEN 'Женщины'
END AS 'Больше лайков ставят:', COUNT(*) as 'Кол-во лайков'
FROM profiles p 
JOIN likes l 
WHERE l.user_id = p.user_id
GROUP BY gender 
LIMIT 1; -- для проверки можно увеличить LIMIT

-- Вывести всех пользователей, которые не отправляли сообщения.

SELECT DISTINCT CONCAT(firstname, ' ', lastname, ' (id: ', (id), ')') AS 'Не отправляют сообщения'
FROM users
WHERE NOT EXISTS (
SELECT from_user_id
FROM messages
WHERE users.id = messages.from_user_id
);
