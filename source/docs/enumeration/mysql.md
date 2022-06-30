# MySQL enumeration

## Nmap

```text
# nmap -sV -p 3306 --script mysql-audit,mysql-databases,mysql-dump-hashes,mysql-empty-password,mysql-enum,mysql-info,mysql-query,mysql-users,mysql-variables,mysql-vuln-cve2012-2122 <IP target>
```

The [CVE-2012-2122](https://www.cve.org/CVERecord?id=CVE-2012-2122) vulnerability allows remote users to bypass 
authentication due to improper checking of returned values. Only old systems are affected: Ubuntu Linux 64-bit (10.04, 
10.10, 11.04, 11.10, 12.04); OpenSuSE 12.1 64-bit MySQL 5.5.23-log; Debian Unstable 64-bit 5.5.23-2; Fedora; and Arch 
Linux. Still, worth checking for.

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