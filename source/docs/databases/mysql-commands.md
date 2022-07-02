# MySQL commands

MySQL is an open source Relational Database Management System (RDBMS) that uses Structured Query Language (SQL). 

Default port is [3306](https://www.speedguide.net/port.php?port=3306)

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
select grantee, table_schema, privilege_type FROM schema_privileges; 
select user,file_priv from mysql.user where user='root'; 
select version(); 
select @@version();
select user(); 
select database(); 
```

## Try to change MySQL root password

```text
UPDATE mysql.user SET Password=PASSWORD('MyNewPass') WHERE User='root';
UPDATE mysql.user SET authentication_string=PASSWORD('MyNewPass') WHERE User='root';
FLUSH PRIVILEGES;
quit;
```

```text
mysql -u username -p < mycommands.sql # A file with all the commands you want to execute
mysql -u root -h 127.0.0.1 -e 'show databases;'
```