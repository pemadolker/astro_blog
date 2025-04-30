---
title: Networking protocols used in AD environments.
publishDate: "2025-04-29T20:00:00Z"
updateDate: "2025-04-29T20:32:00Z"
---



# Kerberos, DNS, LDAP, MSRPC

This notes covers the critical networking protocols used in Active Directory environments.

---

## Kerberos

Kerberos is the default authentication protocol for domain accounts since Windows 2000. It is an open standard enabling interoperability with other systems. It ensures **mutual authentication** and avoids transmitting passwords over the network by using **ticket-based authentication**.

### Key Concepts

- **Stateless Authentication** using encrypted tickets.
- **Key Distribution Center (KDC)**: Composed of two services: Authentication Service (AS) and Ticket Granting Service (TGS).
- **Tickets**: TGT (Ticket Granting Ticket) and TGS (Ticket Granting Service ticket).

### Kerberos Authentication Flow

1. **AS-REQ**: User sends a request encrypted with their password.
2. **AS-REP**: If decrypted successfully, KDC issues TGT encrypted with `krbtgt` key.
3. **TGS-REQ**: User presents TGT to request access to a service.
4. **TGS-REP**: KDC returns a TGS encrypted with the service's NTLM hash.
5. **AP-REQ**: TGS is presented to the target service. If valid, access is granted.

### Ports

- **TCP/UDP 88**

---

## DNS

DNS is used by Active Directory for locating Domain Controllers and for communication.

### Functions

- Resolves hostnames to IPs.
- Maintains **Service (SRV) Records** to locate domain services.
- Uses **Dynamic DNS** to update changes in IPs automatically.

### Commands

- **Forward Lookup**
  ```bash
  nslookup INLANEFREIGHT.LOCAL
  ```
- **Reverse Lookup**
  ```bash
  nslookup 172.16.6.5
  ```
- **Hostname to IP**
  ```bash
  nslookup ACADEMY-EA-DC01
  ```

### Ports

- **UDP 53** (default)
- **TCP 53** (fallback when large messages)

---

## LDAP

LDAP (Lightweight Directory Access Protocol) is the protocol used to access and manage directory services like Active Directory.

### Key Points

- **Port 389** for standard LDAP.
- **Port 636** for LDAP over SSL (LDAPS).
- AD is a directory service that uses LDAP like Apache uses HTTP.

### Authentication

- **Simple Authentication**: Username/password.
- **SASL Authentication**: Uses external services like Kerberos.

> LDAP by default transmits messages in **cleartext**, so encryption (e.g., TLS) is recommended.

---

## MSRPC

MSRPC is Microsoft's implementation of the Remote Procedure Call used in client-server communication.

### Interfaces

| Interface | Description |
|----------|-------------|
| **lsarpc** | Used to manage domain security policies and interactive authentication services. |
| **netlogon** | Authenticates users/services within domain. |
| **samr** | Remote access to Security Account Manager; used to manage users, groups, and can be abused for enumeration. |
| **drsuapi** | Handles replication tasks; can be used to extract domain database (NTDS.dit). |

> **Security Note**: Many RPC interfaces can be abused by attackers. Best practices include restricting access and auditing usage.

---

## Summary

Active Directory heavily depends on:
- **Kerberos**: Secure authentication
- **DNS**: Service discovery
- **LDAP**: Directory access and authentication
- **MSRPC**: Remote procedure call interfaces for system operations

