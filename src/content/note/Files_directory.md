---
title: Files and Directory notes
publishDate: "2025-04-16T13:00:00Z"
updateDate: "2025-04-17T14:32:00Z"
---


## Introduction
In Linux, we interact with files mainly through the terminal instead of a graphical interface like in Windows. The terminal offers speed, flexibility, and efficiency. You can view, create, edit, move, or delete files quickly—sometimes without even using editors like `vim` or `nano`. You can also automate tasks using regex and command chaining.

Let’s now explore the basic commands to manage files and directories in Linux.

---

## Create Files and Directories

### Create a File
Use the `touch` command to create an empty file:
```bash
user@linux$ touch info.txt
```

### Create a Directory
Use the `mkdir` command to create a new folder:
```bash
user@linux$ mkdir SWS_notes
```

### Create Nested Directories
Use `-p` with `mkdir` to create multiple levels at once:
```bash
user@linux$ mkdir -p SWS_Notes/local/user/documents
```

### View Directory Tree
Use the `tree` command to view the folder structure:
```bash
user@linux$ tree .
```
Example output:
```
.
├── info.txt
└── Storage
    └── local
        └── user
            └── documents

4 directories, 1 file
```

---

## Create Files Inside a Directory
Use `touch` with the path:
```bash
user@linux$ touch ./SWS_Notes/local/user/userinfo.txt
```

Updated tree:
```
.
├── info.txt
└── Storage
    └── local
        └── user
            ├── documents
            └── userinfo.txt

4 directories, 2 files
```

---

## Move & Rename Files

### Rename a File
Use `mv` with the new name:
```bash
user@linux$ mv info.txt information.txt
```

### Move Files to a Directory
```bash
user@linux$ touch readme.txt
user@linux$ mv information.txt readme.txt Storage/
```

Updated tree:
```
.
└── Storage
    ├── information.txt
    ├── local
    │   └── user
    │       ├── documents
    │       └── userinfo.txt
    └── readme.txt

4 directories, 3 files
```

---

## Copy Files

### Copy a File to Another Folder
```bash
user@linux$ cp SSWS_Notes/readme.txt Storage/local/
```

Check the structure:
```bash
user@linux$ tree .
```

Updated output:
```
.
└── Storage
    ├── information.txt
    ├── local
    │   ├── readme.txt
    │   └── user
    │       ├── documents
    │       └── userinfo.txt
    └── readme.txt

4 directories, 4 files
```

---

## Other Useful Tips

- You can use **redirection** (`>`, `>>`, `<`) to write or read from files directly.
- Tools like `vim` and `nano` help in editing files interactively.
- Commands can be combined to perform powerful file operations efficiently.

---

## Optional Exercise
Use online resources to learn how to delete files and directories. Try researching commands like:

- `rm` → delete files
- `rm -r` → delete directories and their contents

> Searching online is not cheating—it's how real-world professionals learn. Try different keywords like:  
> `"how to delete files in linux terminal"` or `"remove folder in Linux using command line"`

---