# IDS/IPS Evasion

## Timing attacks

These evasion attacks can be used against any correlating engine that uses a fixed time window and a threshold to classify multiple packets into a composite event. 

Go slow, extremely slow, just a couple of packets per minute will do.

## Protocol-level misinterpretation

### TTL

The IDS/IPS has no easy way of knowing the number of hops to the end point of an IP session stream. 

1. Send some packets with a good payload and with an IP TTL long enough to arrive to the IDS/IPS but not long enough to arrive at the intended host.
2. Follow up with packets with an evil payload and a long IP TTL, the IPS/IDS might consider these just repetitions, and the evil payload reaches the host.   

### Checksums

Checksum calculations are costly, hence not always used. 

1. Send a good payload with a bad checksum. For example, send a packet with the `RST` flag set and an invalid checksum, such that the IPS/IDS concludes the packet is going to close the connection, but the intended host will reject the packet because the checksum is invalid. 
2. Follow up with an evil payload and a good checksum. To the IDS/IPS this appears to be a duplicate, and it will be ignored, but the intended host will now process the evil payload.

## Fragmenting packets

If the IDS/IPS can not reassemble fragmented packets, these might reach the intended host. This is one of the early 
network IPS evasion techniques used to attempt to bypass IDS/IPS. Classic examples of fragmentation-based evasion are:
* TCP segmentation and reordering, where the IDS/IPS must correctly reassemble the entire TCP session, including for example selective ACKs and selective retransmission.
* IP fragmentation, where the IP traffic is fragmented in a manner that it is not uniquely interpreted, causing the IDS/IPS to interpret it differently from the intended host, which leads to the host being compromised.

### Overlapping fragments

In overlapping fragments the offset values in the IP header don't match up as they should, for example, the first 8 
bytes of packet 2 overlap with the last 8 bytes of packet 1, and the 8 last bytes of packet 2 overlap with the first 
8 bytes of packet 3. The IDS/IPS sensor may reassemble these packets differently from the host. Different 
operating systems handle this situation differently:

* BSD prefers packets with smaller offset. For packets with same offset, it will choose the first one.
* Linux does like BSD, but it prefers the last packet with the same offset.
* Windows uses "First value that comes, value that stays".
* Cisco routers use "Last value that comes, value that stays".

## Substitution and insertion

An IDS/IPS sensor may let an evil payloads pass if it looks for data in a particular format and does not recognise 
true meaning of the data. Substitute payload data with other data in a different format, but the same meaning:

* Substitute spaces with tabs, and vv, inside HTTP requests.
* Use Unicode instead of ASCII strings and characters inside HTTP requests.
* Exploit mutation, where shellcode can be substituted by completely different shellcode with the same meaning.
* Exploit case sensitivity and changing case of characters in an evil payload, if the IDS/IPS is configured with case-sensitive signature.
