# Windows enumeration

## SMB

The Server Message Block protocol (SMB) has been updated and improved to the latest security standards in recent 
Windows Operating System releases, but there are still legacy End Of Life (EOF) operating systems running in various 
public and private sector organisations. With tools like the Nmap SMB Scripts it is easy to perform SMB Enumeration.

Port for smb is 445 while 135-9 ports are used for RPC calls which are essential for remote management of Windows systems.

Enumerate all users on remote Windows system using [SAMR Enumeration and LSA Bruteforcing](https://nmap.org/nsedoc/scripts/smb-enum-users.html):

```text
# nmap –-script smb-enum-users.nse -p445 <IP target>
```

Enumerate the Operating System of target system along with other interesting things:

```text
# nmap --script smb-os-discovery.nse -p445 <IP target>
```

Enumerate publically exposed SMB shares:

```text
# nmap --script smb-enum-shares.nse -p445 <IP target>
```