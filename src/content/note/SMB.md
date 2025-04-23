---
title: SMB
publishDate: "2025-04-16T13:20:00Z"
updateDate: "2025-04-17T14:32:00Z"
---

## What is SMB?
- **Server Message Block (SMB)** is a client-server protocol.
- Regulates access to files, directories, and network resources (e.g., printers).
- Allows information exchange between different system processes.

## History and Compatibility
- Initially part of OS/2 network operating system LAN Manager.
- Primarily used in Windows operating systems, ensuring backward compatibility.
- **Samba**: A free software project that enables SMB on Linux and Unix systems for cross-platform communication.

## How SMB Works
- Clients communicate with SMB servers to access shared files or services.
- Establishes a connection through a three-way handshake using TCP.
- Access rights are managed via **Access Control Lists (ACL)**, allowing fine-grained control over user permissions.

## Versions of SMB
- **CIFS**: Common Internet File System, a dialect of SMB, primarily SMB version 1.
- **SMB 1.0**: Introduced with Windows 2000.
- **SMB 2.0**: Introduced with Windows Vista, offering performance upgrades.
- **SMB 2.1**: Introduced with Windows 7, adding locking mechanisms.
- **SMB 3.0**: Introduced with Windows 8, featuring multichannel connections and encryption.
- **SMB 3.1.1**: Introduced with Windows 10, adding integrity checking and AES-128 encryption.

## Samba Configuration
- Samba settings are defined in the `/etc/samba/smb.conf` file.
- Key settings include:
  - `workgroup`: Defines the workgroup name.
  - `path`: Directory to which users are given access.
  - `guest ok`: Allows anonymous access.
  - `read only`: Controls file modification permissions.

## Dangerous Settings
- **browseable = yes**: Allows users to see available shares, which can be exploited by attackers.
- **guest ok = yes**: Permits access without a password, increasing security risks.
- **writable = yes**: Allows users to create and modify files, which can lead to unauthorized changes.

## Using smbclient
- Connect to SMB shares using the `smbclient` command.
- Example command to list shares:
  ```bash
  smbclient -N -L //10.129.14.128

## Accessing a Specific Share

```bash
smbclient //10.129.14.128/notes
```

## Enumeration Tools

- **Nmap**: Can be used to scan SMB services and gather information.
- **rpcclient**: Allows execution of specific functions on the SMB server for detailed information.
- **SMBMap** and **CrackMapExec**: Tools for enumerating SMB shares and permissions.
- **Enum4Linux-ng**: Automates many queries to gather information about SMB services.

## Security Considerations

- Anonymous access can lead to information leakage and potential attacks.
- Weak passwords and misconfigurations can expose the network to risks.
- Regular audits and proper configuration of SMB settings are essential for security.

## Conclusion

Understanding SMB and its configurations is crucial for network security.  
Tools like **Nmap**, **smbclient**, and **rpcclient** are valuable for enumeration and management of SMB services.  
Always be cautious with settings that allow guest access or browsing of shares.
