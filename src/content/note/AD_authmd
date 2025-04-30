---
title: Active Directory  Authentication 
publishDate: "2025-04-29T13:00:00Z"
updateDate: "2025-04-29T14:32:00Z"
---


## Introduction

NTLM (NT LAN Manager) is an authentication protocol used by Microsoft in Active Directory (AD). It provides challenge-response authentication for secure communication over a network. NTLM was used prior to Kerberos in older versions of Windows but is still in use today due to its backward compatibility.

This guide compares the different versions of NTLM (LM, NTLM, NTLMv1, NTLMv2) and provides an overview of how they work, their weaknesses, and how they can be abused by attackers. It will also explore the concept of Domain Cached Credentials (DCC) and how these are used in offline authentication scenarios.

## Hash/Protocol Comparison

| **Hash/Protocol** | **Cryptographic Technique** | **Mutual Authentication** | **Message Type**  | **Trusted Third Party** |
|-------------------|-----------------------------|---------------------------|-------------------|-------------------------|
| **NTLM**          | Symmetric key cryptography  | No                        | Random number     | Domain Controller       |
| **NTLMv1**        | Symmetric key cryptography  | No                        | MD4 hash, random number | Domain Controller       |
| **NTLMv2**        | Symmetric key cryptography  | No                        | MD4 hash, random number | Domain Controller       |
| **Kerberos**      | Symmetric & asymmetric cryptography | Yes                    | Encrypted ticket using DES, MD5 | Domain Controller/Key Distribution Center (KDC) |

## LM (LAN Manager) Hashes

LAN Manager (LM) hashes are the oldest password storage mechanism in Windows OS. They are stored in the SAM database or the NTDS.DIT database in a Domain Controller. LM hashes have significant security weaknesses and have been disabled by default since Windows Vista/Server 2008. Some key details about LM hashes:
- Limited to 14 characters
- Case-insensitive (passwords converted to uppercase before hashing)
- Vulnerable to brute force attacks due to limited keyspace
- Easily cracked using GPU-based tools like Hashcat

**LM Hash Example**:  
`299bd128c1101fd6`

**How LM Hashing Works**:
1. The password is split into two 7-character chunks.
2. Each chunk is hashed with the string "KGS!@#$%" using DES encryption.
3. The resulting two 8-byte ciphertexts are concatenated together to form the LM hash.

## NT Hash (NTLM)

NT LAN Manager (NTLM) uses NT Hashes. These are stored locally in the SAM database or NTDS.DIT file in a Domain Controller. NTLM is used for challenge-response authentication, where the client sends a **NEGOTIATE_MESSAGE** to the server, the server responds with a **CHALLENGE_MESSAGE**, and the client sends the final **AUTHENTICATE_MESSAGE**.

### NT Hashing:
- The NT hash is the MD4 hash of the password in little-endian UTF-16 format.
- NTLM is more secure than LM, supporting the entire Unicode character set.
- NTLM hashes can still be cracked offline, especially for shorter passwords.
- NTLM is vulnerable to **pass-the-hash attacks**, where attackers use the NTLM hash to authenticate as the user without knowing the cleartext password.

**NT Hash Example**:  
`b4b9b02e6f09a9bd760f388b67351e2b`

### Example NTLM Hash Breakdown:
`Rachel:500:aad3c435b514a4eeaad3b935b51304fe:e46b9e548fa0d122de7f59fb6d48eaa2:::`  
- **Rachel**: Username  
- **500**: RID for the administrator account  
- **aad3c435b514a4eeaad3b935b51304fe**: LM Hash (if enabled)  
- **e46b9e548fa0d122de7f59fb6d48eaa2**: NT Hash

## NTLMv1 Authentication (Net-NTLMv1)

NTLMv1 was the first version to use challenge-response authentication, but it is vulnerable to cracking attacks. NTLMv1 uses both the NT and LM hashes.

### NTLMv1 Hash Structure:
- The server sends an 8-byte random challenge (C).
- The client responds using **DES(K1, C) | DES(K2, C) | DES(K3, C)**, where K1, K2, and K3 are based on LM/NT-hashes.
- NTLMv1 hashes are easier to crack using offline dictionary attacks.

### NTLMv1 Hash Example:
`u4-netntlm::kNS:338d08f8e26de93300000000000000000000000000000000:9526fb8c23a90751cdd619b6cea564742e1e4bf33`

## NTLMv2 Authentication (Net-NTLMv2)

NTLMv2 was introduced in Windows NT 4.0 SP4 as a stronger alternative to NTLMv1. It is the default protocol in Windows since Server 2000 and is more resistant to spoofing attacks.

### NTLMv2 Process:
1. The server sends an 8-byte random challenge.
2. The client generates a 16-byte HMAC-MD5 hash of the challenge, user credentials, and domain name.
3. The client sends two responses using the challenge and an additional client-side challenge.

**NTLMv2 Hash Example**:
`admin::N46iSNekpT:08ca45b7d7ea58ee:88dcbe4446168966a153a0064958dac6:5c7830315c7830310000000000000b45c67103`

### NTLMv2 Algorithm:
- **SC**: Server challenge (8 bytes)
- **CC**: Client challenge (8 bytes)
- **v2-Hash**: HMAC-MD5(NT-Hash, username, domain)
- **LMv2/NTv2 Response**: HMAC-MD5 of v2-Hash with the server and client challenge

## Domain Cached Credentials (MSCache2)

MSCache2 is a technique used by Microsoft to handle authentication when a domain-joined host cannot contact a Domain Controller. This method stores the last 10 successful logins locally, with the hashes saved in the registry.

**Key Details**:
- The hashes are stored in `HKEY_LOCAL_MACHINE\SECURITY\Cache`.
- These hashes are more difficult to crack but can still be attacked by an offline brute-force method.
- MSCache2 hashes are typically in the format: `$DCC2$10240#bjones#e4e938d12fe5974dc42a90120bd9c90f`.

## Conclusion

Understanding NTLM authentication and its vulnerabilities is crucial for penetration testers and security professionals. The weaknesses in NTLM (e.g., NTLMv1, LM hashes) can be exploited in attacks such as pass-the-hash and offline cracking. Security measures like using NTLMv2 and disabling LM hashing improve security, but attackers may still find ways to bypass protections.

While NTLM is still in use today, wherever possible, organizations should move towards using Kerberos for authentication due to its stronger security properties and mutual authentication capabilities.

