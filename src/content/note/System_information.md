---
title: System Informtation notes
publishDate: "2025-04-16T11:20:00Z"
updateDate: "2025-04-17T14:32:00Z"
---


## Getting Started with Linux System Info

Before diving deep, remember:
- Use `-h`, `--help`, or `man` to get help for any command.
- Knowing how to get system info is super important—not just for using Linux, but also for finding misconfigurations or security risks.

## Common System Info Commands

| Command    | What it Does |
|------------|---------------|
| `whoami`   | Shows your current username. |
| `id`       | Shows your UID, GID, and group memberships. |
| `hostname` | Prints the name of the machine you're on. |
| `uname`    | Prints OS info (use `-a` for all). |
| `pwd`      | Shows your current working directory. |
| `ifconfig` | Views or sets IP address and config of a network interface. |
| `ip`       | Shows/manages network stuff (routes, devices, etc). |
| `netstat`  | Shows network connections and ports. |
| `ss`       | Similar to netstat but more modern. |
| `ps`       | Shows running processes. |
| `who`      | Shows who’s logged in. |
| `env`      | Displays environment variables. |
| `lsblk`    | Lists block storage devices. |
| `lsusb`    | Lists USB devices. |
| `lsof`     | Shows open files. |
| `lspci`    | Lists PCI devices. |

---

## Logging In via SSH

SSH lets you remotely access other systems through the terminal (no GUI). It's lightweight and fast.

```bash
ssh htb-student@[IP address]
```

## Examples

###  hostname

```bash
hostname
```
> Shows the name of the computer. Ex: `nixfund`

### whoami

```bash
whoami
```
> Shows your current user. Useful to check access level. Ex: `cry0l1t3`

### id

```bash
id
```
> Shows UID, GID, and group membership.
> Helpful in identifying privileges like `sudo`, `adm`, or unusual groups like `hackthebox`.

```bash
uid=1000(cry0l1t3) gid=1000(cry0l1t3) groups=1000(cry0l1t3),1337(hackthebox),4(adm)
```

### uname

```bash
uname -a
```
> Gives full system info: kernel name, version, hostname, hardware type, etc.

```bash
Linux box 4.15.0-99-generic #100-Ubuntu SMP Wed Apr 22 20:32:56 UTC 2020 x86_64
```

#### Just the Kernel Release:

```bash
uname -r
```
> Use this to check for known kernel exploits.

```bash
4.15.0-99-generic
```

---

## Learning & Practice Tips

- Study `man` pages for each command, there’s usually more than you think.
- Use commands in real-time on a target machine to get the hang of it.


---

