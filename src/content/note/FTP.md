---
title: Staff – Intelligence Gathering via Social Media
publishDate: "2025-04-16T13:20:00Z"
updateDate: "2025-04-17T14:32:00Z"
---

## What is FTP?
- **File Transfer Protocol (FTP)** is one of the oldest protocols on the Internet.
- Operates at the **application layer** of the TCP/IP protocol stack, similar to HTTP and POP.
- Used for transferring files between a client and a server.

## How FTP Works
- **Control Channel**: Established through TCP port 21 for sending commands and receiving status codes.
- **Data Channel**: Established via TCP port 20 for actual data transmission.
- Supports **active** and **passive** modes:
  - **Active Mode**: Client opens a port and informs the server to connect back.
  - **Passive Mode**: Server provides a port for the client to connect, useful when firewalls block incoming connections.

## FTP Commands and Status Codes
- FTP commands allow users to upload, download, organize directories, and delete files.
- The server responds with status codes indicating success or failure.

## Security Considerations
- FTP is a **clear-text protocol**, making it vulnerable to sniffing.
- **Anonymous FTP** allows users to access files without credentials, but with limited permissions.
- **TFTP (Trivial File Transfer Protocol)** is simpler, uses UDP, and lacks user authentication.

## Default Configuration of vsFTPd
- Commonly used FTP server on Linux.
- Configuration file located at `/etc/vsftpd.conf`.
- Key settings include:
  - `listen=NO`: Run from inetd or as a standalone daemon?
  - `anonymous_enable=NO`: Enable anonymous access?
  - `local_enable=YES`: Allow local users to log in?

## Dangerous Settings
- Allowing anonymous logins can pose security risks.
- Example settings for anonymous access:
  - `anonymous_enable=YES`
  - `anon_upload_enable=YES`
  - `no_anon_password=YES`

## Using FTP
- Connect to an FTP server using a command like:
  ```bash
  ftp <server_ip>



##  Common FTP Commands

- `ls` — List files.
- `get <filename>` — Download a file.
- `put <filename>` — Upload a file.

---

## Downloading Files from FTP

Use `wget` to mirror/download all files from an FTP server:

```bash
wget -m --no-passive ftp://anonymous:anonymous@<server_ip>
```

---

## Scanning FTP with Nmap

Use `nmap` to scan FTP servers and check for vulnerabilities:

```bash
sudo nmap -sV -p21 -sC -A <server_ip>
```

- Scans for open port 21 (FTP)
- Checks for **anonymous login access**
- Retrieves FTP **version** and **server details**

---

##  Conclusion

- FTP is a powerful tool for **file transfer**.
- It comes with **security risks** like unencrypted data and anonymous access.
- Proper configuration and understanding of commands is **essential for safe usage**.