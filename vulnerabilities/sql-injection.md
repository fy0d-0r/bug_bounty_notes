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

Datatypes
```
INT
FLOAT
CHAR
VARCHAR
DATE #YY-MM-DD
DATETIME #YY-MM-DD HH:MM:SS
BLOB(Binary Large Objects) #store large amount of data such as images
TEXT
```

Parameters
```
PRIMARY KEY
```
Actions
```
CREATE #create tables or dbs
DROP #delete tables or dbs
DELETE #delete rows from tables
INSERT #insert rows into tables
SELECT #read through dbs
UPDATE #update table rows
GRANT OPTION #grant or remove other users' privileges
```

Start up
```
service mysql start
mysqladmin version
mysqladmin -u root password "p@$$w0rd" #settin mysql root user password
mysql -u root -p
```

DATABASES
```
mysql> show databases;
mysql> create database <DB_NAME>;
mysql>  use <DB_NAME>;
mysql> drop database <dbname>;
```

TABLES
```
mysql> show tables;
mysql> create table coffee_table (
  id int,
  name varchar(255),
  region varchar(255),
  roast varchar(255)
  );
mysql> describe coffee_table;
mysql> show columns from coffee_table;
mysql> drop table coffee_table;
```
```
mysql> show tables;
mysql> show columns from <table_name>;
mysql> create table <tablename>(
     <column_name> <datatype> <parameter>,
     <column_name> <datatype> <parameter>,
     <column_name> <datatype> <parameter>
);
mysql> create table student(
     student_id INT PRIMARY KEY,
     name VARCHAR(20),
     major VARCHAR(20)
);
PRIMARY KEY means that each value in the student_id column must be unique within the table, and it cannot contain NULL values

mysql> show columns from <table name>;
mysql> show columns from students;
mysql> drop table <table_name>;
mysql> drop table students;
mysql> insert into <table_name> (field1,field2,...,fieldN) values (value1, value2,...,valueN);
mysql> delete from <table_name> where <condition>
mysql> delete from result_tbl where result_id = 5;
mysql> delete * from result_tbl;
mysql> update <table_name> set <field1>=<new_value1>, <field2>=<new_value2> where <condition>
mysql> update team_tbl set captain_name = "John" where team_name = "StarWar";
mysql> select * from <table_name> order by <column_name> asc;
mysql> select * from <table_name> order by <column_name> desc;
mysql> select * from <table_name> order by <column_num> asc;
mysql> select * from <table_name> order by <column_num>;
mysql> select * from <table_name> limit <number of first rows>
mysql> select * from <table_name> limit <index number of row>,<number of rows>

mysql> select 1,2,3,4 from team_tbl;
mysql> select 1,2,3,4;
mysql> select 1 from team_tbl;
mysql> select 1 as number;
mysql> select group_concat(table_name) from information_schema.tables;
```

Managing Users In Mysql
```
mysql> insert into user
     (host, user, password,
      select_priv, insert_priv, update_priv, ssl_cipher, x509_issuer, x509_subject, authentication_string)
      values ('localhost','chris',
      password('chris2014'), 'Y', 'Y', 'Y', '', '', '', '');
mysql> select host, user, password from user where user = 'chris';
mysql> grant <permission_type> on <dbname>.<tablename> to '<username>'@'localhost';
mysql> grant all privileges on *.* to 'chris'@'localhost';
mysql> flush privileges;
mysql> drop user '<username>'@'localhost';
```

`nmap` dump mysql hashes
```
nmap -p 3306 --script 10.0.2.23 mysql-dump-hashes --script-args="username=chris,password=chris2014"
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

## SQL injection Types
```
In-Band SQLi
- Error-Based
- Union-Based
Blind SQLi
- Boolean-Based
- Time-Based
Out-Of-Bound SQLi
```


Using `sqlmap`
```
sqlmap -u <link> --dbs
sqlmap -u <link> -D <dbname> --tables
sqlmap -u <link> -D <dbname> -T <table_name> --columns
sqlmap -u <link> -D <dbname> -T <table_name> -C <column_name> --dump
```
```
-r <requestfile> #request file from burp
--dbms #specify the type of backend db
```

Search Vulnerable Sites(Google Dorks)
```
site:<host> php?id=
site:http://testphp.vulnweb.com/ php?id=
inurl:php id=site.in
inurl:login.php?id=
```

Boolean Based
```
select * from team_tbl where captain='' or 1='1';
```

ErrorBased
```
select * from team_tbl where id = 1 order by 4;
```

## Creating a Page that will update the database from get parameter

### Configuring the Database
```
$ sudo mysqladmin -u root password "rootpassword";
$ sudo mysql -u root -p

mysql> create database school_db;
mysql> show databases;
mysql> use school_db;

MariaDB [school_db]> create table students(
    -> roll INT(30) NOT NULL PRIMARY KEY,
    -> name VARCHAR(30) NOT NULL,
    -> major VARCHAR(30) NOT NULL,
    -> year VARCHAR(30) NOT NULL,
    -> created_at DATETIME NOT NULL DEFAULT CURRENT_DATE
    -> );
MariaDB [school_db]> show tables;
MariaDB [school_db]> describe students;
MariaDB [school_db]> show columns from students;
```

### Creating Web Page
```
<!DOCTYPE html>
<html lang="en">

	<head>
		<title>web page</title>
	</head>
	<body>
		WELCOME TO THE SCHOOL<br>
	</body>
<?php

	$servername = "localhost";
        $username = "root";
        $password = "rootpassword";
        $database = "school_db";
        $conn = new mysqli($servername, $username, $password, $database);

        if($conn->connect_error){
                die("Connection failed".$conn->connect_error);
	}else{
		echo "Connection Successful<br>";
	}

        $roll = $_GET['roll'];
        $name = $_GET['name'];
        $major = $_GET['major'];
        $year = $_GET['year'];

        $sql = "INSERT INTO students (roll,name,major,year) VALUES ('$roll', '$name', '$major', '$year');";
	echo $sql;	
	$result=$conn->query($sql);
	if($result === TRUE){
                echo "<br>Database is updated successfully<br>";
        }else{
                echo "Error: ". $sql . "<br>" . $conn->error;
        }
        $conn->close();
?>

</html>
```

### Removing the Table and Database
```
mysql> drop table students;
mysql> drop database school_db;
```

## Creating a Page that will update the database from post parameter and then extract data from the database

### Configuring the Database

```
MariaDB [(none)]> show databases;
MariaDB [(none)]> create database school_db;
MariaDB [(none)]> use school_db;
```

```
MariaDB [school_db]> create table student_lms(
    -> id INT(30) NOT NULL AUTO_INCREMENT PRIMARY KEY,
    -> roll INT(30) NOT NULL,
    -> name VARCHAR(30) NOT NULL,
    -> major VARCHAR(30) NOT NULL,
    -> username VARCHAR(30) NOT NULL,
    -> password VARCHAR(30) NOT NULL,
    -> created_at DATETIME NOT NULL DEFAULT CURRENT_DATE
    -> );
```

```
MariaDB [school_db]> show columns from student_lms;
+------------+-------------+------+-----+-----------+----------------+
| Field      | Type        | Null | Key | Default   | Extra          |
+------------+-------------+------+-----+-----------+----------------+
| id         | int(30)     | NO   | PRI | NULL      | auto_increment |
| roll       | int(30)     | NO   |     | NULL      |                |
| name       | varchar(30) | NO   |     | NULL      |                |
| major      | varchar(30) | NO   |     | NULL      |                |
| username   | varchar(30) | NO   |     | NULL      |                |
| password   | varchar(30) | NO   |     | NULL      |                |
| created_at | datetime    | NO   |     | curdate() |                |
+------------+-------------+------+-----+-----------+----------------+
7 rows in set (0.003 sec)
```

### Creating Web Page
`index.html`
```
<!DOCTYPE html>
<html>
	<head>
		<title>web page</title>
	</head>
	<body>
		<p>Hello World</p>
		<br>
		<form action="./action.php" method="post">
			<label for="username">Username:</label><br>
			<input type="text" name="username"><br>
			<label for="password">Password:</label><br>
			<input type="password" name="password"><br>
			<input type="submit" value="login">
		</form>
	</body>
</html>
```

`action.php`
```
<?php
        //Connecting Database
        $servername = "localhost";
        $username = "root";
        $password = "rootpassword";
        $database = "school_db";
        $conn = new mysqli($servername, $username, $password, $database);
        if($conn->connect_error){
                die("Connection failed".$conn->connect_error);
        }else{
                echo "<br>Connection Successful<br>";
        }

	//GET GET data for register
	$roll = $_GET['roll'];
	$name = $_GET['name'];
	$major = $_GET['major'];
	$r_username = $_GET['username'];
	$r_password = $_GET['password'];
	$register = "INSERT INTO student_lms (roll,name,major,username,password) VALUES ('$roll','$name','$major','$r_username','$r_password');";
	echo "$register<br>";
	
	//Getting POST data for login
        $username = $_POST['username'];
	$password = $_POST['password'];
	$login = "SELECT * FROM student_lms WHERE username='$username' and password='$password';";
	echo "$login<br>";

	//Query GET or POST Request
	if(isset($_GET['roll'])){
		echo "GET ISSET<br>";
		$result = $conn->query($register);
	}

	if(isset($_POST['username'])){
		echo "POST ISSET<br>";
		$result = $conn->query($login);
		if(!$result){
			echo "Error".$conn->error;
		}else{
			echo "Login Successful<br>";
			$row = $result->fetch_assoc();
			echo $row["name"];
		}
	}

	//Displaying the result
	echo $result;

	//Closing the connection
	$conn->close();

?>
```

