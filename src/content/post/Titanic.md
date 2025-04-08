---
title: "Titanic"
description: "HTB room Assignment1 "
publishDate: "2025-04-8"
tags: [ "HTB rooms"]
---
# Titanic

The goal was to identify open ports, discover running services, enumerate web directories, and eventually attempt exploitation based on the findings on target - titanic seasonal machine .

1. Initial host discovery and port scanning 

Started by running nmap scan with the -Pn flag. Usually, nmao first pings the target  before scanning, but some machines block ICMP requests, making them seem offline. 

Using -Pn forces nmap to treat the host as online and proceed with scanning. This was important to determine whether the machine was accessible and had any open ports.



The initial scan confirmed that the machine was up and running. 

1. Targeted Service Enumeration

After confirming  that the machine was online, I needed to determine the services running on specific ports. Instead of scanning all  ports, I focused on **ports 1048, 1248, and 2048**, which were filtered based on initial observations.

All targeted ports were closed, which mean no services were running on these ports. Then shifted my focus to web services.

1. Web Server Enumeration

Since many CTF machines have web services running, I decided to scan the web server using Nikto, a well-known tool for detecting vulnerabilities and misconfigurations in web applications.

Nikto is  useful for detecting common issues, so I ran it early in my process to gather insights before moving to more targeted web fuzzing.



1. Service and Script Scan

To gain a deeper scan of the services running soI performed a **service and script scan** using Nmap with the -sC flag. This flag runs default scripts that provide additional information, such as SSL certificate details and potential vulnerabilities.



1. Bruteforcing Web Directory

 Since the target had an active web service, I suspected there might be hidden directories or files that could provide access to sensitive information.

To discover these, I used ffuf  (Fuzz Faster U Fool) that is a powerful web fuzzing tool that helps brute-force common directory names.

Brute-forcing directories is a common technique for discovering hidden resources so I used the common wordlist from dirb, which contains frequently used directory names, to maximize my chances of finding valid paths like admin panel, login page, or exposed sensitive file.



1. Hostname Resolution for Subdomains

I edited my /etc/hosts file and added:

`10.10.11.55 titanic.htb  gitea.titanic.htb`


When dealing with custom domains, web applications usually seem to have virtual hosts or subdomains that require manual mapping.. By adding these entries to my /etc/hosts file, I ensured that I could easily access these domains .
I also added gitea.titanic.htb, as Gitea is siad to be a lightweight Git hosting service, and if running, it would expose repositories, credentials, or configuration files.

7. Exploiting Directory Traversal

 I attempted path traversal, which is a common vulnerability in web applications and  exploiting it can provide access to sensitive information that could be used to escalate privileges or gain further access to the system. 

I bypassed normal path sanitization mechanisms and aimed to traverse up directories and retrieve sensitive system files, like /etc/passwd, which is supposed to lists all system users.



Conclusion 

The penetration testing process on the Titanic machine involved starting with  reconnaissance using nmap and narrowing down to target.  These findings provide a solid foundation for further exploitation