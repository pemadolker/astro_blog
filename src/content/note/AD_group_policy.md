---
title: Examing Group policy
publishDate: "2025-04-29T13:00:00Z"
updateDate: "2025-04-29T14:32:00Z"
---


## What is Group Policy?

- Group Policy is a feature in Windows that helps administrators manage user and computer settings.
- It applies settings across individual machines or in a domain using **Active Directory (AD)**.
- Every Windows system has a **Local Group Policy Editor**, but this guide focuses on **domain-level Group Policy**.

## Why is Group Policy Important?

- It controls OS behavior, user experience, and application settings.
- It is crucial for managing **security policies** in a Windows domain.
- Helps implement **defense-in-depth** strategy.
- Can be abused by attackers if misconfigured.

---

## What is a GPO (Group Policy Object)?

- A **GPO** is a virtual collection of settings.
- It can apply to:
  - Users
  - Computers
  - Groups
- A GPO has a **unique name** and **GUID**.
- Can be linked to:
  - Sites
  - Domains
  - Organizational Units (OUs)

## Examples of What GPOs Can Do

- Set **password policies** (e.g. complexity, length)
- Disable USB ports
- Enforce **screensaver with password**
- Restrict access to apps like `cmd.exe` or PowerShell
- Enforce **audit and logging**
- Deploy software across domain
- Prevent installing unapproved software
- Set **login banners**
- Disable **LM hash** usage
- Run scripts during:
  - Startup/Shutdown
  - Logon/Logoff

### Default Password Policy (Windows Server 2008)

- Minimum 7 characters
- Must include 3 out of 4:
  - Uppercase letters
  - Lowercase letters
  - Numbers
  - Special characters

---

## GPO Application Order (Precedence)

| Level                 | Description                                                                 |
|----------------------|-----------------------------------------------------------------------------|
| **Local GPO**        | Set on local machine. Overwritten by domain policies.                       |
| **Site Policy**      | Applies to specific geographical/enterprise sites.                          |
| **Domain Policy**    | Applies to the entire domain. E.g., default password settings.              |
| **OU Policy**        | Applies to users/computers in specific OUs.                                 |
| **Nested OU Policy** | Specific to objects in nested OUs.                                          |

- **Settings closest to the object (e.g., OU)** have the **highest priority**.
- **Computer settings** take priority over **user settings** if both exist for the same config.

---

## Managing Group Policy

- Use **Group Policy Management Console (GPMC)**.
- Use **PowerShell GroupPolicy module** for command-line control.
- Two default GPOs:
  - **Default Domain Policy**: Applies to all users and computers.
  - **Default Domain Controllers Policy**: Applies to all domain controllers.

---

## Link Order of GPOs

- When multiple GPOs are linked to an OU:
  - **Link Order 1** is processed **last** = **highest precedence**.
- Example:
  - GPO 1 (Link Order 1) overrides GPO 2 (Link Order 2).

## Enforced GPO

- Setting **"Enforced"** ensures lower-level OUs **cannot override** it.
- Formerly known as **"No Override"**.
- Even if a lower-level GPO has different settings, **Enforced GPO wins**.

## Block Inheritance

- Prevents higher-level GPOs from applying to an OU.
- If both **Enforced** and **Block Inheritance** are set:
  - **Enforced** wins.

---

## GPO Refresh Frequency

- By default:
  - Clients refresh GPO every **90 minutes ±30 minutes**.
  - Domain controllers refresh every **5 minutes**.
- Use command:  
  ```bash
  gpupdate /force
  ```
  to manually update policies.
- You can change refresh interval via:
  `Computer Configuration > Policies > Administrative Templates > System > Group Policy`.

Setting refresh intervals too often can cause **network congestion**.

---

## Security Risks with GPOs

- Attackers can abuse GPOs to:
  - Add themselves to admin groups
  - Run malicious scripts
  - Set scheduled tasks
  - Spread malware domain-wide
- Attackers may gain:
  - **Lateral movement**
  - **Persistence**
  - **Privilege escalation**
- Proper configuration and **access control** is essential.

---

## Summary

- Group Policy is **essential** for Windows domain management.
- It’s **powerful** but can be dangerous if not secured.
- Understand **how GPOs work** and their **order of precedence** to protect your domain.
- Always audit who has permission to modify GPOs and monitor GPO changes regularly.