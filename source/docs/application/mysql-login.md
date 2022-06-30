# SQL injection login bypass

## Building SQL segments to modify the WHERE clause and make it true

```text
SELECT * FROM users WHERE username='$USERNAME' AND password='$PASSWORD'
```

Assume a login form with two input fields (username and password) which are both vulnerable (page breaks on 
entering a `'` and responds to changed queries), meaning, the backend script generates a query to validate username and 
password provided by the user and quotes are not correctly handled (escaped) by the application and allow an adversary 
to modify the query. 

The page logic:

```text
admin
wrong' OR 'a'='a
```

Results in a WHERE clause which is true:

```text
SELECT * FROM users WHERE username='admin' AND password='wrong' OR 'a'='a'
```
Because of operator precedence, the AND condition is evaluated first. Then the OR operator is evaluated, making the 
WHERE clause true. Even more, the condition will be true for all rows of the users table and as a result,
username is ignored and the adversary will be logged in as the first user in users table.

The page logic:

```text
admin' --
whatever
```

Also results in a WHERE clause which is true, but now the adversary logs in as admin:

```text
SELECT * FROM users WHERE username='admin' -- AND password='whatever'
```

By using line commenting, an adversary eliminates a part of the login condition and gains access.
Note: For some DBMS, a space needs to be added before and after `--`.