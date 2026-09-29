# Enterprise Network Design

A multi-branch enterprise network built in Cisco Packet Tracer for a fictional company with four sites: **Kuala Lumpur (HQ), Malacca, Johor Bahru and Penang**. I designed the topology, planned the addressing (VLSM) and configured every device myself.

## 1. Overview

- 4 branches connected over WAN links, each with its own departments and VLANs
- Redundant core at KL (CoreA / CoreB) and redundant gateways at every branch
- Centralised services (DHCP, DNS, Web, FTP, Mail) in the server farm
- Layer 2 security on all access switches
- IoT devices (RFID readers, smart doors, CCTV) managed through IoT servers at KL and JB
- Status: core switching, routing, services, security and IoT **done**; wireless (WLC) **in progress**

## 2. Network Design

| Area | Design |
|---|---|
| Addressing | VLSM with private ranges per branch. Public-style addressing (203.0.113.0/24, documentation range) for WAN links and the server farm. IPv6 addressing alongside IPv4 |
| Redundancy | HSRP at all 4 branches. KL uses CoreA/CoreB; Malacca, JB and Penang pair each router with a multilayer switch as HSRP active/standby for the department VLANs |
| Link aggregation | EtherChannel (LACP) between switches |
| Switching | VLANs, trunks, dual-homed access switches (verified with CDP) |
| Routing | OSPF between branches, default static route, inter-VLAN routing on multilayer switches |
| Services | DHCP (centralised server with per-VLAN pools and relay), DNS, Web, FTP, Mail |
| Security | Port security, DHCP snooping, Dynamic ARP Inspection on the access switches |
| IoT | RFID reader controls door lock through rules on the IoT server (valid card unlocks, invalid card locks) |

## 3. Repository Structure

```
Version_4_Enterprise/
├── README.md
├── packet-tracer/
├── topology/
├── configs/
├── docs/
└── screenshots/
```

## 4. How to Run

1. Install Cisco Packet Tracer.
2. Open the `.pkt` file in `packet-tracer/`.
3. Wait for the network to converge (about 1 minute).
4. On any PC, go to Desktop > IP Configuration > DHCP. It should receive an IPv4 address from its branch pool.
5. Verify with `ping` to the local gateway and to the DHCP server (203.0.113.22).

Passwords and secrets in the config files are replaced with `<removed>`.

## 5. Troubleshooting Case Study: Intermittent DHCP, Packettracer file crash

**Symptom:** Some PCs in the HR and Management VLANs received an address, others got none. The behaviour changed between attempts. 

**Investigation:**
- Static IP pings to the gateway (HSRP VIP) and to the DHCP server worked, so L2, the uplinks and routing were fine. The problem was inside DHCP.
- `show ip dhcp snooping` on the server switch showed snooping enabled on the server VLAN, with only the uplinks trusted. The DHCP server's own port was untrusted, so the switch could drop the server's replies.
- The DHCP pools were also oversized. With a start address of .4 and a max user count
