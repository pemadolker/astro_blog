---
title: Active Directory Rights and Privilege
publishDate: "2025-04-29T13:00:00Z"
updateDate: "2025-04-29T14:32:00Z"
---


## Overview
Rights and privileges in Active Directory (AD) are foundational for managing security and access. Mismanagement can lead to serious vulnerabilities.

- **Rights**: Permissions to access objects like files.
- **Privileges**: Allow execution of actions like running programs, resetting passwords, etc.

## Built-in AD Groups

| Group Name | Description |
|------------|-------------|
| **Account Operators** | Can create/modify most accounts. Cannot manage administrative users. |
| **Administrators** | Full domain access. |
| **Backup Operators** | Can backup/restore files, log onto/shut down DCs. Potential for shadow copy extraction. |
| **DnsAdmins** | DNS management access. |
| **Domain Admins** | Full domain control. Members are local admins on all machines. |
| **Domain Computers** | All domain-joined computers (except DCs). |
| **Domain Controllers** | All DCs in the domain. |
| **Domain Guests** | Guest accounts. |
| **Domain Users** | All user accounts. |
| **Enterprise Admins** | Forest-wide configuration rights. |
| **Event Log Readers** | Read event logs. Created on DC promotion. |
| **Group Policy Creator Owners** | Create/edit/delete GPOs. |
| **Hyper-V Administrators** | Full Hyper-V access. Considered DA if managing virtual DCs. |
| **IIS_IUSRS** | Used by IIS 7.0+. |
| **Pre–Windows 2000 Compatible Access** | Legacy group. Risky due to excessive read access. |
| **Print Operators** | Manage DC printers. Can escalate privileges. |
| **Protected Users** | Additional protections against credential theft. |
| **Read-only Domain Controllers** | All RODCs. |
| **Remote Desktop Users** | RDP access. |
| **Remote Management Users** | WinRM remote access. |
| **Schema Admins** | Can modify AD schema. Root domain only. |
| **Server Operators** | Modify services, access shares on DCs. No default members. |

## Group Membership Examples

### Server Operators Group

```powershell
Get-ADGroup -Identity "Server Operators" -Properties *
```

- Default: No members
- GroupScope: DomainLocal

### Domain Admins Group

```powershell
Get-ADGroup -Identity "Domain Admins" -Properties *
```

- Scope: Global
- Multiple members (admin/service accounts)

## User Rights Assignment (URA)

Some rights can lead to privilege escalation if misconfigured. Examples:

| Privilege | Description |
|----------|-------------|
| **SeRemoteInteractiveLogonRight** | RDP login right. |
| **SeBackupPrivilege** | Backup system files (can extract credentials). |
| **SeDebugPrivilege** | Debug processes (e.g., read LSASS memory with Mimikatz). |
| **SeImpersonatePrivilege** | Impersonate SYSTEM. Tools: JuicyPotato, RogueWinRM, etc. |
| **SeLoadDriverPrivilege** | Load/unload drivers. |
| **SeTakeOwnershipPrivilege** | Take ownership of objects (files/shares). |

## Viewing User Privileges

### Standard User

```powershell
whoami /priv
```

Example output:

```text
SeChangeNotifyPrivilege Enabled
SeIncreaseWorkingSetPrivilege Disabled
```

### Domain Admin (Non-Elevated)

```powershell
whoami /priv
```

Limited rights shown due to UAC.

### Domain Admin (Elevated)

```powershell
whoami /priv
```

Shows full list:

```text
SeIncreaseQuotaPrivilege
SeMachineAccountPrivilege
SeSecurityPrivilege
SeTakeOwnershipPrivilege
...
```

## Important Notes

- Use Group Policy to manage rights carefully.
- Abuse tools: SharpGPOAbuse, Mimikatz, JuicyPotato, PrintSpoofer, etc.
- Be cautious with built-in group membership.
- Least privilege principle is critical.