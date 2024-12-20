# Задание

Найти вывести Имя пользователя и имя его сервиса

```SQL

-- create
CREATE TABLE USERS (
  empId INTEGER PRIMARY KEY,
  name TEXT NOT NULL,
  dept TEXT NOT NULL
);

-- insert
INSERT INTO USERS VALUES (0001, 'Iurii', 'Sales');
INSERT INTO USERS VALUES (0002, 'Sasha', 'Accounting');
INSERT INTO USERS VALUES (0003, 'Vova', 'Sales');

-- create
CREATE TABLE CAR (
  id INTEGER PRIMARY KEY,
  name TEXT NOT NULL,
  userId INTEGER NOT NULL
);

-- insert
INSERT INTO CAR VALUES (0001, 'Dodge', 0001);
INSERT INTO CAR VALUES (0002, 'Mercedes', 0003);
INSERT INTO CAR VALUES (0003, 'Lada', 0002);

-- create
CREATE TABLE CAR_SERVICE (
  id INTEGER PRIMARY KEY,
  name TEXT NOT NULL,
  carId INTEGER NOT NULL
);

-- insert
INSERT INTO CAR_SERVICE VALUES (0001, 'fit', 0001);
INSERT INTO CAR_SERVICE VALUES (0002, 'in Slsvs', 0002);
INSERT INTO CAR_SERVICE VALUES (0003, 'interservice', 0003);
```

# Мое Решение

```SQL
-- fetch 
SELECT USERS.name,CAR.name as car,CAR_SERVICE.name as service FROM USERS
inner join CAR on CAR.userId = USERS.empId
inner join CAR_SERVICE on CAR.id = CAR_SERVICE.carId
where CAR_SERVICE.name =  'interservice'
```