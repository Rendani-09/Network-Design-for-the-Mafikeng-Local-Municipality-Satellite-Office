# CMPG 325 — Mafikeng Local Municipality Satellite Office Network

## About the Project

This repository contains the portfolio of evidence for my **CMPG 325 Computer Networks Individual Semester Project**.

The project involves the design and implementation of a network solution for the **Mafikeng Local Municipality Satellite Office** using **Cisco Packet Tracer**. The repository documents the project from the initial network design through implementation, testing, troubleshooting, and final demonstration.

## Project Information

| Item | Details |
|---|---|
| Module | CMPG 325 — Computer Networks |
| Project | Individual Semester Project |
| Project ID | CMPG325-2026-099 |
| Client ID | CLI-099 |
| Organisation | Mafikeng Local Municipality Satellite Office |
| Industry | Municipal Services |
| Assigned IPv4 Block | `192.168.43.0/24` |
| Assigned Challenge | Static Routing — Multi-Router Path Control |
| Simulation Platform | Cisco Packet Tracer |

## Project Requirements

The network provides connectivity for the municipality's Public Counter, Licensing & Permits, Municipal Administration, Finance, and Shared Printer Zone.

- **Security constraint:** Public Counter staff must not access the Administration network.
- **Technical challenge:** Static Routing — Multi-Router Path Control.
- **Client change request (CR8):** A shared printer zone must serve two departments that previously could not print.

The selected departments for the shared printer service are **Licensing & Permits** and **Municipal Administration**.

## Network Overview

The implemented network uses three routers connected in a multi-router topology:

```text
MUN-R1 -------- MUN-R2 -------- MUN-R3
   |                |                |
MUN-SW1          MUN-SW2          MUN-SW3
```

The network is divided into five departmental/service VLANs using the assigned `192.168.43.0/24` address space. Static routing provides the required inter-network reachability across the implemented subnets, subject to the configured security policy. 802.1Q trunks carry the required VLANs between routers and switches.

### Implemented VLANs

| VLAN | Department / Service | Network |
|---|---|---|
| 10 | Public Counter (configured VLAN name: `CITIZEN_SERVICES`) | `192.168.43.0/27` |
| 20 | Licensing & Permits | `192.168.43.32/27` |
| 30 | Municipal Administration | `192.168.43.64/27` |
| 40 | Finance | `192.168.43.96/27` |
| 50 | Shared Printer Zone | `192.168.43.128/28` |

## Project Milestones

### Milestone 1 — Client Design Review
**Due: 28 August 2026 — Completed**

Covered the client requirements, physical and logical network design, IP addressing plan, VLAN design, security design, static routing design, and shared printer solution.

### Milestone 2 — Client Implementation Review
**Due: 2 October 2026 — Implementation and evidence completed**

Milestone 2 requires:

1. Working Packet Tracer file
2. Assigned feature implemented
3. Testing evidence
4. Updated GitHub portfolio

The working Packet Tracer project, implementation/testing report, and testing evidence are included in this repository.

### Final Submission
**Due: 16 October 2026**

The final submission includes the completed Packet Tracer project, GitHub portfolio of evidence, technical report, 15–20 minute INSET video demonstration, and any additional required files.

## Milestone 2 Implementation Status

The following functionality has been implemented and verified:

- VLANs 10, 20, 30, 40 and 50 configured on the appropriate switches.
- 802.1Q trunking configured between the switches and routers.
- Router-on-a-stick inter-VLAN gateways configured for the departmental VLANs.
- Point-to-point WAN links operational between MUN-R1–MUN-R2 and MUN-R2–MUN-R3.
- Static routes configured across MUN-R1, MUN-R2 and MUN-R3.
- Multi-router forwarding verified across the MUN-R1 → MUN-R2 → MUN-R3 path.
- CR8 shared printer access verified for Licensing & Permits and Municipal Administration.
- Extended ACL `PUBLIC_COUNTER_RESTRICTION` implemented on MUN-R1 to prevent Public Counter access to the Administration network.
- ACL operation verified through connectivity testing and ACL hit counters.

## Testing Summary

| Test | Expected Result | Result |
|---|---|---|
| CS-PC01 → VLAN 10 gateway | Reachable | Pass |
| LP-PC01 → VLAN 20 gateway | Reachable | Pass |
| ADM-PC01 → VLAN 30 gateway | Reachable | Pass |
| FIN-PC01 → VLAN 40 gateway | Reachable | Pass |
| MUN-R1 → MUN-R2 WAN | Reachable | Pass |
| MUN-R2 → MUN-R3 WAN | Reachable | Pass |
| LP-PC01 → PRINT-01 | Reachable | Pass |
| ADM-PC01 → PRINT-01 | Reachable | Pass |
| CS-PC01 → ADM-PC01 | Blocked | Pass — Blocked as required |
| LP-PC02 → ADM-PC01 | Reachable | Pass |
| LP-PC01 → ADM-PC01 traceroute | R1 → R2 → R3 | Confirmed |

The traceroute from LP-PC01 to ADM-PC01 confirmed the multi-router path through MUN-R1, MUN-R2 and MUN-R3. Security testing confirmed that traffic from the Public Counter network to the Administration network is denied while authorised traffic remains operational.

## Repository Contents

```text
Network-Design-for-the-Mafikeng-Local-Municipality-Satellite-Office/
│
├── README.md
├── Docs/
│   ├── Milestone_1_Client_Design_Review.pdf
│   └── Milestone_2_Client_Implementation_Review .pdf
├── Diagrams/
│   ├── Logical Topology.png
│   └── Physical Topology.png
├── Packet Tracer/
│   └── Mafikeng Local Municipality Satellite Office.pkt
└── Testing Evidence/
    ├── README.md
    └── 01–14 implementation and verification screenshots
```

### `Docs/`
Contains the Milestone 1 Client Design Review and Milestone 2 Client Implementation Review documentation.

### `Diagrams/`
Contains the physical and logical topology diagrams created during the design phase.

### `Packet Tracer/`
Contains the working Cisco Packet Tracer `.pkt` implementation for the Mafikeng Local Municipality Satellite Office network.

### `Testing Evidence/`
Contains 14 implementation and verification screenshots plus an evidence index explaining what each screenshot demonstrates.

## Current Status

**Milestone 2 implementation and evidence are complete and organised for the Client Implementation Review due 2 October 2026 at 23:55.**

The repository now contains the working Packet Tracer file, milestone documentation, topology diagrams, and organised testing evidence. Work remaining for the overall semester project relates to the final submission and technical demonstration due 16 October 2026.

## Documentation and Evidence

The project portfolio covers:

- Client requirements analysis
- Physical and logical topology
- Device inventory
- VLAN design and implementation
- VLSM and IP addressing
- Static routing and multi-router path verification
- Security ACL implementation and testing
- Shared printer solution (CR8)
- Connectivity testing and verification
- Troubleshooting and implementation evidence
