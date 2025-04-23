---
title: SMTP
publishDate: "2025-04-16T13:20:00Z"
updateDate: "2025-04-17T14:32:00Z"
---

# SMTP Overview

## What is SMTP?
- **Simple Mail Transfer Protocol (SMTP)** is a protocol used for sending emails over an IP network.
- It can operate between an email client and an outgoing mail server or between two SMTP servers.
- SMTP is often used in conjunction with IMAP or POP3 protocols for fetching emails.

## How SMTP Works
- SMTP operates as a client-server protocol, where a client sends emails to a server.
- By default, SMTP servers listen for connections on **port 25**. Newer servers may also use **port 587** for authenticated connections.
- The **STARTTLS** command is used to upgrade a plaintext connection to an encrypted one.
- Authentication occurs at the beginning of the connection using a username and password.

## Email Transmission Process
1. **Client (MUA)**: The Mail User Agent sends the email.
2. **Submission Agent (MSA)**: Validates the email before passing it to the Mail Transfer Agent (MTA).
3. **Mail Transfer Agent (MTA)**: Sends and forwards the email to the recipient's server.
4. **Mail Delivery Agent (MDA)**: Delivers the email to the recipient's mailbox.

## Security Considerations
- SMTP transmits data in plaintext, making it vulnerable to interception.
- To enhance security, SMTP can be used with SSL/TLS encryption.
- **Open Relay Attack**: Misconfigured SMTP servers can be exploited to send spam by allowing unauthorized users to relay emails.

## SMTP Commands
- **AUTH PLAIN**: Authenticates the client.
- **HELO/EHLO**: Initiates the session.
- **MAIL FROM**: Specifies the sender's email address.
- **RCPT TO**: Specifies the recipient's email address.
- **DATA**: Begins the email content transmission.
- **RSET**: Aborts the current email transmission.
- **VRFY**: Verifies if a mailbox exists.
- **QUIT**: Ends the session.

## Default Configuration Example
```bash
Pema@htb[/htb]$ cat /etc/postfix/main.cf | grep -v "#" | sed -r "/^\s*$/d"
smtpd_banner = ESMTP Server
myhostname = mail1.inlanefreight.htb
mynetworks = 127.0.0.0/8 10.129.0.0/16