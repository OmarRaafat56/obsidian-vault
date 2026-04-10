[[CCNA]]
Module 11: IPv4 Addressing
11.1 IPv4 Address Structure

An IPv4 address is a 32-bit hierarchical address composed of a Network portion and a Host portion.
Subnet Mask & ANDing

    Subnet Mask: A 32-bit value used to distinguish the network portion from the host portion.

    Logical ANDing: The bitwise process switches and routers use to find the network address.

        1 AND 1=1

        1 AND 0=0

        0 AND 0=0

    Prefix Length: A shorthand (Slash Notation) representing the number of "1" bits in a mask (e.g., 255.255.255.0 is /24).

Address Types within a Subnet

    Network Address: All host bits are 0.

    First Host Address: All host bits are 0, and the last bit is 1.

    Last Host Address: All host bits are 1, and the last bit is 0.

    Broadcast Address: All host bits are 1.

11.2 Unicast, Broadcast, and Multicast

    Unicast: One-to-one communication.

    Broadcast: One-to-all communication within a local network (e.g., 255.255.255.255).

    Multicast: One-to-many communication (Range: 224.0.0.0 to 239.255.255.255).

11.3 Types of IPv4 Addresses
Public vs. Private (RFC 1918)

Private addresses are used internally and are not globally routable. NAT (Network Address Translation) is used to translate private IPs to public ones for internet access.
Private Range	Prefix
10.0.0.0 – 10.255.255.255	/8
172.16.0.0 – 172.31.255.255	/12
192.168.0.0 – 192.168.255.255	/16