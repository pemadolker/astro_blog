---
title: Active Directory user and machine accounts
publishDate: "2025-04-29T13:00:00Z"
updateDate: "2025-04-29T14:32:00Z"
---

# User and Machine Accounts

## Introduction
User accounts are created on both local systems (not joined to Active Directory (AD)) and in Active Directory to give a person or program the ability to log in and access resources based on their rights. When a user logs in, the system verifies their password and creates an access token. This token describes the security content of a process or thread and includes the user's security identity and group membership. Whenever a user interacts with a process, this token is presented.

### Purpose of User Accounts
- Allow employees/contractors to log in and access resources.
- Run programs or services under a specific security context.
- Manage access to objects and properties such as network file shares, applications, etc.
- Users can be assigned to groups that control access to resources.

### Benefits of Grouping Users
- Simplifies administration by assigning privileges to a group.
- Helps manage privileges more effectively.

### Types of Accounts
- **Standard User Accounts**: Each employee or contractor typically has one user account.
- **Service Accounts**: Used for running applications or services in the background.
- **Disabled Accounts**: Common for former employees or temporary workers, often retained for audit purposes.
  
## Active Directory User Management
The ability to provision and manage user accounts is a core component of Active Directory (AD). In larger organizations, there could be hundreds or thousands of user accounts, including disabled accounts for former employees. In Active Directory, users can have varying levels of rights, ranging from read-only access to Enterprise Admin, which gives complete control over the domain.

### Potential Security Risks
- Users can have misconfigured rights that an attacker could exploit.
- User accounts are a significant attack surface.
- Weak or shared passwords, unauthorized software, and careless admin mistakes can open the door for attacks.

### Policies and Procedures
Organizations need to establish policies to manage user accounts and mitigate risks. Proper management and defense mechanisms should be in place to secure the domain.

## Local Accounts
Local accounts are stored on a particular server or workstation and can only manage access to resources on that host. These accounts are separate from domain accounts and are considered security principals for local machines. Here are some important local accounts on Windows systems:

1. **Administrator**: The first account created on Windows installations, with full control over the system. This account cannot be deleted but can be disabled or renamed.
2. **Guest**: Disabled by default. Intended for temporary access with limited rights. Not recommended for use due to security concerns.
3. **SYSTEM (NT AUTHORITY\SYSTEM)**: A service account that performs internal OS functions. It has full control over the system and is the highest permission level.
4. **Network Service**: A predefined account used for running Windows services. It presents credentials to remote services.
5. **Local Service**: Similar to Network Service but with minimal privileges and presents anonymous credentials.

It's important to understand these local accounts and their roles in Windows systems, as they can be points of entry for attackers.

## Domain Users
Domain users are granted rights from the domain to access resources such as file servers, printers, and other objects based on permissions. They can log in to any machine within the domain, unlike local users who are restricted to a specific host.

### KRBTGT Account
The **KRBTGT** account is a built-in account in Active Directory that provides authentication services for domain resources. This account is a target for attackers as compromising it can allow for privilege escalation and persistence within the domain.

## User Naming Attributes
Security in Active Directory can be improved by understanding user naming attributes that help identify user objects. Important naming attributes include:

- **UserPrincipalName (UPN)**: The primary logon name, often in the form of an email address.
- **ObjectGUID**: A unique identifier for the user that remains constant even if the user is removed.
- **SAMAccountName**: A legacy logon name for earlier Windows versions.
- **ObjectSID**: The user's Security Identifier (SID), used to identify the user and their group memberships.
- **sIDHistory**: Stores previous SIDs if a user object is moved from another domain.

### Example of User Object Attributes
```bash
PS C:\htb Get-ADUser -Identity htb-student
DistinguishedName : CN=htb student,CN=Users,DC=INLANEFREIGHT,DC=LOCAL
Enabled : True
GivenName : htb
Name : htb student
ObjectClass : user
ObjectGUID : aa799587-c641-4c23-a2f7-75850b4dd7e3
SamAccountName : htb-student
SID : S-1-5-21-3842939050-3880317879-2865463114-1111
Surname : student
UserPrincipalName : htb-student@INLANEFREIGHT.LOCAL

```

## Domain-joined vs. Non-Domain-joined Machines

### Domain-joined Machines
A host joined to a domain has easier access to resources and centralized management. It can log in and access resources across any host in the domain. It receives configuration changes and updates via Group Policy.

### Non-domain-joined Machines
Non-domain machines (workgroup computers) do not receive domain policies. They are suitable for small businesses or home use, where each computer is managed independently.

### SYSTEM Level Access
It’s worth noting that SYSTEM accounts (NT AUTHORITY\SYSTEM) on domain-joined machines often have equivalent rights as standard domain users. SYSTEM level access is highly valuable during penetration testing and allows escalating privileges or performing attacks on the domain.

## Conclusion
Understanding user and machine accounts in Active Directory is essential for both administrators and penetration testers. Misconfigurations in user rights and accounts provide valuable attack surfaces, making it important to follow best practices in managing accounts and permissions. Furthermore, understanding the distinctions between local and domain accounts, as well as the implications of SYSTEM-level access, is critical when securing Active Directory environments.