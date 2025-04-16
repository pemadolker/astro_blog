---
title: Linux navigation notes
publishDate: "2025-04-16T13:20:00Z"
updateDate: "2025-04-17T14:32:00Z"
---


## 1. Knowing Where You Are
- `pwd` → Prints the current working directory.  
  Example:
  ```bash
  cry0l1t3@htb[~]$ pwd
  /home/cry0l1t3
  ```

## 2. Listing Directory Contents
- `ls` → Lists files and directories in the current path.
- `ls -l` → Lists with details (permissions, owner, size, date).
- `ls -la` → Includes hidden files (those beginning with `.`).
  Example:
  ```bash
  cry0l1t3@htb[~]$ ls -la
  ```

## 3. Reading Output of `ls -l`
| Column         | Description                      |
|----------------|----------------------------------|
| `drwxr-xr-x`   | Type & Permissions               |
| `2`            | Number of hard links             |
| `cry0l1t3`     | Owner                            |
| `htbacademy`   | Group                            |
| `4096`         | Size in bytes (or block size)    |
| `Nov 13 17:37` | Last modified date & time        |
| `Desktop`      | File/Directory name              |

## 4. Hidden Files
- Hidden files begin with a `.` (e.g., `.bashrc`, `.bash_history`)
- Use `ls -la` to see them.

## 5. Listing or Navigating Without Moving
- You can specify a path without changing directories:
  ```bash
  ls -l /var/
  ```

## 6. Moving Between Directories
- `cd /path/to/dir` → Changes to a specified directory.
- `cd -` → Returns to the previous directory.
- `cd ..` → Goes up one directory level (parent).
- `.` → Refers to the current directory.
- `..` → Refers to the parent directory.

## 7. Auto-Completion
- Press `[TAB]` to auto-complete file/directory names.
- Press `[TAB][TAB]` to see all available options.

Example:
```bash
cd /dev/s[TAB][TAB]
```
Might return:
```
shm/ snd/
```

## 8. Cleaning the Terminal
- `clear` → Clears the terminal.
- `[Ctrl] + [L]` → Keyboard shortcut to clear.

Example:
```bash
cd shm && clear
```

## 9. Command History
- Use `↑` and `↓` arrow keys to browse command history.
- `[Ctrl] + [R]` → Reverse search. Start typing to find a past command.
