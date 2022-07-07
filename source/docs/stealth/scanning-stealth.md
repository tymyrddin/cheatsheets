# Stealth while scanning

Never use connect scan (-sT), which establishes a full connection to a port, if one wishes to remain stealthy. Excessive port connections can create a DoS condition on older boxes, and will raise the alarms on any IDS.

* Use a stealthy port-scanning method with nmap, such as a TCP SYN scan (sometimes called a half-open scan). It is not only stealthy, it is also lighter on both systems, source and target. 
* Mask your IP from the target (Don't expect to find possibilities for either of these two all the time, but do keep looking, especially among older systems not offering useful services.):
    * Use an FTP bounce scan if possible. Some ftp servers feature allowing anonymous users to proxy connections to other systems. If you find an anonymous ftp server during enumeration, or you know of one to which you have login credentials, try using the -b option with user:pass@server:ftpport. If the server does not require authentication, you can skip the user:pass and if it is running on the standard port you can also leave out the ftpport part. This only works on some ftp servers. Many ftp servers today have this option disabled (by default). 
    * Idle scan gives a similar result but uses a different type of scanning. If you can identify an intermediate machine (a zombie) with low traffic and predictable fragment identification values (IP ID) you can send spoofed packets to your target, with the source set to the zombie with <code>-sI zombiehost:port</code>. An IDS will see the idle scan target as the system doing the scanning. If the idle target is a by your target trusted machine that can bypass host-based access control lists, jackpot!


|Template number 	|Template name 	|Description |
| --- | --- | --- | 
|0 	|Paranoid 	|Used for IDS evasion. One port scanned at a time, with 5 minutes between probes|
|1 	|Sneaky 	|Used for IDS evasion. One port scanned at a time, with 15 seconds between probes|
|2 	|Polite 	|Uses less bandwith and resources. One port scanned at a time, with 0.4 seconds between probes|
|3 	|Normal 	|Standard scan. Works locally and on the internet|
|4 	|Aggressive 	|Fast scan. Parallel processing, with 10 milliseconds between probes|
|5 	|Insane 	|Sacrificing accuracy for speed. Parallel processing, with 5ms minutes between probes|



