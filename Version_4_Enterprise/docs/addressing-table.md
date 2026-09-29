# Addressing Table

Private IPv4 (VLSM) for KL, Malacca, Penang and the JB IT VLAN. Public-style addressing (203.0.113.0/24, RFC 5737 documentation range) for the WAN links and the JB server farm. IPv6 uses a /64 per VLAN from 2001:db8::/32 (RFC 3849) and /127 on point-to-point links.

## 1. VLAN / Department Addressing (IPv4 VLSM + IPv6)

Private IPv4 addressing is used for KL, Malacca, Penang, and the JB IT VLAN. Server Farm (VLAN 90) uses public-style addressing (RFC 5737 documentation range) since it must be externally reachable. IPv6 mirrors this with a /64 per VLAN from the 2001:db8::/32 documentation range (RFC 3849), VLAN ID encoded in hex.

| **VLAN** | **Dept** | **Site** | **IPv4 subnet (VLSM)** | **IPv4 GW** | **IPv6 subnet (/64)** | **IPv6 GW** |
| --- | --- | --- | --- | --- | --- | --- |
| 10 | Management | KL | 192.168.10.0/28 | 192.168.10.1 (HSRP VIP) | 2001:db8:a::/64 | 2001:db8:a::1 (VIP) |
| 20 | HR | KL | 192.168.20.0/27 | 192.168.20.1 (HSRP VIP) | 2001:db8:14::/64 | 2001:db8:14::1 (VIP) |
| 30 | Design | KL | 192.168.30.0/25 | 192.168.30.1 (HSRP VIP) | 2001:db8:1e::/64 | 2001:db8:1e::1 (VIP) |
| 110 | Voice (KL) | KL | 192.168.110.0/27 | 192.168.110.1 (HSRP VIP) | 2001:db8:6e::/64 | 2001:db8:6e::1 (VIP) |
| 40 | Management | Malacca | 192.168.40.0/28 | 192.168.40.1 | 2001:db8:28::/64 | 2001:db8:28::1 |
| 50 | Development | Malacca | 192.168.50.0/26 | 192.168.50.1 | 2001:db8:32::/64 | 2001:db8:32::1 |
| 60 | Finance | Penang | 192.168.60.0/27 | 192.168.60.1 | 2001:db8:3c::/64 | 2001:db8:3c::1 |
| 70 | R&D | Penang | 192.168.70.0/26 | 192.168.70.1 | 2001:db8:46::/64 | 2001:db8:46::1 |
| 80 | Delivery | Penang | 192.168.80.0/28 | 192.168.80.1 | 2001:db8:50::/64 | 2001:db8:50::1 |
| 90 | Server Farm | JB | 203.0.113.16/29 (public) | 203.0.113.17 | 2001:db8:5a::/64 | 2001:db8:5a::1 |
| 100 | IT | JB | 192.168.100.0/27 | 192.168.100.1 | 2001:db8:64::/64 | 2001:db8:64::1 |

## 2. WAN Link Addressing (IPv4 /30 + IPv6 /127)

All point-to-point links use the smallest usable block: /30 for IPv4 (2 usable hosts), /127 for IPv6 (RFC 6164 — both addresses of a /127 are valid host addresses, avoiding the ping-pong routing risk of /64 on a point-to-point link).

| **#** | **WAN Link** | **IPv4 (/30)** | **IPv6 (/127)** |
| --- | --- | --- | --- |
| 1 | KL_Router_A ↔ Malacca_Router | 203.0.113.0/30 | 2001:db8:ffff:1::/127 |
| 2 | KL_Router_B ↔ Malacca_Router | 203.0.113.20/30 | 2001:db8:ffff:2::/127 |
| 3 | KL_Router_A ↔ JB_Router | 203.0.113.4/30 | 2001:db8:ffff:3::/127 |
| 4 | KL_Router_B ↔ JB_Router | 203.0.113.24/30 | 2001:db8:ffff:4::/127 |
| 5 | KL_Router_A ↔ Penang_Router | 203.0.113.8/30 | 2001:db8:ffff:5::/127 |
| 6 | KL_Router_B ↔ Penang_Router | 203.0.113.28/30 | 2001:db8:ffff:6::/127 |
| 7 | KL_Router_A ↔ CoreA | 203.0.113.12/30 | 2001:db8:ffff:7::/127 |
| 8 | KL_Router_B ↔ CoreB | 203.0.113.32/30 | 2001:db8:ffff:8::/127 |
| 9 | KL_Router_A ↔ KL_Router_B (sync) | 203.0.113.36/30 | 2001:db8:ffff:9::/127 |
| 10 | KL_Router_A ↔ ISP (default route) | 203.0.113.40/30 | 2001:db8:ffff:a::/127 |
| 11* | KL_Router_B ↔ ISP2 (recommended — see Step 26B) | 203.0.113.44/30 | 2001:db8:ffff:b::/127 |

**Link 11 is a recommended addition, not from the original brief — it closes the redundancy **story** so **KL_Router_B** also has its own path to the Internet if **KL_Router_A** fails completely (see Step 26B).*

## 3. JB Server Farm hosts

| **Device** | **Connects to / role** | **IPv4** | **IPv6** |
| --- | --- | --- | --- |
| DNS Server | Server Farm, VLAN 90 | 203.0.113.19/29 | 2001:db8:5a::19/64 |
| Web Server | Server Farm, VLAN 90 | 203.0.113.20/29 | 2001:db8:5a::20/64 |
| FTP Server | Server Farm, VLAN 90 | 203.0.113.21/29 | 2001:db8:5a::21/64 |
| DHCP Server | Server Farm, VLAN 90 (central relay target) | 203.0.113.22/29 | 2001:db8:5a::22/64 |

