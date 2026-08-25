# CMPG 325 — Mafikeng Local Municipality Satellite Office Network

## About the Project

This repository contains the portfolio of evidence for my **CMPG 325 Computer Networks Individual Semester Project**.

The project involves the design and implementation of a network solution for the **Mafikeng Local Municipality Satellite Office** using **Cisco Packet Tracer**.

The repository documents the project from the initial network design through implementation, testing, troubleshooting, and final demonstration.

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

The network is designed to provide connectivity for the municipality's:

- Public Counter 
- Licensing & Permits
- Municipal Administration
- Finance
- Shared Print Services

The project also includes the following specific requirements:

- **Security constraint:** Public Counter staff must not access the administrative network.
- **Technical challenge:** Static Routing with multi-router path control.
- **Client change request (CR8):** A shared printer zone must serve two departments that currently cannot print.

The selected departments for the shared printer service are **Licensing & Permits** and **Municipal Administration**.

Detailed requirements, design decisions, topology diagrams, subnetting calculations and IP addressing are documented in the relevant milestone documentation.

## Network Overview

The proposed network uses three routers connected in a multi-router topology:

```text
MUN-R1 -------- MUN-R2 -------- MUN-R3
   |                |                |
MUN-SW1          MUN-SW2          MUN-SW3
```

The network is logically divided into departmental VLANs and subnets using the assigned `192.168.43.0/24` address space.

Further technical details are available in the project documentation contained in this repository.

## Project Milestones

### Milestone 1 — Client Design Review
**Due: 28 August 2026**

Covers the initial client requirements, physical and logical network design, IP addressing plan, and project repository.

### Milestone 2 — Client Implementation Review
**Due: 2 October 2026**

Includes:

1. Working Packet Tracer file
2. Assigned feature implementation
3. Testing evidence
4. Updated GitHub portfolio

### Final Submission
**Due: 16 October 2026**

Includes the completed network, portfolio of evidence, technical report, and project demonstration.

## Repository Contents

```text
CMPG325-Mafikeng-Municipality-Network/
│
├── README.md
├── docs/
├── diagrams/
├── packet-tracer/
└── evidence/
```

### `docs/`
Project documentation and milestone submissions.

### `diagrams/`
Physical and logical network topology diagrams.

### `packet-tracer/`
Cisco Packet Tracer project files.

### `evidence/`
Configuration, testing, verification, and troubleshooting evidence collected during development.

## Current Status

**Current Phase:** Milestone 1 — Client Design Review

The initial network design, addressing plan, topology, and project documentation are currently being prepared for the Milestone 1 submission.

## Documentation

Detailed technical information is maintained in the project documents.

This includes:

- Client requirements analysis
- Physical topology
- Logical topology
- Device inventory
- VLAN design
- VLSM and IP addressing
- Static routing design
- Security and ACL design
- Shared printer solution
- Implementation evidence
- Testing and troubleshooting results
