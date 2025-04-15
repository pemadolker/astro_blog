---
title: Linux_Structure notes
publishDate: "2025-04-16T12:00:00Z"
updateDate: "2025-04-17T14:32:00Z"
---


# Linux Structure 

Linux is an operating system just like Windows or macOS, and it’s used on PCs, servers, and even phones. It's super important in cybersecurity because it's open-source, secure, and flexible.

## History of Linux

- It all started with Unix in 1970 by Ken Thompson and Dennis Ritchie.
- BSD came in 1977 but had legal issues because it used Unix code from AT&T.
- Richard Stallman started the GNU project in 1983 and created the GPL (General Public License).
- In 1991, Linus Torvalds (a student from Finland) made the Linux kernel.
- Now, Linux has grown massively with over 600 versions (called distros). Some popular ones: Ubuntu, Debian, Fedora, RedHat, etc.

Linux is popular because it's free, secure, and very stable. Android is actually built on the Linux kernel, so Linux is used more than any other OS!

## Linux Philosophy

Linux follows a simple and smart way of doing things:

- **Everything is a file** – Even settings are saved as text files.
- **Small tools for small jobs** – Each tool does one thing and does it well.
- **Chain tools together** – You can combine tools to do big tasks.
- **No forced UIs** – It focuses more on terminal/shell usage.
- **Text-based config files** – Like `/etc/passwd` which stores user info.

## Components of Linux

| Component      | Description |
|----------------|-------------|
| **Bootloader** | Starts the OS (e.g. GRUB bootloader). |
| **Kernel** | The brain – manages hardware and system resources. |
| **Daemons** | Background services (e.g. printing, time). |
| **Shell** | The terminal – interface between you and the system. |
| **Graphics Server** | Allows GUIs to run (X or X-server). |
| **Window Manager** | The actual graphical UI like GNOME, KDE, etc. |
| **Utilities** | Tools and apps that do various tasks. |

## Linux Architecture (How it’s built)

- **Hardware** – Your computer stuff like RAM, CPU, disk.
- **Kernel** – Talks to hardware and handles resources.
- **Shell** – Terminal that you use to send commands.
- **System Utilities** – All the extra tools and programs.

##  Linux File System (Directory Structure)

Linux uses a tree-like structure for files and folders. Here's a simple breakdown:

| Path | What’s Inside |
|------|---------------|
| `/` | The root of everything. |
| `/bin` | Basic commands like `ls`, `cp`, `mv`. |
| `/boot` | Files needed to start the system. |
| `/dev` | Access to hardware devices. |
| `/etc` | System config files. |
| `/home` | Personal folders for users. |
| `/lib` | Libraries needed for booting. |
| `/media` | Where USBs and CDs show up. |
| `/mnt` | Temporary mount point. |
| `/opt` | Extra/optional software. |
| `/root` | Home folder for root user. |
| `/sbin` | System admin tools. |
| `/tmp` | Temporary files (auto deleted). |
| `/usr` | Programs, docs, libraries. |
| `/var` | Logs, mail, dynamic data. |

---
