[[CCNA]]
Module 9: Address Resolution
9.1 MAC and IP

To communicate on a network, a device needs both a physical and a logical address.

    Layer 2 (MAC Address): Used for NIC-to-NIC communication on the same local network.

    Layer 3 (IP Address): Used for end-to-end communication from the original source to the final destination.

Delivery Logic

    Local Destination: If the destination IP is on the same subnet, the destination MAC is the actual address of the destination device.

    Remote Destination: If the destination IP is on a different network, the destination MAC is the address of the Default Gateway (router).

9.2 ARP (Address Resolution Protocol)

ARP is the method used by IPv4 to map a known IPv4 address to a MAC address.
Functions

    Address Resolution: Finding the MAC address associated with an IPv4 address.

    Maintenance: Storing these mappings in an ARP Table (ARP Cache) in RAM.

The Process

    ARP Request: A broadcast frame sent to find a MAC address. Every device on the LAN receives it, but only the one with the matching IP replies.

    ARP Reply: A unicast frame sent back to the requester containing the requested MAC address.

    Caching: To reduce traffic, devices save mappings. Entries are removed when the ARP cache timer expires or are cleared manually.

Useful Commands

    Cisco Router: show ip arp

    Windows PC: arp -a

    [!WARNING] Security Issues: ARP is vulnerable to ARP Spoofing/Poisoning, where a threat actor sends fake ARP replies to intercept traffic.

9.3 IPv6 Neighbor Discovery (ND)

IPv6 does not use ARP. Instead, it uses the Neighbor Discovery protocol via ICMPv6 messages.
Key Message Types
Message Type	Function
Neighbor Solicitation (NS)	Sent to find a destination's MAC address (replaces ARP Request).
Neighbor Advertisement (NA)	The reply containing the MAC address (replaces ARP Reply).
Router Solicitation (RS)	Sent by a device to find an IPv6 router on the link.
Router Advertisement (RA)	Sent by routers to provide addressing and network info to hosts.
Redirect	Sent by a router to inform a host of a better next-hop for a destination.
How it differs from ARP

Instead of broadcasting to everyone, IPv6 ND uses Multicast (specifically the Solicited-Node Multicast address), making it more efficient than the "shout-to-everyone" approach of IPv4 ARP.
Tags

#Cisco #CCNA #Networking #ARP #IPv6 #NeighborDiscovery #ICMPv6 #Layer3

Next Step: I've noticed you're moving through the Cisco ITN modules. Would you like me to create a comparison table between IPv4 ARP and IPv6 ND to help you remember the differences for your exam?