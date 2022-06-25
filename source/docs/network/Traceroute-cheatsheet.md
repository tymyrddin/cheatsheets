# Traceroute CheatSheet

## Basic commands

Basic traceroute:

    # traceroute [domain]

Disable IP address and host name mapping:

    # traceroute [domain] -n

Configure response wait time. The -w option expects a value which will be taken as the response time to wait for (for example 0,1 seconds) If traceroute is unable to wait for any response it will print *’s.

    # traceroute [domain] -w 0.1

Configure number of queries per hop. Traceroute uses a default value of 3 packets per hop to provide 3 round trip times. With the option ‘-q’ (integer) you can set a new value for the number of probes per hop.

    # traceroute [domain] -q 5

Configure the TTL value. By default, the TTL value is 1 which means the output starts off with the first router in the path but using the ‘-f’ option a new value of the TTL field can be set.

    # traceroute [domain] -f 8 

## Resources

* [Traceroute for Linux](http://traceroute.sourceforge.net/) is a package.