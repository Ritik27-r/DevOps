# File Permissions

## Introduction

Linux is a multi-user operating system. File permissions control who can:

* Read files
* Modify files
* Execute files
* Access directories

Permissions are a critical part of Linux security.

---

# Understanding Permissions

Run:

```bash
ls -l
```

Example output:

```text
-rwxr-xr-- 1 user developers 1024 Jun 24 10:00 script.sh
```

Breakdown:

```text
-rwxr-xr--
││ │ │
││ │ └── Others Permissions
││ └──── Group Permissions
│└────── Owner Permissions
└──────── File Type
```

---

# File Types

The first character indicates the file type.

| Symbol | Type             |
| ------ | ---------------- |
| -      | Regular File     |
| d      | Directory        |
| l      | Symbolic Link    |
| c      | Character Device |
| b      | Block Device     |
| p      | Named Pipe       |
| s      | Socket           |

Examples:

```text
-rw-r--r-- file.txt
drwxr-xr-x Documents/
lrwxrwxrwx shortcut -> file.txt
```

---

# Permission Types

Linux uses three basic permissions:

| Symbol | Meaning | Value |
| ------ | ------- | ----- |
| r      | Read    | 4     |
| w      | Write   | 2     |
| x      | Execute | 1     |

---

# Permission Groups

Permissions are assigned to:

| Group      | Description           |
| ---------- | --------------------- |
| User (u)   | File owner            |
| Group (g)  | Members of file group |
| Others (o) | Everyone else         |

Example:

```text
-rwxr-xr--
```

Breakdown:

```text
Owner  : rwx
Group  : r-x
Others : r--
```

Meaning:

* Owner can read, write, execute
* Group can read and execute
* Others can only read

---

# Numeric Permission System

Each permission has a numeric value.

```text
Read    = 4
Write   = 2
Execute = 1
```

Add them together:

| Permission | Value |
| ---------- | ----- |
| rwx        | 7     |
| rw-        | 6     |
| r-x        | 5     |
| r--        | 4     |
| --x        | 1     |
| ---        | 0     |

Examples:

```text
755 = rwxr-xr-x
644 = rw-r--r--
700 = rwx------
600 = rw-------
777 = rwxrwxrwx
```

---

# chmod Command

Used to change permissions.

Syntax:

```bash
chmod [permissions] file
```

---

## Numeric Method

Example:

```bash
chmod 755 script.sh
```

Result:

```text
rwxr-xr-x
```

---

### Common Permission Values

#### 644

```bash
chmod 644 file.txt
```

```text
rw-r--r--
```

Typical for text files.

---

#### 755

```bash
chmod 755 script.sh
```

```text
rwxr-xr-x
```

Typical for executable scripts.

---

#### 700

```bash
chmod 700 private.sh
```

```text
rwx------
```

Only owner has access.

---

#### 600

```bash
chmod 600 secrets.txt
```

```text
rw-------
```

Good for passwords and SSH keys.

---

# Symbolic Method

Syntax:

```bash
chmod [who][operator][permission] file
```

Where:

```text
u = user
g = group
o = others
a = all
```

Operators:

```text
+ Add permission
- Remove permission
= Set exact permission
```

---

## Examples

Add execute permission:

```bash
chmod +x script.sh
```

Equivalent:

```bash
chmod a+x script.sh
```

---

Add write permission for owner:

```bash
chmod u+w file.txt
```

---

Remove execute permission:

```bash
chmod -x script.sh
```

---

Remove read permission from others:

```bash
chmod o-r file.txt
```

---

Set exact permissions:

```bash
chmod u=rwx,g=rx,o=r file.txt
```

Result:

```text
rwxr-xr--
```

---

# Directory Permissions

Permissions behave differently on directories.

Assume:

```text
drwxr-xr-x
```

---

## Read (r)

Allows viewing directory contents.

```bash
ls directory
```

---

## Write (w)

Allows:

* Create files
* Delete files
* Rename files

---

## Execute (x)

Allows entering the directory.

```bash
cd directory
```

Without execute permission:

```bash
cd directory
```

fails even if read permission exists.

---

# Ownership

Every file has:

* Owner
* Group

View ownership:

```bash
ls -l
```

Example:

```text
-rw-r--r-- 1 john developers file.txt
```

Owner:

```text
john
```

Group:

```text
developers
```

---

# chown Command

Change file owner.

Syntax:

```bash
sudo chown owner file
```

Example:

```bash
sudo chown john file.txt
```

---

Change owner and group:

```bash
sudo chown john:developers file.txt
```

---

Recursive ownership change:

```bash
sudo chown -R john:developers project/
```

---

# chgrp Command

Change group ownership.

Syntax:

```bash
chgrp group file
```

Example:

```bash
chgrp developers file.txt
```

---

# Default Permissions

When creating files:

```bash
touch file.txt
```

Typical permission:

```text
644
```

When creating directories:

```bash
mkdir test
```

Typical permission:

```text
755
```

These defaults are affected by:

```bash
umask
```

---

# Understanding umask

View current umask:

```bash
umask
```

Example:

```text
0022
```

Default permissions:

Files:

```text
666 - 022 = 644
```

Directories:

```text
777 - 022 = 755
```

---

Set temporary umask:

```bash
umask 027
```

New files:

```text
640
```

New directories:

```text
750
```

---

# Special Permissions

Linux supports three special permissions:

1. SUID
2. SGID
3. Sticky Bit

---

# SUID (Set User ID)

Allows a program to run with the owner's privileges.

Example:

```bash
ls -l /usr/bin/passwd
```

Output:

```text
-rwsr-xr-x
```

Notice:

```text
s
```

instead of:

```text
x
```

Set SUID:

```bash
chmod u+s file
```

Numeric:

```bash
chmod 4755 file
```

---

# SGID (Set Group ID)

Runs a program with group privileges.

For directories:

New files inherit the directory group.

Set SGID:

```bash
chmod g+s directory
```

Numeric:

```bash
chmod 2755 directory
```

---

# Sticky Bit

Used mainly on shared directories.

Example:

```bash
ls -ld /tmp
```

Output:

```text
drwxrwxrwt
```

Meaning:

Users can only delete their own files.

Set Sticky Bit:

```bash
chmod +t directory
```

Numeric:

```bash
chmod 1777 directory
```

---

# Access Control Lists (ACL)

ACLs provide more granular permissions.

Check ACL:

```bash
getfacl file.txt
```

---

Grant permission:

```bash
setfacl -m u:alice:rwx file.txt
```

Grant group permission:

```bash
setfacl -m g:developers:r-x file.txt
```

Remove ACL:

```bash
setfacl -x u:alice file.txt
```

---

# Useful Permission Examples

## Make Script Executable

```bash
chmod +x script.sh
```

---

## Secure SSH Private Key

```bash
chmod 600 ~/.ssh/id_rsa
```

---

## Secure SSH Directory

```bash
chmod 700 ~/.ssh
```

---

## Shared Team Directory

```bash
chmod 2775 shared/
```

SGID ensures new files inherit the group.

---

## Public Read-Only File

```bash
chmod 644 notes.txt
```

---

# Permission Troubleshooting

## Permission Denied

Example:

```bash
./script.sh
```

Error:

```text
Permission denied
```

Fix:

```bash
chmod +x script.sh
```

---

## Cannot Access Directory

Check:

```bash
ls -ld directory
```

Ensure execute permission exists:

```bash
chmod +x directory
```

---

## Ownership Problems

Check ownership:

```bash
ls -l
```

Fix:

```bash
sudo chown user:group file
```

---

# Security Best Practices

✅ Use least privilege

✅ Avoid `777`

✅ Restrict sensitive files

```bash
chmod 600 secrets.txt
```

✅ Use groups instead of giving permissions to everyone

✅ Regularly audit permissions

```bash
find / -perm -4000
```

Search SUID files:

```bash
find / -perm -4000 2>/dev/null
```

Search SGID files:

```bash
find / -perm -2000 2>/dev/null
```

---

# Quick Reference

| Command | Purpose                 |
| ------- | ----------------------- |
| ls -l   | View permissions        |
| chmod   | Change permissions      |
| chown   | Change owner            |
| chgrp   | Change group            |
| umask   | Set default permissions |
| getfacl | View ACLs               |
| setfacl | Set ACLs                |

---

# Summary

Linux permissions are based on:

* Read (r = 4)
* Write (w = 2)
* Execute (x = 1)

Applied to:

* User
* Group
* Others

Essential commands:

```bash
chmod
chown
chgrp
umask
getfacl
setfacl
```

Understanding permissions is essential for Linux security, system administration, DevOps, cloud computing, and server management.

