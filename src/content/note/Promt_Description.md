---
title: Prompt description notes
publishDate: "2025-04-16T13:00:00Z"
updateDate: "2025-04-17T14:32:00Z"
---


## What is the Bash Prompt?

The bash prompt is the line you see in your terminal when it's ready for a command. It usually shows:

- **Your username** (who you are)
- **Hostname** (name of your computer)
- **Current working directory**

It looks something like this:
```
<username>@<hostname><current working directory>$
```

The **`$`** means you're a regular user. If you're the **root user**, it changes to **`#`**.

Examples:
- Regular user: `user@machine[~]$`
- Root user: `root@htb[/htb]#`

> Note: The tilde `~` means you're in your **home directory**.

---

## Why Does the Prompt Sometimes Look Different?

Sometimes, when you get a shell on a target system (e.g., during a pentest), the prompt might just show:
```
$
```
or
```
#
```
This happens because the **PS1** variable isn't set properly.

---

##  What is PS1?

**PS1** is a variable in Linux that controls how your prompt looks. You can customize it to show things like:

- Your username
- Hostname
- Folder you're in
- Date and time
- IP address
- Status of last command
- And even colors!

You do this by editing the `.bashrc` file in your home directory.

---

## Special Characters for Custom Prompts

Here are some useful codes you can use in PS1:

| Code         | What it shows                   |
|--------------|----------------------------------|
| `\u`         | Current username                 |
| `\h`         | Hostname                         |
| `\w`         | Full path of current directory   |
| `\d`         | Date (e.g., Mon Feb 6)           |
| `\D{{%Y-%m-%d}}` | Date in YYYY-MM-DD format     |
| `\H`         | Full hostname                    |
| `\j`         | Number of background jobs        |
| `\n`         | Newline                          |
| `\r`         | Carriage return                  |
| `\s`         | Shell name                       |
| `\t`         | Current time (24-hour format)    |
| `\T`         | Current time (12-hour format)    |
| `\@`         | Current time (AM/PM format)      |

---

## Customizing Your Terminal

You can also:

- Change **color schemes**
- Use different **fonts**
- Add **plugins** (like powerline)

This makes your terminal easier to use and nicer to look at.

> Tools like **bash-prompt-generator** or **powerline** help customize prompts easily.

---


Everything you do in the terminal can be recorded using:
- The `script` command
- Your `.bash_history` file

Useful for **note-taking**, **reporting**, or **repeating commands** later.

