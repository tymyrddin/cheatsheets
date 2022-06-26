# Unicornscan cheatsheet

[Unicornscan](https://www.aldeid.com/wiki/Unicornscan) is a tool for information gathering and security audits.

## Example scans

    us -H -msf -Iv [address] -p 1-65535
    us -H -mU -Iv [address] -p 1-65535

## Flags

    SYN : -mT
    ACK scan : -mTsA
    Fin scan : -mTsF
    Null scan : -mTs
    Xmas scan : -mTsFPU
    Connect Scan : -msf -Iv
    Full Xmas scan : -mTFSRPAU
    scan ports 1 through 5 : (-mT) host:1-5

