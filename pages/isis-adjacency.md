---
title: "ISIS Adjacency Basics"
category: Basic
read_time: "10 min read"
description: "Basic ISIS Adjacency Setup and packet Flow "
type: blog_post
id: isis-adjacency
---

# Basic IP Networking Within a LAN
Understanding how different protocols interact within a Local Area Network (LAN) is fundamental to network engineering. This article explores the interaction between DNS, DHCP, ARP, HTTP, SCTP, and FTP protocols in a typical LAN environment.
## The Protocol Stack
In a typical LAN environment, multiple protocols work together to enable communication between devices. Each protocol serves a specific purpose:
### DHCP (Dynamic Host Configuration Protocol)
DHCP automates the assignment of IP addresses, subnet masks, default gateways, and DNS servers to network devices. When a device connects to the network, it broadcasts a DHCP DISCOVER message to find available DHCP servers.
### DNS (Domain Name System)
DNS translates human-readable domain names into IP addresses. This allows users to access websites using memorable names rather than numeric IP addresses. DNS operates on both TCP and UDP port 53.
### ARP (Address Resolution Protocol)
ARP maps IP addresses to MAC addresses within the local network segment. Before any IP communication can occur, devices must know the hardware addresses of their communication partners.
## Protocol Interactions
These protocols work together seamlessly:
<ol>
- A device connects and uses DHCP to obtain network configuration
- When accessing a website, DNS resolves the domain name to an IP address
- ARP determines the MAC address for local communication
- HTTP/HTTPS carries the web traffic over TCP
- FTP may be used for file transfers, also over TCP
</ol>
## Practical Considerations
Understanding these interactions helps in troubleshooting network issues. Common problems include DHCP exhaustion, DNS resolution failures, and ARP table corruption. Network engineers must understand how these protocols interact to design efficient and reliable networks.