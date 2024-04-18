# SQL Injection

```
SQL    - Structured Query Language
DMBS   - Database Management System
```

## Database Management Systems(DBMSs)
- Microsoft SQLServer
- MySQL
- PostgreSQL
- ORACLE

## MySQL Basics

`mysqld` runs on tcp port `3306` on default.

DATABASES
```
mysql> show databases;
mysql> create database <DB_NAME>;
mysql>  use <DB_NAME>;
```

TABLES
```
mysql> show tables;
mysql> create table coffee_table (
- id int,
- name varchar(255),
- region varchar(255),
- roast varchar(255)
- );
mysql> describe coffee_table;
```

INSERT
```
mysql> insert into coffee_table values (
- 1, "default route", "ethiopia", "light");
mysql> select * from coffee_table;
```

FILTER
```
mysql> select * from avengers where origin = "earth";

mysql>  select * from avengers where origin = "earth" or origin = "asgard";

mysql> select alias from avengers where age < 30;

mysql> select alias from avengers where not origin = "earth";
```

DELETE
```
mysql> delete from avengers where first_name = "jeff";
```

UPDATE
```
mysql> update avengers set last_name = NULL where first_name = "groot";
```

ORDERS
```
mysql> select * from avengers order by age asc;
mysql> select * from avengers order by age desc;
```

ADD COLUMN
```
mysql> alter table avengers add beard boolean;
```


