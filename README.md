# Enterprise Network Design

Cisco Packet Tracer projects that model multi-branch enterprise networks. Each version is a separate scenario and builds on the previous one, from basic static routing to a redundant, secured, multi-branch design.

## Versions

| Version | Scenario | Focus | Folder |
|---|---|---|---|
| V1 | MACSATech (KL, Penang, Johor, Kelantan) | Static routing, ring topology, subnetting, basic servers and IoT | [Version_1_Basic](Version_1_Basic) |
| V4 | Suzlon (KL, Malacca, JB, Penang) | HSRP, EtherChannel, OSPF, VLANs, DHCP relay, IPv6, Layer 2 security, IoT | [Version_4_Enterprise](Version_4_Enterprise) |

V1 and V4 use different scenarios. V4 is a larger, more advanced build.

## Version 4: Suzlon Enterprise Network (latest)

A four-site enterprise network with redundant gateways, a centralised server farm and Layer 2 security.

- HSRP at all four branches
- EtherChannel (LACP) between switches
- OSPF and a default static route
- VLSM addressing with IPv4 and IPv6
- Central DHCP server with relay across branches
- DNS, Web, FTP and Mail servers
- Port security, DHCP snooping and Dynamic ARP Inspection
- IoT devices with RFID-controlled doors
- Wireless LAN controllers with WPA2: in progress

Full details, screenshots and a troubleshooting case study are in [Version_4_Enterprise](Version_4_Enterprise).

## Version 1: MACSATech (Basic Static Routing)

A multi-branch network for a fictional company, MACSATech, connecting four branches across Malaysia (Kuala Lumpur, Penang, Johor and Kelantan). Branches are linked in a ring topology, and each branch uses a star topology.

**Tech stack and concepts**
- Simulation tool: Cisco Packet Tracer
- Routing: static routes across a ring of 4 routers
- Switching: Cisco 2960 switches, VLAN 1
- Addressing: custom subnetting (/24 for LANs, /30 for WAN serial links)
- Infrastructure: DNS, FTP, Email and Web servers; IoT devices (IP cameras, ACs, RFID, IP phones)

**Branches**
- Kuala Lumpur: Server Room, Reception, HR, IT
- Penang: Server Room, Reception, HR, IT
- Johor: Server Room, Administration, HR, Reception
- Kelantan: Server Room, Administration, HR, Reception

## How to View

1. Open the folder of the version you want.
2. Download the `.pkt` file.
3. Open it in Cisco Packet Tracer (8.0 or later recommended).
4. Hover over devices to check IP configurations, or open the router CLI to view routing tables.

## Tools

Cisco Packet Tracer, Cisco IOS CLI.
