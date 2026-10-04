# enterprise-network-design

Two network designs I built in **Cisco Packet Tracer** for my Bachelor of Cybersecurity at Victoria University.

---

## 1. Enterprise LAN Design: Multi-Building Network with High Availability

![LAN topology](lan-topology.png)

A 65-device LAN for a company with five buildings, five departments and a central server farm.

**What I built**
- Subnetted a `/16` block with **VLSM** and put each department on its own **VLAN**
- **Inter-VLAN routing** on two Layer-3 core switches (Cisco 3560)
- **HSRP** gateways split across both cores, so they share the load and one takes over if the other fails
- **Redundancy:** every access switch is dual-homed to both cores, there's an **LACP EtherChannel** between the cores, and **Rapid-PVST+** prevents loops
- **OSPF** between the core switches and the gateway router
- **NAT overload** so the whole network reaches the internet through one public IP
- Used the fewest devices and links that still met every requirement, to keep the cost down

**Devices:** 1 ISP router, 1 gateway router (2911), 2 multilayer switches (3560), 5 access switches (2960), 25 PCs, 25 IP phones, 6 servers

**Skills:** VLANs, Subnetting, HSRP, OSPF, EtherChannel, STP, NAT, Network Design

---

## 2. IPv4 to IPv6 WAN Migration: Multi-Site Company Network

![WAN topology](wan-topology.png)

A staged migration from IPv4 to IPv6 for a company with a head office and three branches, to get it ready for IoT devices. The head office and two branches move to IPv6 now. The third branch stays on IPv4 until a later phase.

**What I built**
- An **IPv6 addressing plan** from a `/48` allocation, using `/64` for every LAN and WAN link
- An **IPv4 plan** for the branch that stays on IPv4
- **OSPFv3** for the IPv6 sites and **OSPFv2** for the IPv4 site
- A three-way WAN link between the head office and two branches, so the migrated branches have a backup path
- **NAT-PT** on the head-office router, so IPv6 users can still reach the IPv4 branch server during the changeover
- Tested with routing tables, OSPF neighbour checks and end-to-end pings, and wrote a troubleshooting guide

**Skills:** IPv6, OSPFv2/v3, NAT-PT, WAN, Cisco IOS, Routing

---

## Tools
Cisco Packet Tracer · Cisco IOS CLI

## Author
**Jenish Gurung**, Bachelor of Cybersecurity, Victoria University
[LinkedIn](https://www.linkedin.com/in/jenish-gurung-7ba907326) · [GitHub](https://github.com/jish-tenz)
