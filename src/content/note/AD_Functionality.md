---
title: Active Directory Functionality
publishDate: "2025-04-29T13:00:00Z"
updateDate: "2025-04-29T14:32:00Z"
---

## FSMO Roles (Flexible Single Master Operation)

Active Directory (AD) uses five critical FSMO roles that ensure the smooth operation of AD across multiple domain controllers (DCs). Each role is designed to manage a particular function that requires a single authoritative server.

### 1. **Schema Master**
- **Role**: Manages the schema for the Active Directory forest, which defines the structure of objects and attributes.
- **Responsibilities**: Ensures all DCs in the forest are updated with schema changes.
- **Key Impact**: If the schema master fails, no changes can be made to the schema (e.g., adding a new attribute to an object).

### 2. **Domain Naming Master**
- **Role**: Manages domain names within the forest to ensure uniqueness.
- **Responsibilities**: Prevents the creation of duplicate domain names across the forest.
- **Key Impact**: Without this role functioning properly, domain name conflicts may arise when adding new domains.

### 3. **Relative ID (RID) Master**
- **Role**: Allocates blocks of relative IDs to DCs in the domain.
- **Responsibilities**: Ensures that each object within a domain has a unique Security Identifier (SID) by assigning RIDs to objects.
- **Key Impact**: If the RID Master is down, no new objects can be created, as they cannot be assigned a unique RID.

### 4. **PDC Emulator**
- **Role**: Acts as the primary Domain Controller for authentication and time synchronization.
- **Responsibilities**: Handles password changes, group policy application, and time synchronization. It is also responsible for backward compatibility with older Windows versions (e.g., Windows NT).
- **Key Impact**: If this role is unavailable, time synchronization will fail, password changes may not be propagated, and Group Policy may not be applied correctly.

### 5. **Infrastructure Master**
- **Role**: Ensures that cross-domain references are correctly resolved.
- **Responsibilities**: Translates object references between domains (e.g., resolving user SIDs and GUIDs in cross-domain scenarios).
- **Key Impact**: If not functioning, access control lists (ACLs) may show unresolved SIDs instead of user or group names.

#### FSMO Role Assignment
- These roles can be assigned to specific DCs based on organizational requirements. Issues with FSMO roles often lead to authentication failures and authorization problems.
  
---

## Domain and Forest Functional Levels

Functional levels in AD determine the available features and the compatibility with Windows Server versions.

### Domain Functional Levels
Each functional level unlocks certain features and is tied to the operating systems supported by the DCs.

| **Domain Functional Level** | **Features Available** | **Supported OS** |
| --------------------------- | ---------------------- | ---------------- |
| **Windows 2000 Native** | Universal groups, SID history, group nesting | Windows Server 2003, Windows 2000 |
| **Windows Server 2003** | Netdom.exe, well-known users, constrained delegation | Windows Server 2003, Windows Server 2008 R2 |
| **Windows Server 2008** | DFS replication, AES support for Kerberos | Windows Server 2008, Windows Server 2008 R2 |
| **Windows Server 2008 R2** | Managed Service Accounts | Windows Server 2008 R2, Windows Server 2012 |
| **Windows Server 2012** | KDC support for claims, compound authentication | Windows Server 2012, Windows Server 2012 R2 |
| **Windows Server 2012 R2** | Extra protection for Protected Users, Authentication Policy Silos | Windows Server 2012 R2 |
| **Windows Server 2016** | New Kerberos features, credential protection | Windows Server 2016, Windows Server 2019 |

#### Forest Functional Levels
Forest functional levels provide additional capabilities for Active Directory as new versions are released.

| **Version** | **Capabilities** |
| ----------- | ---------------- |
| **Windows Server 2003** | Forest trust, domain renaming, RODC |
| **Windows Server 2008** | Default to Server 2008 functional level, no new features |
| **Windows Server 2008 R2** | AD Recycle Bin to restore deleted objects |
| **Windows Server 2012** | No new features, but sets default to 2012 functional level |
| **Windows Server 2012 R2** | Default to 2012 R2 functional level |
| **Windows Server 2016** | Privileged Access Management (PAM) using MIM |

---

## Trusts in Active Directory

Trusts enable authentication across different domains and forests, allowing users to access resources in domains outside their own.

### Types of Trusts
- **Parent-child Trust**: Automatically created when a child domain is added to a parent domain. It is a transitive, two-way trust.
- **Cross-link Trust**: Set between two child domains to facilitate quicker authentication.
- **External Trust**: Non-transitive, used between domains in different forests. Typically, SID filtering is applied.
- **Tree-root Trust**: A two-way transitive trust between a forest root domain and a new tree-root domain.
- **Forest Trust**: A transitive trust between two forest root domains.

#### Trust Characteristics
- **Transitive vs. Non-transitive**:
  - A **transitive** trust extends the trust to any domains trusted by the child domain.
  - A **non-transitive** trust only trusts the specific child domain.
  
- **One-way vs. Two-way**:
  - **One-way**: Trust flows from the trusting domain to the trusted domain.
  - **Two-way**: Trust is mutual; both domains trust each other.

---

### Security Implications of Trusts
Improperly configured trusts can introduce significant security risks. For example:
- **Kerberoasting Attacks**: A malicious user can request service tickets for service accounts in a trusted domain and crack them offline to gain unauthorized access.
- **Bidirectional Trusts**: Mergers and acquisitions can introduce unreviewed trust relationships, creating unintentional attack paths.
- **Cross-domain Attacks**: Trusts set up without proper security checks can lead to unauthorized access across domains or forests.

---

## Conclusion

Active Directory’s functionality revolves around the FSMO roles, domain and forest functional levels, and trusts. Each element is crucial for maintaining an organized, efficient, and secure directory service, especially in large organizations with complex domain structures. Proper configuration and management of these features are essential to ensuring the integrity, availability, and security of the Active Directory environment.

