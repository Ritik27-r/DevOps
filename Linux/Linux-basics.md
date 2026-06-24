# Linux Basics

## What is Linux?

Linux is an open-source operating system kernel created by Linus Torvalds in 1991. Most Linux distributions (distros) combine the Linux kernel with GNU utilities, package managers, and desktop environments.

### Popular Linux Distributions

* Ubuntu
* Debian
* Fedora
* CentOS Stream
* Rocky Linux
* Arch Linux
* Kali Linux
* openSUSE

### Why Use Linux?

* Free and open source
* Secure and stable
* Highly customizable
* Widely used in servers and cloud computing
* Powerful command-line interface
* Strong developer ecosystem

---

# Linux Architecture

```text
+---------------------+
|      User Apps      |
+---------------------+
|      Shell          |
+---------------------+
|      Kernel         |
+---------------------+
|     Hardware        |
+---------------------+
```

### Components

#### Kernel

The core of the operating system that manages:

* CPU
* Memory
* Devices
* Processes
* Filesystems

#### Shell

A command interpreter that allows users to interact with the system.

Examples:

* Bash
* Zsh
* Fish
* Sh

#### File System

Organizes files and directories in a hierarchical structure.

---

# Linux Directory Structure

```text
/
├── bin
├── boot
├── dev
├── etc
├── home
├── lib
├── media
├── mnt
├── opt
├── proc
├── root
├── run
├── sbin
├── srv
├── sys
├── tmp
├── usr
└── var
```

## Important Directories

### /

Root directory containing everything.

### /home

User home directories.

Example:

```bash
/home/john
```

### /root

Home directory of the root user.

### /etc

System configuration files.

Examples:

```bash
/etc/passwd
/etc/hostname
/etc/ssh/
```

### /bin

Essential user commands.

Examples:

```bash
ls
cp
mv
cat
```

### /usr

User applications and utilities.

### /var

Variable data such as logs.

Examples:

```bash
/var/log
```

### /tmp

Temporary files.

### /dev

Device files.

Examples:

```bash
/dev/sda
/dev/null
```

---

# Basic Linux Commands

## pwd

Displays the current working directory.

```bash
pwd
```

Output:

```text
/home/user
```

---

## ls

Lists files and directories.

```bash
ls
```

Useful options:

```bash
ls -l
ls -a
ls -lh
```

---

## cd

Changes directory.

```bash
cd Documents
cd ..
cd ~
cd /
```

---

## mkdir

Creates directories.

```bash
mkdir project
mkdir -p project/src
```

---

## rmdir

Removes empty directories.

```bash
rmdir project
```

---

## touch

Creates empty files.

```bash
touch file.txt
```

---

## cat

Displays file contents.

```bash
cat file.txt
```

---

## less

Views large files page by page.

```bash
less file.txt
```

Navigation:

* Space → Next page
* b → Previous page
* q → Quit

---

## cp

Copies files and directories.

```bash
cp file1.txt file2.txt
cp -r folder backup/
```

---

## mv

Moves or renames files.

```bash
mv file.txt docs/
mv old.txt new.txt
```

---

## rm

Deletes files and directories.

```bash
rm file.txt
rm -r folder
rm -rf folder
```

⚠️ Be careful with `rm -rf`.

---

# File Paths

## Absolute Path

Starts from root (`/`).

```bash
/home/user/Documents/file.txt
```

## Relative Path

Starts from current directory.

```bash
Documents/file.txt
```

---

# Getting Help

## man

Displays manual pages.

```bash
man ls
```

---

## --help

Shows command usage.

```bash
ls --help
```

---

## info

Detailed GNU documentation.

```bash
info ls
```

---

# Working with Files

## file

Determines file type.

```bash
file notes.txt
```

---

## head

Displays first lines.

```bash
head file.txt
head -n 20 file.txt
```

---

## tail

Displays last lines.

```bash
tail file.txt
tail -f /var/log/syslog
```

---

# Searching Files

## find

Search files and directories.

```bash
find . -name "*.txt"
find /home -type d
```

---

## locate

Fast file search.

```bash
locate file.txt
```

Update database:

```bash
sudo updatedb
```

---

## grep

Search text patterns.

```bash
grep "error" log.txt
grep -i "linux" file.txt
grep -r "main" .
```

---

# Process Management

## View Running Processes

```bash
ps
ps aux
```

---

## Real-Time Process Monitoring

```bash
top
```

Modern alternative:

```bash
htop
```

---

## Kill a Process

```bash
kill PID
kill -9 PID
```

Example:

```bash
kill 1234
```

---

# Package Management

## Debian / Ubuntu

```bash
sudo apt update
sudo apt upgrade
sudo apt install nginx
```

---

## Fedora

```bash
sudo dnf install nginx
```

---

## Arch Linux

```bash
sudo pacman -S nginx
```

---

# Users and Groups

## Current User

```bash
whoami
```

---

## User Information

```bash
id
```

---

## Switch User

```bash
su username
```

---

## Run as Root

```bash
sudo command
```

Example:

```bash
sudo apt update
```

---

# Networking Basics

## Check IP Address

```bash
ip addr
```

Alternative:

```bash
hostname -I
```

---

## Test Connectivity

```bash
ping google.com
```

---

## DNS Lookup

```bash
nslookup google.com
```

---

## Download Files

```bash
wget URL
curl URL
```

Examples:

```bash
wget https://example.com/file.zip
curl -O https://example.com/file.zip
```

---

# Disk Usage

## Show Filesystem Usage

```bash
df -h
```

---

## Show Directory Size

```bash
du -sh folder/
```

---

# Archives and Compression

## Create Tar Archive

```bash
tar -cvf archive.tar folder/
```

---

## Extract Archive

```bash
tar -xvf archive.tar
```

---

## Gzip Compression

```bash
gzip file.txt
gunzip file.txt.gz
```

---

# Environment Variables

View variables:

```bash
printenv
```

Example:

```bash
echo $HOME
echo $PATH
```

Set variable:

```bash
export NAME="Linux"
```

---

# Useful Shortcuts

| Shortcut | Description            |
| -------- | ---------------------- |
| Ctrl + C | Stop process           |
| Ctrl + Z | Suspend process        |
| Ctrl + L | Clear terminal         |
| Ctrl + D | Logout / EOF           |
| Tab      | Auto-complete          |
| Up Arrow | Previous command       |
| Ctrl + R | Search command history |

---

# Summary

Essential commands every Linux user should know:

```bash
pwd
ls
cd
mkdir
touch
cat
cp
mv
rm
find
grep
ps
top
kill
df
du
tar
curl
wget
sudo
```

Master these commands before moving on to:

1. File Permissions
2. Shell Scripting
3. Process Management
4. Networking
5. System Administration

