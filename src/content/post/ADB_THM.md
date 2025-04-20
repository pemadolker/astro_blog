---
title: "Active Directory Basics"
description: "Basics about active Directory "
publishDate: "2025-4-21"
tags: [ "Try Hack Me", "Active Directory", "Notes"]
---


## Introduction to Active Directory
- Active Directory (AD) is a crucial component in corporate environments, simplifying the management of users and devices.
- It centralizes administration, making it easier to manage large networks compared to handling each device individually.

## Room Objectives
- Understand what Active Directory is.
- Learn about Active Directory Domains and their components.
- Explore forests and domain trusts.

## Windows Domain
- A Windows domain is a collection of users and computers managed under a single administration.
- The central repository for managing these components is Active Directory, and the server running AD services is called a Domain Controller (DC).

### Advantages of a Windows Domain
1. **Centralized Identity Management**: Users can be managed from a single point, reducing administrative overhead.
2. **Security Policy Management**: Security policies can be applied across the network from AD.

### Real-World Example
- In educational institutions, students use a single set of credentials across multiple computers, thanks to AD. This allows for centralized authentication and policy enforcement.

## Active Directory Components
### Core Components
- **Active Directory Domain Services (AD DS)**: The main service that holds information about all objects in the network, including users, groups, machines, and more.

### Object Types in AD
1. **Users**: Represent individuals or services that need access to the network. Users are security principals and can be assigned privileges.
2. **Machines**: Each computer in the domain has a machine account, which is a security principal with limited rights.
3. **Security Groups**: Groups that simplify permission management by allowing multiple users to inherit access rights collectively.

### Organizational Units (OUs)
- OUs are containers that help organize users and machines based on similar policy requirements. They mimic the organizational structure of a business.

## Active Directory Users and Computers
- To manage users, groups, and machines, use the "Active Directory Users and Computers" tool.
- OUs can be created to reflect the business structure, allowing for efficient policy deployment.

### Default Containers
- **Builtin**: Contains default groups.
- **Computers**: Default location for machines joining the domain.
- **Domain Controllers**: Contains all DCs in the network.
- **Users**: Default users and groups applicable to the domain.

## Delegation
- Delegation allows specific users to manage certain OUs without needing full Domain Admin privileges. This is useful for tasks like password resets.

## Group Policy Objects (GPOs)
- GPOs are collections of settings that can be applied to OUs, allowing for tailored configurations and security baselines.
- GPOs are distributed via the SYSVOL share on the DC.

### Creating and Linking GPOs
- GPOs can be created to enforce policies, such as restricting access to the Control Panel or setting screen lock times.
- Policies can be linked to specific OUs or the root domain for broader application.

## Authentication Protocols
### Kerberos
- The default authentication protocol for modern Windows versions, using tickets for secure authentication.
- Users receive a Ticket Granting Ticket (TGT) to request service tickets for accessing resources.

### NetNTLM
- A legacy authentication protocol that uses a challenge-response mechanism.
- User passwords are never transmitted over the network, enhancing security.

## Trees and Forests
### Trees
- A tree is a collection of Windows domains that share the same namespace. For example, a root domain like thm.local can have subdomains like uk.thm.local and us.thm.local.

### Forests
- A forest is a collection of multiple trees that may have different namespaces. This structure allows for better management and resource access across different domains.

### Trust Relationships
- Trust relationships enable users in one domain to access resources in another domain. They can be one-way or two-way, allowing for flexible access control.

