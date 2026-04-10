[[CCNA]]
Module 15: Application Layer
15.1 Application, Presentation, and Session

The upper three layers of the OSI model define the functions that the TCP/IP Application Layer handles.
OSI Layer Functions

    Application Layer: The interface between the human-used software and the underlying network.

    Presentation Layer: * Formatting: Ensuring data is in a compatible format (e.g., GIF, JPEG, MPEG).

        Compression: Reducing file size for transmission.

        Encryption: Securing data at the source and decrypting it at the destination.

    Session Layer: Creates, maintains, and restarts "dialogs" (sessions) between applications.

15.2 Peer-to-Peer (P2P)

    Client-Server Model: A dedicated server provides resources to requesting clients.

    P2P Network: Devices connect without a dedicated server. Every device (peer) can act as both a client and a server simultaneously.

    P2P Applications: Software (like BitTorrent or Gnutella) that allows a device to act as a server for others while downloading data.

15.3 Web and Email Protocols
Web Protocols

    HTTP (TCP 80/8080): A request/response protocol for web traffic.

        GET: Requests data/files from the server.

        POST: Uploads data (like form entries).

        PUT: Uploads resources/content.

    HTTPS: A secure version of HTTP that uses encryption to protect data.

Email Protocols

    SMTP (TCP 25): Used to send email from a client to a server or between servers.

    POP (TCP 110): Retrieves mail from a server. Typically downloads and deletes the email from the server.

    IMAP (TCP 143): Retrieves mail from a server. Synchronizes the client and server; the message remains on the server until manually deleted.

15.4 IP Addressing Services
DNS (TCP/UDP 53)

Translates human-friendly domain names (cisco.com) into numeric IP addresses.

    Record Types:

        A: IPv4 address.

        AAAA: IPv6 address.

        NS: Authoritative Name Server.

        MX: Mail Exchange record.

    Hierarchy: Uses a tree structure (Root, Top-Level Domains like .com, Second-Level Domains).

DHCP (UDP 67 Server, 68 Client)

Automates the assignment of IP addresses, subnet masks, and gateways.

    DORA Process (IPv4):

        Discover: Client broadcasts to find a server.

        Offer: Server offers a lease.

        Request: Client accepts the specific offer.

        Acknowledge: Server finalizes the lease.

15.5 File Sharing Services

    FTP (TCP 20/21):

        Port 21: Control connection (commands/replies).

        Port 20: Data connection (actual file transfer).

    SMB (Server Message Block): A client-server request-response protocol used by Windows for sharing files and printers. Unlike FTP, SMB keeps a long-term connection, making the remote file feel "local."

Protocol Summary Table
Protocol	Use Case	Port	Transport
DNS	Name Resolution	53	UDP/TCP
HTTP	Web Browsing	80	TCP
HTTPS	Secure Web	443	TCP
SMTP	Sending Email	25	TCP
POP3	Receiving Email	110	TCP
IMAP	Syncing Email	143	TCP
DHCP	Auto-Addressing	67/68	UDP
FTP	File Transfer	20/21	TCP
Tags

#Cisco #CCNA #ApplicationLayer #HTTP #DNS #DHCP #FTP #Networking #ITN

Next Step: Since we've covered the Application layer, would you like me to create a troubleshooting cheat sheet for common connectivity issues involving DNS and DHCP?