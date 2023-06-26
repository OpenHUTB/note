





https://github.com/hxgdzyuyi/tang_poetry
create database tang_poetry;

mysql -uroot -p -h10.19.19.23 -P3319 tang_poetry < tang_poetry.sql

全唐诗中写诗歌最多的人，以及数量
SELECT poets.`name`, COUNT(poetries.id) 
FROM poetries 
LEFT JOIN poets ON poetries.poet_id=poets.id 
GROUP BY poets.id 
ORDER BY COUNT(poetries.id) DESC LIMIT 10;

杨贵妃的诗歌
SELECT poetries.title, poetries.content 
FROM poetries 
LEFT JOIN poets ON poetries.poet_id=poets.id 
WHERE poets.`name`='杨贵妃';

