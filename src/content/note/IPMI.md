---
title: IPMI
publishDate: "2025-04-23T13:20:00Z"
updateDate: "2025-04-23T14:32:00Z"
---


## Overview
Intelligent Platform Management Interface (IPMI) is a set of standardized specifications for hardware-based host management systems used for system management and monitoring. It acts as an autonomous subsystem and works independently of the host's BIOS, CPU, firmware, and underlying operating system. IPMI provides sysadmins with the ability to manage and monitor systems even if they are powered off or in an unresponsive state. It operates using a direct network connection to the system's hardware and does not require access to the operating system via a login shell. IPMI can also be used for remote upgrades to systems without requiring physical access to the target host.

IPMI is typically used in three ways:
- Before the OS has booted to modify BIOS settings
- When the host is fully powered down
- Access to a host after a system failure

When not being used for these tasks, IPMI can monitor a range of different things such as system temperature, voltage, fan status, and power supplies. It can also be used for querying inventory information, reviewing hardware logs, and alerting using SNMP. The host system can be powered off, but the IPMI module requires a power source and a LAN connection to work correctly.

The IPMI protocol was first published by Intel in 1998 and is now supported by over 200 system vendors, including Cisco, Dell, HP, Supermicro, Intel, and more. Systems using IPMI version 2.0 can be administered via serial over LAN, giving sysadmins the ability to view serial console output in band.

### Required Components
- **Baseboard Management Controller (BMC)**: A micro-controller and essential component of an IPMI
- **Intelligent Chassis Management Bus (ICMB)**: An interface that permits communication from one chassis to another
- **Intelligent Platform Management Bus (IPMB)**: Extends the BMC
- **IPMI Memory**: Stores system event logs, repository store data, and more
- **Communications Interfaces**: Local system interfaces, serial and LAN interfaces, ICMB and PCI Management Bus

## Footprinting the Service
IPMI communicates over port 623 UDP. Systems that use the IPMI protocol are called Baseboard Management Controllers (BMCs). BMCs are typically implemented as embedded ARM systems running Linux and connected directly to the host's motherboard. BMCs are built into many motherboards but can also be added to a system as a PCI card.

The most common BMCs we see during internal penetration tests are HP iLO, Dell DRAC, and Supermicro IPMI. If we can access a BMC during an assessment, we would gain full access to the host motherboard and be able to monitor, reboot, power off, or even reinstall the host operating system.

IPMI

| ipmi-version: | Version: | IPMI-2.0 | UserAuth: | PassAuth: auth_user, non_null_user |_ Level: 2.0 MAC Address: 14:03:DC:674:18:6A (Hewlett Packard Enterprise) Nmap done: 1 IP address (1 host up) scanned in 0.46 seconds


## Metasploit Version Scan
Metasploit can be used to scan for IPMI services.
msf6 auxiliary(scanner/ipmi/ipmi_version) > run [] Sending IPMI requests to 10.129.42.195->10.129.42.195 (1 hosts) [+] 10.129.42.195:623 - IPMI - IPMI-2.0 UserAuth(auth_msg, auth_user, non_null_user) PassAuth(password, [] Scanned 1 of 1 hosts (100% complete) [*] Auxiliary module execution completed


## Default Credentials
During internal penetration tests, we often find BMCs where the administrators have not changed the default password. Here are some default credentials to keep in mind:

| Product      | Username | Password |
|--------------|----------|----------|
| Dell iDRAC   | root     | calvin   |
| HP iLO       | Administrator | randomized 8-character string |
| Supermicro IPMI | ADMIN | ADMIN |

### Dangerous Settings
If default credentials don't work, an attacker may exploit flaws in the RAKP protocol in IPMI 2.0. This flaw can expose the password hash of any user account, which can be cracked offline using tools like Hashcat.

## Metasploit Hash Retrieval
To retrieve IPMI hashes, Metasploit's `ipmi_dumphashes` module can be used.


### Conclusion
IPMI is commonly found in network environments where sysadmins need to access servers remotely. However, it can pose security risks if not properly configured, such as exposing password hashes or default credentials. It is crucial to include IPMI in internal penetration tests to avoid unauthorized access.
