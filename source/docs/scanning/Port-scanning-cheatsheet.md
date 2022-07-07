# Port scanning cheatsheet

```text
# nmap -sn -T4 -oG Discovery.gnmap 192.168.9.1/24  
Starting Nmap 7.91 ( https://nmap.org ) at 2021-03-13 18:47 UTC
Nmap scan report for LEDE.lan (192.168.9.1)
Host is up (0.00022s latency).
MAC Address: C1:4F:B2:BD:1A:3E (Tp-link Technologies)
Nmap scan report for machine.lan (192.168.9.173)
Host is up (0.00025s latency).
MAC Address: B3:BC:70:43:33:05 (Pegatron)
Nmap scan report for kali.lan (192.168.1.89)
Host is up.
Nmap done: 256 IP addresses (3 hosts up) scanned in 2.04 seconds
```

Enumerating live hosts in a file 

```text
# grep "Status: Up" Discovery.gnmap | cut -f 2 -d ' ' > LiveHosts.txt  
```

OS services TCP ports 21-25,80,139,8080:

```text
# nmap -O -sV -T4 -Pn -p T:21-25,80,139,8080 -oG OS_Service_Detect -iL LiveHosts.txt

Host discovery disabled (-Pn). All addresses will be marked 'up' and scan times will be slower.
Starting Nmap 7.91 ( https://nmap.org ) at 2021-03-13 21:46 UTC
Nmap scan report for LEDE.lan (192.168.1.1)
Host is up (0.00043s latency).

PORT     STATE  SERVICE     VERSION
21/tcp   closed ftp
22/tcp   open   ssh         Dropbear sshd (protocol 2.0)
23/tcp   closed telnet
24/tcp   closed priv-mail
25/tcp   closed smtp
80/tcp   open   http        LuCI Lua http config
139/tcp  closed netbios-ssn
8080/tcp closed http-proxy
MAC Address: C1:4F:B2:BD:1A:3E (Tp-link Technologies)
Device type: WAP
Running: Linux 3.X|4.X
OS CPE: cpe:/o:linux:linux_kernel:3.18 cpe:/o:linux:linux_kernel:4.1
OS details: OpenWrt Chaos Calmer 15.05 (Linux 3.18) or Designated Driver (Linux 4.1 or 4.4)
Network Distance: 1 hop
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

Nmap scan report for machine.lan (192.168.1.173)
Host is up (0.00040s latency).

PORT     STATE  SERVICE     VERSION
21/tcp   closed ftp
22/tcp   open   ssh         OpenSSH 7.9p1 Debian 10+deb10u2 (protocol 2.0)
23/tcp   closed telnet
24/tcp   closed priv-mail
25/tcp   closed smtp
80/tcp   open   http        Apache httpd 2.4.38 ((Debian))
139/tcp  closed netbios-ssn
8080/tcp closed http-proxy
MAC Address: B3:BC:70:43:33:05 (Pegatron)
Device type: general purpose
Running: Linux 4.X|5.X
OS CPE: cpe:/o:linux:linux_kernel:4 cpe:/o:linux:linux_kernel:5
OS details: Linux 4.15 - 5.6
Network Distance: 1 hop
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

Nmap scan report for kali.lan (192.168.1.89)
Host is up (0.000090s latency).

PORT     STATE  SERVICE     VERSION
21/tcp   closed ftp
22/tcp   closed ssh
23/tcp   closed telnet
24/tcp   closed priv-mail
25/tcp   closed smtp
80/tcp   closed http
139/tcp  closed netbios-ssn
8080/tcp closed http-proxy
Too many fingerprints match this host to give specific OS details
Network Distance: 0 hops

OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 3 IP addresses (3 hosts up) scanned in 10.16 seconds
```

OS services UDP: 53,111,137                                                                        

```text
# nmap -O -sU -T4 -Pn -p U:53,111,137 -oG OS_Service_Detect -iL LiveHosts.txt

Host discovery disabled (-Pn). All addresses will be marked 'up' and scan times will be slower.
Starting Nmap 7.91 ( https://nmap.org ) at 2021-03-13 21:47 UTC
Nmap scan report for LEDE.lan (192.168.1.1)
Host is up (0.00097s latency).

PORT    STATE  SERVICE
53/udp  open   domain
111/udp closed rpcbind
137/udp closed netbios-ns
MAC Address: C1:4F:B2:BD:1A:3E (Tp-link Technologies)
Too many fingerprints match this host to give specific OS details
Network Distance: 1 hop

Nmap scan report for machine.lan (192.168.1.173)
Host is up (0.00042s latency).

PORT    STATE  SERVICE
53/udp  closed domain
111/udp closed rpcbind
137/udp closed netbios-ns
MAC Address: B3:BC:70:43:33:05 (Pegatron)
Too many fingerprints match this host to give specific OS details
Network Distance: 1 hop

Nmap scan report for kali.lan (192.168.1.89)
Host is up (0.00011s latency).

PORT    STATE  SERVICE
53/udp  closed domain
111/udp closed rpcbind
137/udp closed netbios-ns
Too many fingerprints match this host to give specific OS details
Network Distance: 0 hops

OS detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 3 IP addresses (3 hosts up) scanned in 3.57 seconds
```