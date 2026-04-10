[[CCNA]]

Module 17: Build a Small Network
17.1 Devices in a Small Network

Small networks are the foundation of most businesses. Their design is usually simple, typically featuring a single router for WAN access (DSL, Cable, or Ethernet).
Key Considerations

    Device Selection: Factors include cost, port speed/type, expandability, and OS features.

    IP Addressing: Must be planned and documented.

        End devices: Often use DHCP.

        Servers/Printers: Require static IPs.

        Intermediary devices: Need static IPs for management.

    Redundancy: Essential to eliminate single points of failure by using duplicate equipment or links.

    Traffic Management: Priority should be given to real-time traffic (Voice/Video) using Quality of Service (QoS).

17.2 Small Network Applications and Protocols

    Network Applications: Directly network-aware (e.g., Web browsers).

    Application Layer Services: Programs that interface with the network for non-network-aware applications.

    Common Protocols:

        Security: Use SSH, SFTP, and HTTPS instead of Telnet, FTP, and HTTP.

        Email: SMTP (send), POP3/IMAP (retrieve).

        Real-time: VoIP and IP Telephony use RTP (Real-Time Transport Protocol).

17.3 Scaling to Larger Networks

To grow a network, an administrator needs:

    Documentation: Physical and logical topologies.

    Device Inventory: Comprehensive list of hardware.

    Budget: Fiscal planning for equipment.

    Traffic Analysis: Monitoring peak utilization and flow patterns to identify bottleneck areas.

17.4 Verify Connectivity
Ping Indicators (Cisco IOS)

    !: Success. Validates Layer 3 connectivity.

    .: Timeout. Problem along the path or destination didn't respond.

    U: Destination Unreachable. A router returned an ICMP error.

Traceroute (tracert or traceroute)

    Identifies where a path fails.

    Windows: Uses ICMP Echo Requests.

    Cisco IOS: Uses UDP.

    Baseline: Essential for comparing current performance against "normal" historical performance.

17.5 Host and IOS Commands

    Windows: ipconfig /all (Full details), ipconfig /displaydns (DNS cache), arp -a (MAC table).

    Linux/macOS: ifconfig or ip address.

    Cisco IOS:

        show ip interface brief: Quick status of all ports.

        show cdp neighbors detail: Discover IP addresses of directly connected Cisco devices.

        show running-config: Verify current settings.

17.6 - 17.7 Troubleshooting
Methodologies

    Identify the problem (Ask the user questions).

    Establish theory of probable causes.

    Test theory to determine the cause.

    Plan of action and implement the solution.

    Verify full functionality and implement preventive measures.

    Document findings (Crucial for future reference).

Common Scenarios

    Duplex Mismatch: One side is Full, the other is Half. Results in poor performance and collisions.

    APIPA (169.254.x.x): Occurs when a Windows client cannot reach a DHCP server.

    Default Gateway: If incorrect, the host can communicate locally but cannot reach remote networks/internet.

    DNS Issues: The link is up, but names won't resolve. Test by pinging an IP (e.g., 8.8.8.8) versus a name (google.com).

Tags

#Cisco #CCNA #SmallNetwork #Troubleshooting #Ping #Traceroute #DHCP #APIPA