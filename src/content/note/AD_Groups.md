---
title: Active Directory  Groups
publishDate: "2025-04-29T13:00:00Z"
updateDate: "2025-04-29T14:32:00Z"
---

# Active Directory Groups

After users, **groups** are another significant object in Active Directory. They help organize similar users together and allow mass assignment of rights and access.

Groups are a key target for attackers and penetration testers. The rights they confer might not be readily apparent but may grant **excessive or unintended privileges** if not properly configured.

There are **many built-in groups** in AD, and organizations typically create custom groups to manage access. Over time, the number of groups can become large and hard to manage, potentially leading to **unintended access**.

> Periodic auditing is essential:  
> - What groups exist?  
> - What privileges do they grant?  
> - Are there unnecessary memberships?

---

## Groups vs Organizational Units (OUs)

| **Groups** | **OUs (Organizational Units)** |
|------------|-------------------------------|
| Used to assign permissions to access resources. | Used to group users, groups, and computers. |
| Help manage access. | Help ease administration and apply Group Policy settings. |
| Cannot delegate admin tasks directly. | Can delegate tasks like password resets. |

---

## Types of Groups

Groups make it easy to manage permissions for **multiple users, computers, and contacts**.

### Example Scenario:
An admin needs to assign access to a new shared drive for 50 users. Instead of assigning permissions individually, a **group** is created and granted access. Users added to this group inherit those permissions automatically.

> Modifying/removing access is as simple as removing users from the group.

---

## Group Type and Scope

Every AD group has two key characteristics:

- **Type**: Defines the **purpose** of the group.
- **Scope**: Defines **where** and **how** the group can be used.

### Group Types

| **Type**       | **Purpose** |
|----------------|-------------|
| **Security**   | Assign rights and permissions to users. |
| **Distribution** | Used for email distribution (e.g., mailing lists). Cannot be used for resource permissions. |

---

## Group Scopes

There are **three scopes** for AD groups:

### 1. Domain Local Group

- Used **only within** the domain where it was created.
- Can contain users **from other domains**.
- Can be nested in **other local groups**, but **not in global groups**.

### 2. Global Group

- Can be used to access **resources in other domains**.
- Can contain only **users from its own domain**.
- Can be added to **global or domain local groups**.

### 3. Universal Group

- Used across **multiple domains**.
- Stored in the **Global Catalog (GC)**.
- Can contain **users from any domain**.
- **Triggers forest-wide replication** when modified.

> Best practice:  
> Use **global groups inside universal groups** to reduce replication.

---

## Group Scope Examples (via PowerShell)

```powershell
PS C:\htb> Get-ADGroup -Filter * | select samaccountname, groupscope
```

| samAccountName                     | groupScope     |
|-----------------------------------|----------------|
| Administrators                    | DomainLocal    |
| Users                             | DomainLocal    |
| Guests                            | DomainLocal    |
| Domain Computers                  | Global         |
| Domain Admins                     | Global         |
| Schema Admins                     | Universal      |
| Enterprise Admins                 | Universal      |
| Remote Desktop Users              | DomainLocal    |
| Domain Controllers                | Global         |
| Domain Users                      | Global         |
| Print Operators                   | DomainLocal    |
| ...                               | ...            |

---

## Changing Group Scopes

| **From**         | **To**          | **Condition** |
|------------------|------------------|----------------|
| Global → Universal | Only if not part of another Global group. |
| Domain Local → Universal | Only if it doesn't contain other Domain Local groups. |
| Universal → Domain Local | No restriction. |
| Universal → Global | Only if it doesn’t contain other Universal groups. |

---

## Built-in vs Custom Groups

- **Built-in groups**:  
  - Created when a domain is initialized.
  - Often have **Domain Local** scope.
  - Used for **administrative functions**.
  - Cannot have nested groups.

- **Custom groups**:  
  - Created by organizations to manage their own needs.
  - Can be **Security** or **Distribution** groups.

> ⚠️ Microsoft Exchange and other services can automatically create **privileged groups** — be cautious!

---

## Nested Group Membership

Nested groups allow one group to be a **member of another**. This can result in:

- **Inherited privileges** from parent groups.
- **Unintended privilege escalation** that is hard to track.

### Example:

User `DCorner` is in `Help Desk`, and `Help Desk` is in `Helpdesk Level 1`.  
Even if DCorner is not a direct member of `Helpdesk Level 1`, they inherit its permissions.

> **Tool Tip:**  
> Use **BloodHound** to visualize nested group memberships and discover privilege paths.

---

## Important Group Attributes

| **Attribute** | **Description** |
|---------------|------------------|
| `cn`          | Common name of the group in AD DS. |
| `member`      | Lists all users, groups, and contacts in the group. |
| `groupType`   | Integer representing group type and scope. |
| `memberOf`    | Shows parent groups (for nested memberships). |
| `objectSid`   | Unique security identifier for the group. |

---

## Summary

- Groups simplify permission management.
- Understand **types** (Security vs Distribution) and **scopes** (Domain Local, Global, Universal).
- Be cautious with **nested group memberships**.
- Periodically **audit groups** to prevent privilege sprawl.
- Tools like **BloodHound** can help identify hidden privilege relationships.