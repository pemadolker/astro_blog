---
title: Domain Information
publishDate: "2025-04-23T13:00:00Z"
updateDate: "2025-04-23T14:32:00Z"
---


Domain info is one important part in pentest. It’s not only about subdomains but full Internet presence of the company. So we collect info and try to understand how company works and what techs or structures are used to provide service successfully. This type of info we collect passively, meaning we don't do direct scan. We stay hidden and look like customers or visitors, so we don't expose ourself.

The OSINT part here is only small part of how deep OSINT can go. More methods are in module `OSINT: Corporate Recon`. But here we use third-party services to understand company better. First thing we do is look properly at the main website of company. We read all the texts and think what techs or structure needed to provide those services. For example, IT companies may offer app dev, IoT, hosting, data science, and cyber security services.

If we see services we don’t know, we should study it. It helps us know how company is structured. This part is like mix of first and second principle of enumeration. We look at what we see and also what we don't see. We see the services, but not how they work. But services depend on tech things that make it work. So we think like a developer and understand it from their view. That view gives many tech insight.

## Online Presence

When we know little bit about company and services, we can get first idea of their Internet presence. Let’s say a mid-size company ask us to pentest all infra from black-box view. We only get target scope, we need to find rest of info.

First thing we check is SSL certificate of main website. Many time, cert has more than one domain, and those are probably still active.

### Certificate Transparency Logs

To find more subdomains, we use `crt.sh`. It show logs of certs from Certificate Authority. This process is called Certificate Transparency (RFC 6962). It helps detect fake or bad certs. SSL cert providers like Let’s Encrypt share to `crt.sh` and database update.


## Find Company-Hosted Servers

We want to find hosts that are hosted by the company, not third party. Because we cannot test third party hosts.



## Use Shodan

After we get IPs, we use Shodan to get more info. Shodan is search engine for Internet-connected devices. It checks open ports and gives info like city, country, org, open ports and what is running.


## DNS Records

To find more possible hosts, we check DNS records also.

---
