# Milestone 2 — Testing Evidence

This folder contains implementation and verification evidence for the CMPG 325 Computer Networks Individual Semester Project for the Mafikeng Local Municipality Satellite Office.

**Project ID:** CMPG325-2026-099  
**Client:** Mafikeng Local Municipality Satellite Office  
**Assigned IPv4 block:** `192.168.43.0/24`  
**Technical challenge:** Static Routing — Multi-Router Path Control  
**Client security constraint:** Public Counter staff must not access the Administration network.  
**Change Request CR8:** A shared printer zone must provide printer access to Licensing & Permits and Municipal Administration.

## Evidence Index

| # | Evidence file | What it demonstrates |
|---|---|---|
| 01 | `01-MUN-SW1-VLANs-and-Trunk.png` | VLAN 10 (Public Counter; configured VLAN name `CITIZEN_SERVICES`) and VLAN 20 (Licensing & Permits) are configured on MUN-SW1, with the router uplink operating as an 802.1Q trunk. |
| 02 | `02-MUN-SW2-Printer-VLAN-and-Trunk.png` | VLAN 50 (Shared Printer Zone) is configured on MUN-SW2 and carried over the 802.1Q trunk to MUN-R2. |
| 03 | `03-MUN-SW3-VLANs-and-Trunk.png` | VLAN 30 (Administration) and VLAN 40 (Finance) are configured on MUN-SW3, with the router uplink operating as an 802.1Q trunk. |
| 04 | `04-MUN-R1-Static-Routing.png` | MUN-R1 routing table, including static routes toward the remote Administration, Finance and Shared Printer networks through MUN-R2. |
| 05 | `05-MUN-R2-Static-Routing.png` | MUN-R2 routing table, showing static routes toward networks located behind both MUN-R1 and MUN-R3. |
| 06 | `06-MUN-R3-Static-Routing.png` | MUN-R3 routing table, including static routes toward the remote Public Counter, Licensing & Permits and Shared Printer networks through MUN-R2. |
| 07 | `07-Multi-Router-Path-Traceroute.png` | Traceroute from the Licensing & Permits network to Administration. The path traverses MUN-R1 → MUN-R2 → MUN-R3, verifying the assigned multi-router static-routing challenge. |
| 08 | `08-LP-PC01-to-Shared-Printer.png` | Successful connectivity from Licensing & Permits to PRINT-01 (`192.168.43.130`), verifying the first authorised department in CR8. |
| 09 | `09-ADM-PC01-to-Shared-Printer.png` | Successful connectivity from Municipal Administration to PRINT-01 (`192.168.43.130`), verifying the second authorised department in CR8. |
| 10 | `10-Public-Counter-to-Administration-Blocked.png` | Public Counter traffic to the Administration network is blocked, satisfying the client security constraint. |
| 11 | `11-Authorised-Access-to-Administration.png` | Successful Licensing & Permits connectivity to Administration, demonstrating that legitimate routed traffic remains operational while the Public Counter restriction is enforced. |
| 12 | `12-MUN-R1-Public-Counter-ACL.png` | The `PUBLIC_COUNTER_RESTRICTION` extended ACL on MUN-R1 and its match counters, providing evidence that restricted traffic is being matched by the deny rule. |
| 13 | `13-MUN-R2-Interface-Status.png` | MUN-R2 interface status, showing the VLAN 50 gateway subinterface and both serial WAN interfaces operational (`up/up`). |
| 14 | `14-MUN-R1-ACL-Application.png` | MUN-R1 configuration showing the Public Counter ACL applied inbound on `GigabitEthernet0/0.10`, close to the source of the restricted traffic. |

## Static Routing Verification

The network uses three routers in the path:

`MUN-R1 → MUN-R2 → MUN-R3`

The traceroute evidence demonstrates traffic from the Licensing & Permits network reaching Administration through the following Layer 3 path:

`192.168.43.33 → 192.168.43.146 → 192.168.43.150 → 192.168.43.66`

This confirms end-to-end connectivity across multiple routers using manually configured static routes.

## CR8 — Shared Printer Zone

PRINT-01 is located in VLAN 50 at `192.168.43.130/28`, with default gateway `192.168.43.129`. Testing confirms that both departments selected for CR8 can reach the shared printer:

- Licensing & Permits (VLAN 20)
- Municipal Administration (VLAN 30)

The printer is centralised behind MUN-R2, requiring routed connectivity from both sides of the three-router topology.

## Security Constraint Verification

An extended named ACL, `PUBLIC_COUNTER_RESTRICTION`, is applied inbound to MUN-R1 subinterface `GigabitEthernet0/0.10`. It denies traffic originating from the Public Counter subnet (`192.168.43.0/27`) when the destination is the Administration subnet (`192.168.43.64/27`) and permits other IP traffic.

The evidence includes both the failed Public Counter-to-Administration connectivity test and the ACL match counters. A successful Licensing & Permits-to-Administration test is also included to demonstrate that the restriction is selective rather than a general routing failure.

## Result

The evidence in this folder demonstrates functioning VLAN segmentation, 802.1Q trunking, inter-router static routing, multi-router path control, CR8 shared-printer connectivity, operational router interfaces, and enforcement of the required Public Counter security restriction.
