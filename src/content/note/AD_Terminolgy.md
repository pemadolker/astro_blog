---
title: Active Directory Terminology
publishDate: "2025-04-30T13:00:00Z"
updateDate: "2025-04-30T14:32:00Z"
---
# Active Directory Terminology - Notes

## Object
- **Definition:** Any resource in AD (users, computers, printers, etc.).

## Attributes
- **Definition:** Characteristics of objects (e.g., `displayName`, `givenName`).
- **Example:** Computer object has hostname, DNS name.

## Schema
- **Definition:** Blueprint of the AD environment. Defines object types and their attributes.
- **Example:** User objects belong to "user" class.

## Domain
- **Definition:** A logical group of objects (e.g., users, computers).
- **Example:** A domain is like a "city" within a state.

## Forest
- **Definition:** A collection of domains in AD. The topmost container.
- **Example:** A forest can have one or more trees.

## Tree
- **Definition:** A collection of domains in a hierarchy, rooted at a parent domain.
- **Example:** `corp.inlanefreight.local` under `inlanefreight.local`.

## Container
- **Definition:** Objects that contain other objects in the AD hierarchy.
- **Example:** Organizational Units (OUs).

## Leaf
- **Definition:** Objects that don’t contain other objects, found at the end of the hierarchy.
- **Example:** A user object.

## GUID (Global Unique Identifier)
- **Definition:** A unique 128-bit value assigned to every object in AD.
- **Use:** Ensures objects are unique across the environment.

## Security Principals
- **Definition:** Entities that can be authenticated (users, groups, computers).
- **Example:** A user account or group.

## SID (Security Identifier)
- **Definition:** Unique identifier for security principals and groups.
- **Use:** Ensures objects can be uniquely identified.

## Distinguished Name (DN)
- **Definition:** Full path to an object in AD.
- **Example:** `cn=bjones, ou=IT, dc=inlanefreight, dc=local`.

## Relative Distinguished Name (RDN)
- **Definition:** Single component of DN that uniquely identifies an object in the current level.
- **Example:** `bjones`.

## sAMAccountName
- **Definition:** Logon name for a user (up to 20 characters).
- **Example:** `bjones`.

## userPrincipalName
- **Definition:** An alternative user identifier, usually in the format `user@domain`.
- **Example:** `bjones@inlanefreight.local`.

## FSMO Roles (Flexible Single Master Operations)
- **Definition:** Roles to ensure proper management of AD.
  - **Schema Master**
  - **Domain Naming Master**
  - **RID Master**
  - **PDC Emulator**
  - **Infrastructure Master**

## Global Catalog (GC)
- **Definition:** Domain controller storing copies of all objects in the AD forest.
- **Use:** Allows search of objects in any domain in the forest.

## RODC (Read-Only Domain Controller)
- **Definition:** Domain controller with a read-only AD database.
- **Use:** Provides security and redundancy.

## Replication
- **Definition:** The process of synchronizing AD changes across DCs.
- **Use:** Ensures all DCs have the same information.

## SPN (Service Principal Name)
- **Definition:** Uniquely identifies a service instance.
- **Use:** Used in Kerberos authentication.

## GPO (Group Policy Object)
- **Definition:** Collection of policy settings for users and computers.
- **Use:** Defines security settings, software installation, etc.

## ACL (Access Control List)
- **Definition:** List of permissions for accessing an object.
- **Use:** Controls who can access what.

## ACE (Access Control Entry)
- **Definition:** Individual permission entry in an ACL.
- **Use:** Specifies what rights a user or group has.

## DACL (Discretionary ACL)
- **Definition:** Defines who has access to an object.
- **Use:** Grants or denies access to objects.

## SACL (System ACL)
- **Definition:** Defines auditing settings on an object.
- **Use:** Determines what actions will be logged.

## FQDN (Fully Qualified Domain Name)
- **Definition:** Complete domain name for a specific host.
- **Example:** `server.inlanefreight.local`.

## Tombstone
- **Definition:** A deleted object in AD kept temporarily for 60 days.
- **Use:** Prevents stale references from reappearing.

## AD Recycle Bin
- **Definition:** Feature that allows recovery of deleted AD objects.
- **Use:** Simplifies object recovery without restoring backups.
