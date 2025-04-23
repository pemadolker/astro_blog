---
title: Network File System
publishDate: "2025-04-16T13:20:00Z"
updateDate: "2025-04-17T14:32:00Z"
---
## Introduction
NFS is a protocol developed by Sun Microsystems in 1984 that allows a user on a client computer to access files over a network in the same way they access local storage.

---

## How NFS Works
- NFS operates on a client-server model.
- Server exports directories to clients.
- Clients mount the exported directory and access files transparently.

---

## Key Features
- **Transparency**: Users interact with remote files as if they are local.
- **Centralized Management**: Files can be stored in one place and shared.
- **Security**: Controlled via export options and tools like firewalls and Kerberos.

---

## Configuration

### Server Side
1. Install NFS utilities:
   ```bash
   sudo apt install nfs-kernel-server
   ```

2. Create a directory to share:
   ```bash
   sudo mkdir -p /srv/nfs/general
   ```

3. Add to exports:
   ```bash
   sudo nano /etc/exports
   /srv/nfs/general 192.168.1.0/24(rw,sync,no_subtree_check)
   ```

4. Restart the service:
   ```bash
   sudo systemctl restart nfs-kernel-server
   ```

---

### Client Side
1. Install NFS client:
   ```bash
   sudo apt install nfs-common
   ```

2. Create mount point:
   ```bash
   sudo mkdir -p /mnt/nfs/general
   ```

3. Mount the NFS share:
   ```bash
   sudo mount 192.168.1.100:/srv/nfs/general /mnt/nfs/general
   ```

---

## Permanent Mounting (Client Side)
- Edit `/etc/fstab`:
  ```bash
  192.168.1.100:/srv/nfs/general /mnt/nfs/general nfs defaults 0 0
  ```

---

## Security Considerations
- Use `/etc/exports` options carefully: `no_root_squash`, `read-only`, etc.
- Secure with firewalls.
- Use `rpcbind` security or Kerberos for enterprise.

---

## Common Commands
- Show mounted NFS shares:
  ```bash
  showmount -e 192.168.1.100
  ```
- Unmount a share:
  ```bash
  sudo umount /mnt/nfs/general
  ```

---

## Troubleshooting
- Check firewall and NFS status.
- Use `dmesg`, `journalctl`, or `systemctl status` for logs.
- Permissions and ownership should match between server and client.

---

## Conclusion
NFS is a reliable and efficient way to share files across Unix/Linux systems, ideal for internal networks where centralized file storage is necessary.