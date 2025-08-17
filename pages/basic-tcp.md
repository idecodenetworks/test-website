---
title: "Basic TCP Communication"
category: Intermediate
read_time: "20 min read"
description: "Understanding TCP header fields, connection negotiation, and practical examples using HTTP and BGP applications."
type: blog_post
id: basic-tcp
---

# Basic TCP Communication
Transmission Control Protocol (TCP) is one of the most important protocols in networking, providing reliable, connection-oriented communication between applications. This article examines TCP header fields, connection establishment, and practical applications.
## TCP Header Structure
The TCP header contains several critical fields that enable reliable communication:
### Key Header Fields
- **Source and Destination Ports:** Identify the sending and receiving applications
- **Sequence Number:** Ensures data arrives in the correct order
- **Acknowledgment Number:** Confirms receipt of data
- **Window Size:** Implements flow control
- **Flags:** Control connection state (SYN, ACK, FIN, RST, etc.)
## Three-Way Handshake
TCP establishes connections using a three-way handshake:
<ol>
- **SYN:** Client sends synchronization request
- **SYN-ACK:** Server acknowledges and sends its own SYN
- **ACK:** Client acknowledges server's SYN
</ol>
## HTTP Over TCP
HTTP (Hypertext Transfer Protocol) relies on TCP for reliable web communication. When you browse a website:
- TCP establishes a connection to port 80 (HTTP) or 443 (HTTPS)
- HTTP requests are sent over the TCP connection
- The server responds with web content
- TCP ensures all data arrives correctly
## BGP Over TCP
Border Gateway Protocol (BGP) also uses TCP (port 179) for routing information exchange between autonomous systems. BGP requires reliable delivery of routing updates, making TCP an ideal choice.
## Connection Termination
TCP connections terminate using a four-way handshake with FIN flags, ensuring both sides agree to close the connection and all data has been transmitted successfully.