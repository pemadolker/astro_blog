---
title: Simple Network Management Protocol
publishDate: "2025-04-16T13:20:00Z"
updateDate: "2025-04-17T14:32:00Z"
---

## What is SNMP?
- **Simple Network Management Protocol (SNMP)** is used to monitor and manage network devices.
- It allows for configuration tasks and remote management of devices like routers, switches, servers, and IoT devices.
- The current version, **SNMPv3**, enhances security but increases complexity.

## How SNMP Works
- SNMP operates over **UDP**:
  - **Port 161**: Used for sending control commands and querying devices.
  - **Port 162**: Used for receiving SNMP traps, which are unsolicited notifications sent from devices to the SNMP manager.
- SNMP clients (managers) can request information from devices, and devices can send traps to notify the manager of events.

## Management Information Base (MIB)
- **MIB** is a standardized format for storing device information.
- It contains a hierarchical structure of **Object Identifiers (OIDs)**, which uniquely identify SNMP objects.
- MIB files are written in **Abstract Syntax Notation One (ASN.1)** format.

## Object Identifier (OID)
- An **OID** is a unique identifier for a node in the MIB hierarchy.
- OIDs are represented as a sequence of numbers separated by dots (e.g., `1.3.6.1.2.1`).

## SNMP Versions
1. **SNMPv1**:
   - First version, widely used in small networks.
   - Lacks authentication and encryption, making it insecure.

2. **SNMPv2**:
   - Introduced community-based security (SNMPv2c).
   - Still lacks encryption; community strings are sent in plaintext.

3. **SNMPv3**:
   - Introduces authentication and encryption.
   - More complex configuration with enhanced security features.

## Community Strings
- Community strings act as passwords to control access to SNMP data.
- Many organizations still use SNMPv2, which poses security risks due to plaintext transmission of community strings.


# Dangerous Settings
- **rwuser noauth**: Grants access to the full OID tree without authentication.
- **rwcommunity <community string> <IPv4 address>**: Allows access to the full OID tree from any source.

# Footprinting SNMP Services
Tools for SNMP enumeration include:
- **snmpwalk**: Queries OIDs for information.
- **onesixtyone**: Brute-forces community strings.
- **braa**: Enumerates OIDs using known community strings.


## Conclusion
- SNMP is a powerful tool for network management but poses security risks if not configured properly.

- Understanding SNMP versions, community strings, and configuration settings is crucial for secure network management.

- Experimenting with SNMP in a controlled environment can provide valuable insights into its functionality and security implications.