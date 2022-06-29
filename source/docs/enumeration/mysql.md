# MySQL enumeration

## Nmap

```text
# nmap -sV -p 3306 --script mysql-audit,mysql-databases,mysql-dump-hashes,mysql-empty-password,mysql-enum,mysql-info,mysql-query,mysql-users,mysql-variables,mysql-vuln-cve2012-2122 <IP target>
```

## Metasploit

```text
msf> use auxiliary/scanner/mysql/mysql_version
msf> use auxiliary/scanner/mysql/mysql_authbypass_hashdump
```

Requiring credentials:

```text
msf> use auxiliary/scanner/mysql/mysql_hashdump
msf> use auxiliary/admin/mysql/mysql_enum
msf> use auxiliary/scanner/mysql/mysql_schemadump
msf> use exploit/windows/mysql/mysql_start_up #Execute commands Windows, Creds
```