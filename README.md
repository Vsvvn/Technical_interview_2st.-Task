
postgres=# CREATE DATABASE task;\
CREATE DATABASE\
postgres=# \c task\
Вы подключены к базе данных "task" как пользователь "postgres".\
task=# CREATE TABLE employee(\
task(# name VARCHAR(50) NOT NULL,\
task(# department INT NOT NULL,\
task(# salary INT NOT NULL);\
CREATE TABLE\
task=# INSERT INTO employee (\
task(# name, department, salary)\
task-# VALUES('Анна', 1, 50000);\
INSERT 0 1\
task=# INSERT INTO employee (\
task(# name, department, salary)\
task-# VALUES('Инна', 2, 51000);\
INSERT 0 1\
task=# INSERT INTO employee (\
task(# name, department, salary)\
task-# VALUES('Петр', 2, 55000);\
INSERT 0 1\
task=# INSERT INTO employee (\
task(# name, department, salary)\
task-# VALUES('Ольга', 3, 57000);\
INSERT 0 1\
task=# INSERT INTO employee (\
task(# name, department, salary)\
task-# VALUES('Евгений', 3, 56000);\
INSERT 0 1\
task=# SELECT department AS Отдел,\
task-# MAX (salary) AS максимальная_зарплата,\
task-# AVG (salary) AS средняя_зарплата,\
task-# COUNT (*) count\
task-# FROM employee\
task-# GROUP by department\
task-# HAVING count (department) > 1\
task-# ORDER by count(*) desk;\
ОШИБКА:  ошибка синтаксиса (примерное положение: "desk")\
СТРОКА 8: ORDER by count(*) desk;\
^\
task=# SELECT department AS Отдел,\
task-# MAX (salary) AS максимальная_зарплата,\
task-# AVG (salary) AS средняя_зарплата,\
task-# COUNT (*) count\
task-# FROM employee\
task-# GROUP by department\
task-# HAVING count (department) > 1\
task-# ORDER by count(*) desc;\
Отдел | максимальная_зарплата |  средняя_зарплата  | count\
-------+-----------------------+--------------------+-------\
3 |                 57000 | 56500.000000000000 |     2\
2 |                 55000 | 53000.000000000000 |     2\
(2 строки)
