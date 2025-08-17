---
title: "RSVP Message Types & Fast Reroute"
category: Advanced
read_time: "22 min read"
description: "Deep dive into RSVP message flows and link protection fast reroute mechanisms in MPLS networks."
type: blog_post
id: rsvp-message-types
---

# RSVP Message Types & Fast Reroute
Resource ReSerVation Protocol (RSVP) plays a crucial role in MPLS Traffic Engineering and Fast Reroute mechanisms. This deep dive explores RSVP message types and how link protection fast reroute works in modern MPLS networks.
## RSVP Message Types
RSVP uses several message types to establish and maintain Label Switched Paths (LSPs):
### Path Messages
Path messages are sent by the ingress LSR (Label Switch Router) to establish an LSP:
- **Purpose:** Advertise the LSP requirements downstream
- **Content:** Traffic specifications, route objects, and constraints
- **Processing:** Each node records the previous hop and forwards downstream
### Resv Messages
Reservation messages travel upstream to allocate resources:
- **Purpose:** Reserve bandwidth and establish label bindings
- **Content:** Label objects, bandwidth reservations, and confirmations
- **Processing:** Resources are allocated at each hop
### PathErr Messages
Path error messages indicate problems during LSP setup:
- **Triggers:** Resource unavailability, routing loops, or constraint failures
- **Direction:** Sent upstream toward the ingress LSR
- **Action:** LSP setup is aborted or alternative paths are attempted
### ResvErr Messages
Reservation error messages report resource allocation failures:
- **Causes:** Insufficient bandwidth, label conflicts, or policy violations
- **Direction:** Sent downstream toward the egress LSR
- **Response:** Reservation is rolled back
## RSVP Fast Reroute
Fast Reroute provides sub-50ms protection against link and node failures in MPLS networks.
### Link Protection
Protects against individual link failures:
<h4>Setup Process:</h4>
<ol>
- **Backup tunnel creation:** Point of Local Repair (PLR) establishes backup LSPs
- **Merge point identification:** Determines where backup rejoins primary path
- **Path signaling:** Primary LSP includes backup tunnel information
</ol>
<h4>Failure Detection & Switching:</h4>
<ol>
- **Failure detection:** PLR detects link failure (BFD, hardware signals)
- **Traffic redirection:** Traffic immediately switches to backup tunnel
- **Notification:** PLR sends PathErr to trigger new path computation
- **Path reoptimization:** New primary path is established
</ol>
### Node Protection
Extends protection to cover entire node failures:
- **Next-Next Hop (NNHOP):** Backup tunnel bypasses the next downstream node
- **Enhanced coverage:** Protects against both link and node failures
- **Complexity trade-off:** More backup tunnels required but better protection
## Message Flow During Fast Reroute
### Normal Operation:
<ol>
- Path messages establish primary LSP
- Resv messages allocate resources and labels
- Traffic flows along primary path
- Periodic refresh maintains LSP state
</ol>
### Failure and Recovery:
<ol>
- Link failure detected at PLR
- Traffic immediately diverted to backup tunnel
- PathErr message sent to ingress LSR
- Ingress computes new path avoiding failed link
- New Path/Resv messages establish alternative LSP
- Traffic moves to new primary path
- Backup tunnel resources released
</ol>
## Advanced Considerations
### Bandwidth Protection
- **Admission control:** Backup tunnels must have sufficient bandwidth
- **Over-subscription:** Statistical multiplexing of backup resources
- **Priority schemes:** Higher priority traffic gets better protection
### Scalability Challenges
- **State explosion:** Each protected LSP requires backup tunnel state
- **Tunnel management:** Backup tunnels need lifecycle management
- **Resource optimization:** Sharing backup tunnels across multiple LSPs
## Best Practices
- **Failure detection:** Use BFD for rapid failure detection
- **Backup planning:** Ensure backup paths have adequate resources
- **Testing:** Regular failure simulation and recovery testing
- **Monitoring:** Track protection coverage and switching statistics
Understanding RSVP message flows and Fast Reroute mechanisms is essential for designing resilient MPLS networks that can recover from failures in milliseconds rather than seconds.