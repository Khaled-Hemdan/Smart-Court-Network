# Smart National Judicial Network

A unified, redundant national network design linking judicial sites across Egypt, built in **Cisco Packet Tracer** as a capstone project for the **DigiLians – Digital Pioneers Initiative** Intensive Diploma (Track: Infrastructure & Cybersecurity), in cooperation with the National Telecommunication Institute (NTI).

---

## Overview

Judicial data is often fragmented across provinces, with no centralized architecture. This creates security risks while data is in transit and leaves no real disaster-recovery plan.

This project proposes a **unified, redundant network** that connects three sites through dual-ISP OSPF routing, enabling secure, high-speed transfer of evidence and case archives.

**Target users:** provincial courts, prosecution offices, and a national headquarters.

## Network Topology

The design connects three sites:

| Site | Name | OSPF Area | Firewalls |
|------|------|-----------|-----------|
| BC | Branch Court | Area 0 | BC-FW1 / BC-FW2 |
| SC | Supreme Court | Area 2 | SC-FW1 / SC-FW2 |
| SH | State HQ | Area 1 | SH-FW1 / SH-FW2 |



For the full visual summary, see (Smart_National_Judicial_Network_Infographic.pdf).

## Architecture

The network is built in four layers:

1. **Dual-ISP WAN Backbone**
   Two ISPs (WE and Vodafone) connected via MPLS links, with OSPF running across Areas 0, 1 and 2.

2. **Redundant Firewall Layer**
   Two firewalls per site with HSRP gateway failover, hardened with SSHv2 and local AAA.

3. **Core Distribution Layer**
   Two multilayer switches per site (ML1 / ML2) connected with LACP EtherChannel trunks (802.1Q).

4. **Access & VLAN Layer**
   Six VLANs per site, with sticky-MAC port security on access ports:
   `Employee` · `Guest` · `IT` · `Lawyers` · `Judges` · `Voice`

## Key Features

- **3-site redundant topology** with dual-ISP uplinks
- **Multi-area OSPF** routing (Areas 0 / 1 / 2)
- **HSRP** gateway redundancy for failover
- **Redundant ASA-style firewalls** at every site
- **LACP EtherChannel** trunks (802.1Q) between core switches
- **VLAN segmentation** per department (18 VLANs in total)
- **Port security** with sticky MAC addresses
- **Device hardening:** SSHv2, local AAA, enable-secret encryption
- **Disaster recovery:** failover tested across links and devices
- **Structured IP addressing plan** with 30+ `/30` WAN links

## Implementation Steps

1. Design the 3-site topology (BC, SC, SH) with dual-ISP uplinks.
2. Configure OSPF multi-area routing (Areas 0 / 1 / 2).
3. Harden the firewalls: SSHv2, local AAA, and enable-secret encryption.
4. Build VLANs per department with LACP EtherChannel trunks.
5. Apply port security and test failover / disaster recovery.

## Tools & Technologies

- Cisco Packet Tracer
- OSPF (multi-area)
- Dual-ISP WAN (ISP-WE, ISP-VF) over MPLS
- HSRP
- ASA-style firewalls
- LACP EtherChannel (802.1Q)
- VLAN segmentation
- Port security (sticky MAC)
- SSHv2 and local AAA

## Results

| Metric | Value |
|--------|-------|
| Redundant sites | 3 |
| ISPs | 2 (WE & VF) |
| OSPF areas | 3 |
| Segmented VLANs | 18 |

## Deliverables

- Unified national judicial network
- Secure evidence / archive transfer
- Disaster-recovery-ready infrastructure
- Structured IP addressing plan (30+ `/30` WAN links)
- Full topology documentation




*DigiLians · National Telecommunication Institute (NTI) · Graduation Project 2026/2027*


