# Shodan CLI cheatsheet

[Shodan](https://www.shodan.io/) gathers information about all devices directly connected to the Internet. If a device is directly hooked up to 
the Internet then Shodan queries it for various publicly-available information. 

The shodan command-line interface (CLI) is a command-line library for Shodan search engine. 

Install with pip:

    $ pip install shodan

Get the private API key from your shodan account settings:

    $ shodan init PRIVATE_API_KEY

List with help

    $ shodan

## Examples

Public internet-facing ip address:

    $ shodan myip

Get information on location, ports, owner of an IP.

    $ shodan host xxx.xxx.xxx.xxx
