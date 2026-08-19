  # Enterprise Network Simulation — Cisco Packet Tracer

## Overview

A beginner-level enterprise network security lab built using Cisco Packet Tracer.

The project simulates a small enterprise network with internal departments, a DMZ-hosted web server, an ISP, and a **Cisco ASA firewall**. The main focus was understanding how routing, ACLs, NAT, and network segmentation work together to control traffic.

## Objectives

- Design a segmented enterprise-style network
- Configure a Cisco ASA firewall
- Separate Inside, DMZ, and Outside networks
- Configure static routing
- Implement extended ACLs
- Configure static NAT
- Host a web server in the DMZ
- Allow controlled HTTP access to the web server
- Block direct access from the outside network to internal networks
- Troubleshoot connectivity and firewall issues

## Network Design

### Inside Network

Three internal departments were created:

- HR: `192.168.10.0/24`
- Admin: `192.168.20.0/24`
- Dev:`192.168.30.0/24`

These networks represent trusted internal users.

### DMZ

The DMZ contains the public-facing web server:

- DMZ: `192.168.50.0/24`
- ASA DMZ: `192.168.50.1`
- Web Server: `192.168.50.10`

### Outside Network

The outside network represents the ISP/Internet side:

- ASA Outside: `192.168.100.2`
- Edge Router: `192.168.100.1`
- ISP Link: `203.0.113.0/30`
- Outside PC: `200.200.10.4`

## Security Configuration

The Cisco ASA was configured to enforce separation between the three zones.

ACLs were used to:

- Allow HR, Admin, and Dev to access the DMZ web server over HTTP
- Allow controlled HTTP access from the outside to the published web server
- Block direct access from the outside network to internal departments
- Restrict unnecessary traffic between security zones

Static NAT was configured so that the DMZ web server could be reached through the ASA's outside address.

The project also required static routes on the routers to ensure that both forward and return traffic had a valid path.

## Testing & Troubleshooting

Connectivity was tested from both internal and external networks.

The lab was intentionally used as a troubleshooting exercise. Issues encountered included missing routes, return-path problems, ACL behavior, and NAT verification.

Useful verification commands included:

show route
show access-list
show nat
show xlate


# The troubleshooting process reinforced an important networking principle:

A connection can fail even when the destination is reachable if the return path is missing or another security control blocks the traffic.

# Key Concepts
Network segmentation
Firewall security zones
Extended ACLs
Static routing
Static NAT
DMZ architecture
Least-privilege access
Network troubleshooting

# Limitations

This project is intentionally a basic educational simulation and is not a production-ready enterprise architecture.

The main limitations are:

- Cisco Packet Tracer does not fully reproduce the behavior and features of real Cisco ASA hardware.
- No firewall or router high availability is implemented.
- No IDS/IPS is included.
- No SIEM or centralized logging is included.
- The web server uses HTTP rather than HTTPS for simplicity.
- The ISP/Internet environment is highly simplified.
- The project focuses on IPv4 and does not include IPv6.

# Future Improvements

Possible extensions include:

HTTPS/TLS
IDS/IPS
SIEM and centralized logging
VPN connectivity
Firewall redundancy
More advanced VLAN and ACL policies
IPv6
More realistic Internet routing
Tools Used
Cisco Packet Tracer
Cisco ASA
Cisco Routers
Cisco Switches
Web Server
Outcome

This project provided hands-on experience with designing and securing a small enterprise network. More importantly, it helped bridge the gap between theoretical networking concepts and practical troubleshooting.

It demonstrates how routing, ACLs, NAT, firewall policies, and network segmentation work together to control traffic in an enterprise environment.

# Disclaimer

This project is for educational purposes only. The configuration and security design are simplified for use in Cisco Packet Tracer and should not be considered a production-ready enterprise deployment.
