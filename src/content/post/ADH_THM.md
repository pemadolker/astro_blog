---
title: "Breaching Active Directory"
description: "Notes for self on active Directory Breaching"
publishDate: "2025-4-21"
tags: [ "Try Hack Me", "Active Directory", "Notes"]
---

## Overview of Active Directory
- Active Directory (AD) is utilized by around 90% of Global Fortune 1000 companies, especially those using Microsoft Windows.
- It is the primary suite for managing Windows domain networks and is crucial for Identity and Access Management (IAM).
- Due to its significance, AD is a prime target for attackers.

## Initial Access to AD
- To exploit AD misconfigurations for privilege escalation and lateral movement, initial access is required.
- Acquiring valid AD credentials is essential, and even low-privileged accounts can be sufficient for further enumeration.
- Various methods exist to breach AD, including:
  - NTLM Authenticated Services
  - LDAP Bind Credentials
  - Authentication Relays
  - Microsoft Deployment Toolkit (MDT)
  - Configuration Files

## Connecting to the Network
- **AttackBox**: Automatically connects to the network; DNS configuration is necessary.
- **Other Hosts**: Use OpenVPN to connect to the network and configure DNS accordingly.
- **Debugging DNS**: Essential for AD testing; common issues can arise from incorrect DNS settings.

## Credential Acquisition Techniques
### Open Source Intelligence (OSINT)
- OSINT can reveal publicly disclosed credentials through:
  - User queries on forums.
  - Hardcoded credentials in scripts on platforms like GitHub.
  - Past breaches listed on sites like HaveIBeenPwned.

### Phishing
- Phishing attacks can trick users into providing credentials or executing malicious software, allowing attackers to impersonate users.

### NTLM and NetNTLM
- NTLM is a suite of security protocols for user authentication in AD.
- NetNTLM is a challenge-response mechanism used by various services, which can be exploited if exposed to the internet.

### Password Spraying
- A method to test a single password against multiple usernames to avoid account lockouts.
- Tools like Hydra can assist, but custom scripts provide more control.

### LDAP Authentication
- LDAP is another method for AD authentication, often used by third-party applications.
- Credentials can be extracted from configuration files or through LDAP Pass-back attacks.

### Microsoft Deployment Toolkit (MDT) and PXE Boot
- MDT automates OS deployment; PXE Boot allows devices to install OS over the network.
- Attackers can exploit PXE Boot images to inject malicious configurations or scrape credentials.

### Configuration Files
- Configuration files from applications (e.g., McAfee) can contain stored credentials.
- Tools like SQLite can be used to extract and decrypt these credentials.

## Mitigations
- **User  Awareness and Training**: Educating users about credential security and phishing risks.
- **Limit Exposure**: Restricting access to AD services from the internet.
- **Network Access Control (NAC)**: Preventing rogue devices from connecting to the network.
- **Enforce SMB Signing**: Protecting against SMB relay attacks.
- **Principle of Least Privilege**: Minimizing permissions for service accounts to reduce risk.

## Conclusion
- Understanding the various attack vectors and methods for breaching AD is crucial for security assessments.
- Continuous learning and updating of methodologies are necessary to stay ahead of potential threats.