# Mission 3

## Part 1

[[Link to video](https://www.youtube.com/watch?v=UUhavvMO2FQ)
](https://drive.google.com/file/d/1sbcNPnLbkBN-VNi6ZF2G2tUo74Bg8Nkz/view?usp=drive_link)

## Part 2
Прикрепляю ссылку на файл где скрины схем и ответов, так как два дня подряд выходила ошибка с таймаутом 
https://docs.google.com/document/d/1AUgvhgAG4S2xBzu54fWDI6fUhadkwS3FV1g3g-mk28A/edit?usp=sharing 

## Part 3

Получить список юзернеймов пользователей
SELECT username FROM users;

Получить кол-во отправленных сообщений каждым пользователем
SELECT from_username, COUNT(id) AS number_of_sent_messages
FROM messages
GROUP BY from_username; 

Получить пользователя с самым большим кол-вом полученных сообщений и само количество
SELECT to_username, COUNT(id) AS "number of received messages"
FROM messages
GROUP BY to_username
ORDER BY "number of received messages" DESC
LIMIT 1;

Получить среднее кол-во сообщений, отправленное каждым пользователем
SELECT username, AVG(number_of_sent_messages) AS average_sent_messages
FROM (
    SELECT from_username AS username, COUNT(*) AS number_of_sent_messages
    FROM messages
    GROUP BY from_username
) AS sent_messages_per_user
GROUP BY username;
