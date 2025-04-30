---
title: Active Directory Objects
publishDate: "2025-04-29T20:00:00Z"
updateDate: "2025-04-29T20:32:00Z"
---



## Security in Active Directory (AD)

Active Directory is a centralized directory service used for authentication and access management. While it’s designed for **availability**, its default settings may sacrifice **confidentiality** and **integrity**, making **security hardening essential**.

---

## CIA Triad in Active Directory

- **Confidentiality**: Only authorized users access sensitive information.
- **Integrity**: Ensure data is accurate and unaltered.
- **Availability**: Services remain accessible to legitimate users.

> ⚠️ AD emphasizes availability, so extra steps are needed to enforce confidentiality and integrity.

---

## General Hardening Measures

### 1. Microsoft LAPS (Local Administrator Password Solution)

- **Purpose**: Randomizes and secures local admin passwords on domain-joined machines.
- **Benefits**:
  - Prevents lateral movement.
  - Ensures unique, rotated passwords.
- **Implementation**:
  - Deploy via Group Policy.
  - Store passwords in AD attributes securely.

---

### 2. Audit Policy Settings (Logging & Monitoring)

- **Goal**: Detect and respond to unauthorized activities.
- **Key Audit Categories**:
  - Account logon events
  - Object access
  - Directory service access
  - Policy/privilege changes
- **Tools**:
  - Use **Advanced Audit Policy Configuration**.
  - Integrate with **SIEM tools** for real-time monitoring.

---

### 3. Group Policy Security Settings

- **Account Policies**:
  - Enforce password complexity, history, lockout.
  - Configure Kerberos lifetimes.
- **Local Policies**:
  - Define user rights, audit settings, security options.
- **Software/Application Control**:
  - Restrict unauthorized software (via **SRP**/**AppLocker**).
  - Limit PowerShell/CMD access for standard users.

---

### 4. Advanced Audit Policy Configuration

- **Purpose**: Fine-grained event tracking.
- **Categories**:
  - Logon/logoff
  - Object access
  - Privilege use
- **Usefulness**:
  - Supports forensic investigations.
  - Enables detailed user and system activity tracking.

---

### 5. Update Management (WSUS / SCCM)

- **WSUS**: Patch Microsoft products centrally.
- **SCCM**: Comprehensive patch, OS, and app deployment.
- **Benefits**:
  - Ensure compliance.
  - Approve/decline updates with reporting.

---

### 6. Group Managed Service Accounts (gMSA)

- **Function**: Auto-manage passwords for service accounts.
- **Benefits**:
  - No manual password handling.
  - Reduces password-related outages.

---

### 7. Security Groups

- **Types**:
  - **Security Groups** – Assign resource permissions.
  - **Distribution Groups** – Email lists.
- **Best Practice**:
  - Use **AGDLP model**:
    - Accounts → Global Groups → Domain Local Groups → Permissions
  - Regularly audit memberships.

---

### 8. Account Separation

- **Practice**: Use different accounts for admin and daily tasks.
  - Example: `jdoe` vs `jdoe_admin`
- **Benefit**: Reduces exposure of admin credentials.

---

### 9. Password Complexity, Passphrases & MFA

- **Recommendations**:
  - Enforce ≥12-character passwords.
  - Use passphrases for strength and memorability.
  - Require MFA for admin and remote access.
- **Tools**:
  - Password filters to block weak/common passwords.

---

### 10. Limit Domain Admin Usage

- **Rules**:
  - Use only on Domain Controllers.
  - Never for day-to-day or on workstations.
- **Why**:
  - Avoid credential theft (e.g., via **Mimikatz**).

---

### 11. Remove Stale Users and Objects

- **Practice**:
  - Regularly identify & disable inactive accounts.
  - Audit accounts with long inactivity.
- **Tools**:
  - Use **PowerShell** or **3rd-party tools**.

---

### 12. Audit Permissions & Access

- **Goal**: Ensure **least privilege principle**.
- **Actions**:
  - Audit **ACLs**, group memberships.
  - Minimize privileged groups (e.g., **Domain Admins**).

---

### 13. Logging & Centralized Audit Policies

- **Importance**: Monitor suspicious behavior.
- **Practices**:
  - Centralize logs using **SIEM**.
  - Set alerts for anomalies (e.g., brute-force login attempts).

---

### 14. Restricted Groups

- **Use**: Enforce group membership via **Group Policy**.
- **Example**: Ensure only allowed users are in **Administrators**, **RDP Users**.

---

### 15. Limit Server Roles on Domain Controllers

- **Recommendation**: Don’t install unnecessary roles (e.g., **IIS**) on DCs.
- **Benefit**: Minimizes attack surface.

---

### 16. Restrict Local Admin & RDP Rights

- **Approach**:
  - Only essential users get local admin rights.
  - Limit Remote Desktop Protocol (RDP) access.
- **Implementation**:
  - Manage via Group Policy.
  - Monitor RDP and configure firewall access.

---

##  Additional Best Practices

### Secure Admin Hosts

- Use isolated, hardened workstations for admin tasks.
- Avoid using them for regular tasks.

---

### Security Assessments

- Periodically review AD permissions and configs.
- Use **Microsoft Security Compliance Toolkit**.

---

### Incident Response

- Create & maintain a plan tailored for AD.
- Test backups and recovery procedures regularly.
