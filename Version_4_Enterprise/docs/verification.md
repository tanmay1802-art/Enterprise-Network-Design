# Verification

Screenshots proving each requirement works. Images are in `../screenshots/`.

## 1. DHCP (IPv4 and IPv6) across branches

Clients in every branch receive an IPv4 address from the central DHCP server (203.0.113.22) through relay, plus an IPv6 address, with DNS 203.0.113.23.

| Device | Department / site | IPv4 |
|---|---|---|
| PC3 | HR, KL | 192.168.20.4 |
| Laptop0 | Design, KL | 192.168.30.6 |
| PC9 | Management, KL | 192.168.10.12 |
| PC17 | Management, Malacca | 192.168.40.8 |
| PC23 | IT, JB | 192.168.100.6 |
| PC24 | Delivery, Penang | 192.168.80.6 |
| PC25 | R&D, Penang | 192.168.70.13 |
| PC26 | Finance, Penang | 192.168.60.14 |

![PC3](../screenshots/01-dhcp-ipv6-verification/pc3-hr-kl.png)
![Laptop0](../screenshots/01-dhcp-ipv6-verification/laptop0-design-kl.png)
![PC9](../screenshots/01-dhcp-ipv6-verification/pc9-management-kl.png)
![PC17](../screenshots/01-dhcp-ipv6-verification/pc17-management-malacca.png)
![PC23](../screenshots/01-dhcp-ipv6-verification/pc23-it-jb.png)
![PC24](../screenshots/01-dhcp-ipv6-verification/pc24-delivery-penang.png)
![PC25](../screenshots/01-dhcp-ipv6-verification/pc25-rnd-penang.png)
![PC26](../screenshots/01-dhcp-ipv6-verification/pc26-finance-penang.png)

## 2. EtherChannel and routing

`show etherchannel summary` shows Port-channel 1 in use (SU) with LACP and both member ports bundled (P), on the JB switches and on Malacca. The routing table on the JB multilayer switch shows routes learned through OSPF (`O`).

![EtherChannel Server_Switch](../screenshots/02-etherchannel-routing/etherchannel-jb-server-switch.png)
![EtherChannel JB multilayer](../screenshots/02-etherchannel-routing/etherchannel-jb-multilayer.png)
![EtherChannel Malacca](../screenshots/02-etherchannel-routing/etherchannel-malacca-1.png)
![EtherChannel Malacca](../screenshots/02-etherchannel-routing/etherchannel-malacca-2.png)
![Routing table](../screenshots/02-etherchannel-routing/ip-route-ospf-jb-multilayer.png)

## 3. Server farm services

Web, DNS and FTP servers in the JB server farm, and ping tests to the server addresses.

![Web server](../screenshots/03-server-services/web-server-1.png)
![Web server](../screenshots/03-server-services/web-server-2.png)
![Web server IP](../screenshots/03-server-services/web-server-ip.png)
![Browser](../screenshots/03-server-services/web-browser-suzlon.png)
![DNS server IP](../screenshots/03-server-services/dns-server-ip.png)
![DNS records](../screenshots/03-server-services/dns-records.png)
![Browser by name](../screenshots/03-server-services/web-browser-by-name.png)
![FTP server IP](../screenshots/03-server-services/ftp-server-ip.png)
![Ping 1](../screenshots/03-server-services/ping-test-1.png)
![Ping 2](../screenshots/03-server-services/ping-test-2.png)
![Ping 3](../screenshots/03-server-services/ping-test-3.png)
![Ping 4](../screenshots/03-server-services/ping-test-4.png)
![Ping 5](../screenshots/03-server-services/ping-test-5.png)

## 4. Layer 2 security

VLAN membership, port security, DHCP snooping and Dynamic ARP Inspection on the access switches (KL Management, HR and Design, Malacca, Penang and JB IT). Screenshots `l2-security-01` to `l2-security-20` are in `../screenshots/04-l2-security/`.

![L2 security 01](../screenshots/04-l2-security/l2-security-01.png)
![L2 security 02](../screenshots/04-l2-security/l2-security-02.png)
![L2 security 03](../screenshots/04-l2-security/l2-security-03.png)
![L2 security 04](../screenshots/04-l2-security/l2-security-04.png)
![L2 security 05](../screenshots/04-l2-security/l2-security-05.png)
![L2 security 06](../screenshots/04-l2-security/l2-security-06.png)
![L2 security 07](../screenshots/04-l2-security/l2-security-07.png)
![L2 security 08](../screenshots/04-l2-security/l2-security-08.png)
![L2 security 09](../screenshots/04-l2-security/l2-security-09.png)
![L2 security 10](../screenshots/04-l2-security/l2-security-10.png)
![L2 security 11](../screenshots/04-l2-security/l2-security-11.png)
![L2 security 12](../screenshots/04-l2-security/l2-security-12.png)
![L2 security 13](../screenshots/04-l2-security/l2-security-13.png)
![L2 security 14](../screenshots/04-l2-security/l2-security-14.png)
![L2 security 15](../screenshots/04-l2-security/l2-security-15.png)
![L2 security 16](../screenshots/04-l2-security/l2-security-16.png)
![L2 security 17](../screenshots/04-l2-security/l2-security-17.png)
![L2 security 18](../screenshots/04-l2-security/l2-security-18.png)
![L2 security 19](../screenshots/04-l2-security/l2-security-19.png)
![L2 security 20](../screenshots/04-l2-security/l2-security-20.png)

## 5. IoT

RFID readers, doors and webcams register to the IoT servers at KL and JB. At KL, rules on the IoT server lock and unlock the doors: a valid RFID status unlocks, an invalid one locks.

![KL IoT server IP](../screenshots/05-iot/iot-server-kl-ip.png)
![IoT service on](../screenshots/05-iot/iot-service-enabled.png)
![KL devices](../screenshots/05-iot/iot-devices-kl.png)
![JB login](../screenshots/05-iot/iot-login-jb.png)
![JB devices](../screenshots/05-iot/iot-devices-jb.png)
![Add rule](../screenshots/05-iot/iot-add-rule.png)
![Conditions](../screenshots/05-iot/iot-conditions-1.png)
![Conditions](../screenshots/05-iot/iot-conditions-2.png)
![Conditions](../screenshots/05-iot/iot-conditions-3.png)
