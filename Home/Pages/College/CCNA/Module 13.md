[[CCNA]]
Module 13: ICMP
13.1 ICMP Messages

Internet Control Message Protocol (ICMP) provides feedback regarding issues with IP packet processing. It does not make IP reliable; it simply reports errors and provides information.
Common Messages (v4 and v6)

    Host Reachability: Used by Ping to see if a host is "alive."

    Destination or Service Unreachable: Notifies the sender that a destination cannot be reached.

        ICMPv4 Codes: 0 (Net), 1 (Host), 2 (Protocol), 3 (Port).

        ICMPv6 Codes: 0 (No route), 1 (Admin prohibited/Firewall), 3 (Address unreachable).

    Time Exceeded: Sent when the TTL (IPv4) or Hop Limit (IPv6) reaches 0.

ICMPv6 Specifics (Neighbor Discovery)

ICMPv6 includes the Neighbor Discovery Protocol (NDP) for device-to-router and device-to-device communication:

    Router Solicitation (RS) / Router Advertisement (RA): Used for dynamic address allocation (SLAAC) and router discovery.

    Neighbor Solicitation (NS) / Neighbor Advertisement (NA): Used for address resolution (replacing ARP) and Duplicate Address Detection (DAD).

13.2 Ping and Traceroute Tests
Ping: Testing Connectivity

Uses ICMP Echo Request and Echo Reply to verify connectivity.

    Ping Loopback (127.0.0.1 or ::1): Verifies that the TCP/IP stack is installed and functioning on the local host.

    Ping Default Gateway: Verifies local network connectivity and that the router interface is operational.

    Ping Remote Host: Verifies communication across the internetwork.

Traceroute: Testing the Path

Traceroute (tracert in Windows) identifies the path (hops) between two hosts.

    How it works: It sends packets with increasing TTL values starting at 1.

    TTL=1: The first router decrements it to 0, drops the packet, and sends an ICMP Time Exceeded message back.

    Discovery: This reveals the IP address of every router in the path.

    Output: Shows round-trip time for each hop. An asterisk (*) indicates a lost packet or a router configured not to reply to ICMP.

Troubleshooting Summary
Tool	Primary Function	ICMP Message Used
Ping	Test reachability/latency	Echo Request / Echo Reply
Traceroute	Map path to destination	Time Exceeded / Echo Request
DAD	Ensure unique IPv6 address	Neighbor Solicitation
SLAAC	Auto-configure IPv6 address	Router Advertisement
Tags

#Cisco #CCNA #Networking #ICMP #Ping #Traceroute #IPv6 #Troubleshooting

Next Step: Since ICMP is often blocked by firewalls for security, would you like me to explain how to configure Access Control Lists (ACLs) to allow specific ICMP traffic on a Cisco router?