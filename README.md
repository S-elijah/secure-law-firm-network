# Secure Law Firm Network

A segmented network for a law firm, built in Cisco Packet Tracer. Client
case files are sensitive, so the goal was simple: reception and guests
must never share a network with lawyers or the case-file server.

## Network layout
| VLAN | Purpose | Subnet |
|------|---------|--------|
| 10 | Reception & Guest | 192.168.10.0/24 |
| 20 | Lawyers | 192.168.20.0/24 |
| 30 | Servers (Case Files DB) | 192.168.30.0/24 |

## What I implemented
- VLANs 10/20/30 across three access switches
- 802.1Q trunking between switches and router
- Inter-VLAN routing with router-on-a-stick (Gi0/0.10, .20, .30)
- DHCP for every VLAN (verified: PC1 received 192.168.10.22)
- Device hardening: enable secret, console/VTY passwords,
  password encryption, login banner

## Verification
Screenshots in /screenshots: `show vlan brief`, `show interfaces trunk`,
`show ip interface brief`, `show ip dhcp pool`.

## Design documents
Topology, data flow diagram and use case diagram are in /diagrams.

## Planned (Phase 2)
- ACLs so only lawyers reach VLAN 30
- Linux firewall (iptables/UFW) at the edge
- SSH instead of Telnet
- Python script to monitor logs and alert on failed access

## Lessons learned
(Write 2-3 real ones. Example: "My trunk allowed all VLANs until I
restricted it to 10, 20, 30.")

## Tools
Cisco Packet Tracer, Cisco IOS CLI

Built by Elijah Senabulya, Nigel Tech Solutions, Kampala.
