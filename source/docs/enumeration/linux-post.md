# Linux post exploitation enumeration

This info can help escalate privileges.

## System information

```text
hostname
uname -a
cat /etc/*-release
cat /proc/version
mount
dpkg -l
apache2 -v
mysql –version
```

## Network information

```text
route
arp
ifconfig
netstat -antp
netstat -anup
iptables -L
cat /etc/resolv.conf
cat /etc/network/interfaces
```

## User information

```text
id
who
last
cat /etc/passwd (you will need a privilege account for this one!)
cat /etc/sudoers
cat history
```

## Information from files

```text
cat /etc/passwd
cat /etc/group
cat /etc/shadow
```

## SSH information

```text
cat ~/.ssh/authorized_keys
cat ~/.ssh/identity.pub
cat ~/.ssh/identity
cat ~/.ssh/id_rsa.pub
cat ~/.ssh/id_rsa
cat ~/.ssh/id_dsa.pub
cat ~/.ssh/id_dsa
cat /etc/ssh/ssh_config
cat /etc/ssh/sshd_config
cat /etc/ssh/ssh_host_dsa_key.pub
cat /etc/ssh/ssh_host_dsa_key
cat /etc/ssh/ssh_host_rsa_key.pub
cat /etc/ssh/ssh_host_rsa_key
cat /etc/ssh/ssh_host_key.pub
cat /etc/ssh/ssh_host_key
```