---
title: Domian Name system
publishDate: "2025-04-16T13:20:00Z"
updateDate: "2025-04-17T14:32:00Z"
---

## What is DNS?
- **Domain Name System (DNS)** is a crucial part of the Internet that translates domain names (e.g., academy.hackthebox.com) into IP addresses.
- It operates without a central database, distributing information across thousands of name servers globally.

## Types of DNS Servers
1. **DNS Root Server**: 
   - Responsible for top-level domains (TLDs).
   - Acts as a central interface linking domain names and IP addresses.
   - There are 13 root servers worldwide.

2. **Authoritative Name Server**: 
   - Holds authority for a specific zone and provides binding answers to queries within its area.

3. **Non-authoritative Name Server**: 
   - Collects information from other DNS zones but does not hold authority over them.

4. **Caching DNS Server**: 
   - Caches information from other name servers for a specified duration to speed up future queries.

5. **Forwarding Server**: 
   - Forwards DNS queries to another DNS server.

6. **Resolver**: 
   - Performs name resolution locally on a computer or router.

## DNS Security
- DNS is primarily unencrypted, making it vulnerable to eavesdropping.
- Solutions for DNS encryption include:
  - **DNS over TLS (DoT)**
  - **DNS over HTTPS (DoH)**
  - **DNSCrypt**

## DNS Records
Different DNS records serve various functions:
- **A**: Returns an IPv4 address.
- **AAAA**: Returns an IPv6 address.
- **MX**: Specifies mail servers for the domain.
- **NS**: Lists the domain's name servers.
- **TXT**: Contains various information, such as SPF and DMARC records.
- **CNAME**: Serves as an alias for another domain name.
- **PTR**: Converts IP addresses into domain names (reverse lookup).
- **SOA**: Provides information about the DNS zone and administrative contact.

## DNS Configuration
- DNS servers typically use three types of configuration files:
  1. Local DNS configuration files
  2. Zone files
  3. Reverse name resolution files

### Example of Local DNS Configuration
```bash
root@bind9:~# cat /etc/bind/named.conf.local
zone "domain.com" {
    type master;
    file "/etc/bind/db.domain.com";
    allow-update { key rndc-key; };
};

## Dangerous Settings
Certain DNS configurations can lead to vulnerabilities:

- **allow-query**: Defines which hosts can send requests.
- **allow-recursion**: Defines which hosts can make recursive requests.
- **allow-transfer**: Defines which hosts can receive zone transfers.

## Footprinting the DNS Service
DNS servers can be queried for various information, including other name servers using NS records.


## Zone Transfer
Zone transfers (AXFR) allow the transfer of zone data to another server, typically over TCP port 53.



## Brute Forcing Subdomains
Subdomain brute forcing can be performed using lists of potential hostnames.

## Conclusion
- Understanding DNS and its configurations is essential for network management and security.
- Tools like `dig` and `dnsenum` can be used for querying and enumerating DNS records.
- Proper configuration and security measures are crucial to prevent vulnerabilities in DNS services.