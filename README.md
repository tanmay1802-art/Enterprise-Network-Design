# Suzlon Enterprise Network

A multi-branch enterprise network built in Cisco Packet Tracer for a fictional company with four sites: Kuala Lumpur (HQ), Malacca, Johor Bahru and Penang. This is a group project (Group CyberRoute, CT133-3-2 Switching and Routing Essentials, APU). My part (Tanmay Sarkar Emon): topology design, WLC (Penang and JB), EtherChannel and HSRP at all four branches, IoT server and devices, ISP cross-connection with NAT, and the final Packet Tracer merge.

## 1. Overview

- 4 branches connected over WAN links, each with its own departments and VLANs
- Redundant core at KL (CoreA / CoreB) and redundant gateways at every branch
- Centralised services (DHCP, DNS, Web, FTP) in the JB server farm
- Wireless LAN controllers with WPA2 at JB and Penang
- Layer 2 security on the access switches
- IoT devices (RFID readers, smart doors, CCTV) managed through IoT servers at KL and JB
- Dual ISP exit with NAT, a floating backup route and a backup ISP router
- Status: complete (final submission)

## 2. Network Design

| Area | Design |
|---|---|
| Addressing | VLSM with private ranges per branch. Public-style addressing (203.0.113.0/24, documentation range) for WAN links and the server farm. IPv6 dual-stack alongside IPv4 |
| Redundancy | HSRP (IPv4 and IPv6) at all 4 branches. KL uses CoreA/CoreB; the other branches pair a router with a multilayer switch as active/standby |
| Link aggregation | EtherChannel (LACP) between switches |
| Switching | VLANs, voice VLAN 110, 802.1Q trunks, native VLAN 999, DTP disabled |
| Routing | OSPF process 1 (area 0), default static route, inter-VLAN routing on multilayer switches |
| Wireless | Cisco WLC with VLAN interface, DHCP server and WPA2-PSK (JB and Penang) |
| Services | Central DHCP with relay, DNS, Web, FTP |
| Security | SSH v2, port security, DHCP snooping, Dynamic ARP Inspection, VLAN hopping protection |
| Management | RADIUS authentication and Syslog |
| Internet | Primary NAT exit on KL_Router_A, floating default route on KL_Router_B, Backup_ISP router |
| IoT | RFID reader controls a door lock through rules on the IoT server |

Full address plan: [docs/addressing-table.md](/Version_4_Enterprise/docs/addressing-table.md)

## 3. Verification

All evidence (about 290 screenshots with captions) is in [docs/verification-final.md](/Version_4_Enterprise/docs/verification-final.md). Screenshots are grouped in `screenshots/final-report/`:

| Folder | Content |
|---|---|
| 01-topology | Full network diagram |
| 02a-kl, 02b-malacca, 02c-jb, 02d-penang-and-dhcp | LAN/WAN configuration and verification per site |
| 03-wlc-wlan | WLC setup, SSID, AP groups, client verification |
| 04-etherchannel | EtherChannel verification |
| 05-hsrp | HSRP verification at all branches |
| 06-server-farm-and-iot | DNS, Web, FTP, DHCP and IoT |
| 07-connectivity-tests | Ping, traceroute, OSPF |
| 08-layer2-security | SSH, port security, DHCP snooping, DAI |
| 09-management-monitoring | RADIUS and Syslog |
| 10-isp-nat-internet | ISP links, NAT, backup route, backup ISP |

## 4. Repository Structure

```
Version_4_Enterprise/
├── README.md
├── packet-tracer/     Final Packet Tracer file (.pkt)
├── configs/           Exported running-configs
├── docs/              Addressing table and verification
└── screenshots/       Verification screenshots
```

## 5. How to Run

1. Install Cisco Packet Tracer.
2. Open the final `.pkt` file in `packet-tracer/`.
3. Wait for the network to converge (about 1 minute).
4. On any PC, go to Desktop > IP Configuration > DHCP. It should receive an IPv4 address from its branch pool.
5. Verify with ping to the local gateway and to the DHCP server (203.0.113.22).

## 6. Challenges and What I Learned

| Problem | Cause | Fix | What I learned |
|---|---|---|---|
| Only some PCs received an IP | DHCP snooping was on with the DHCP server's port untrusted, and the pools overlapped switch management IPs | Trusted the server-facing port and sized the pools to stop before the management IPs | Security features can break a working service. Add them one at a time and test after each |
| Native VLAN mismatch warnings between switches | Native VLAN 999 was set on one side of a trunk but not the other | Set the same native VLAN on both ends and disabled DTP negotiation | Trunk settings must match on both ends, and the CDP log shows where they do not |
| DHCP worked, then failed after a change | Stale leases and no saved copy to compare against | Cycled the DHCP service and kept a saved copy of the working file | Save a known-good version before every big change |
| Many branches and devices to keep consistent | Each branch repeats the same pattern | One addressing plan and one config pattern for all branches | A clear addressing plan up front prevents most mistakes |

## 7. Roadmap

- [x] VLANs, trunks, HSRP, EtherChannel, OSPF, inter-VLAN and inter-branch routing
- [x] DHCP (IPv4 and IPv6), DNS, Web, FTP
- [x] Port security, DHCP snooping, DAI, VLAN hopping protection
- [x] IoT / RFID devices
- [x] Wireless LAN controllers with WPA2 (JB and Penang)
- [x] Dual ISP, NAT, backup ISP, RADIUS and Syslog
- [x] Full topology diagram
- [x] Running-config dumps for all devices (see configs/)

## Skills Demonstrated

VLSM, VLANs and trunking, HSRP, EtherChannel, OSPF, IPv6, DHCP and relay, WLC/WPA2, Layer 2 security, NAT and ISP redundancy, IoT integration, network troubleshooting, technical documentation.
