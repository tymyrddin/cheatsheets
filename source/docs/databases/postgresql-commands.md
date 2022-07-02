# PostgreSQL commands

PostgreSQL is an open source Relational Database Management System (RDBMS) that uses Structured Query Language (SQL). 

Default port is [5432](https://www.speedguide.net/port.php?port=5432)

```bash
$ 5432/tcp open  postgresql
```

## Connect

Local, without password:

```bash
$ sudo -i -u postgres
```

Local, with password:

```bash
psql –U [username] –W [password] –d [database_name]
```

Remote:

```bash
$ psql -h <REMOTE HOST> -p <REMOTE PORT> -U <DB_USER> <DB_NAME>
```

For example:
```bash
$ psql -h target_ip -U username
```

Try default Username & Passwords:
    postgres : postgres
    postgres : password
    postgres : admin
    admin : admin
    admin : password

## Basic postgresql commands
```text
\?                      # help
\c <dbname> <username>  # to change database on a specified user
\l                      # list all databases in the current PostgreSQL database server
\dt                     # list all tables in the current database
\d <table_name>         # describe a table such as a column, type, modifiers, etc.
\dn                     # list all schemas of the currently connected database
\du                     # list all users and their assigned roles
SELECT version();       # the current version of PostgreSQL server
\g                      # type the previous command again (but last command should be SELECT statement)
\q                      # exit
```

## Try to change PostgreSQL root password

```text
ALTER USER postgres WITH PASSWORD 'MyNewPass';
```

There is a table in the PostgreSQL Server which manages the user information like — username and passwords(in hash). 
It is `pg_shadow`, it can only be accessed by `postgres` user.

To  concatenate the password and username and calculate the MD5 hash, and save the result in password field:
```text
select username, passwd from pg_shadow;
```
