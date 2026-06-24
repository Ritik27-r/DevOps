# Process Management in Linux

## What is a Process?

A **process** is a running instance of a program.

Examples:

* Running `vim`
* Opening a web browser
* Executing a shell script
* Running a web server like Nginx

Every process in Linux is assigned a unique **Process ID (PID)**.

---

# Process Lifecycle

```text
New
 │
 ▼
Ready
 │
 ▼
Running
 │
 ├──► Waiting/Blocked
 │          │
 │          ▼
 └──────► Ready
 │
 ▼
Terminated
```

### States

| State        | Description                 |
| ------------ | --------------------------- |
| Running (R)  | Currently executing         |
| Sleeping (S) | Waiting for an event        |
| Stopped (T)  | Suspended process           |
| Zombie (Z)   | Finished but not cleaned up |
| Dead (X)     | Process terminated          |

---

# Viewing Processes

## ps Command

Displays currently running processes.

```bash
ps
```

Example Output:

```text
PID TTY          TIME CMD
1023 pts/0    00:00:00 bash
1050 pts/0    00:00:00 ps
```

---

## ps aux

Shows all processes running on the system.

```bash
ps aux
```

Columns:

| Column  | Meaning          |
| ------- | ---------------- |
| USER    | Process owner    |
| PID     | Process ID       |
| %CPU    | CPU usage        |
| %MEM    | Memory usage     |
| VSZ     | Virtual memory   |
| RSS     | Physical memory  |
| STAT    | Process state    |
| COMMAND | Executed command |

---

## ps -ef

Alternative format for viewing all processes.

```bash
ps -ef
```

Useful for scripting and filtering.

---

# Real-Time Process Monitoring

## top

Displays live process information.

```bash
top
```

Information shown:

* CPU usage
* Memory usage
* Running processes
* Load averages

Useful keys inside top:

| Key | Action         |
| --- | -------------- |
| q   | Quit           |
| k   | Kill process   |
| M   | Sort by memory |
| P   | Sort by CPU    |

---

## htop

Enhanced version of top.

```bash
htop
```

Features:

* Colorized output
* Mouse support
* Easier navigation
* Process tree visualization

Installation:

Ubuntu/Debian:

```bash
sudo apt install htop
```

Fedora:

```bash
sudo dnf install htop
```

Arch:

```bash
sudo pacman -S htop
```

---

# Finding Specific Processes

## pgrep

Find process IDs by name.

```bash
pgrep nginx
```

Output:

```text
1254
```

---

## pidof

Find PID of a running program.

```bash
pidof nginx
```

---

## grep with ps

```bash
ps aux | grep nginx
```

Example:

```bash
ps aux | grep python
```

---

# Process Tree

Displays parent-child process relationships.

## pstree

```bash
pstree
```

Example:

```text
systemd─┬─sshd───bash───vim
        └─nginx
```

Show PIDs:

```bash
pstree -p
```

---

# Process Priority

Linux schedules CPU time based on priority.

Priority ranges:

```text
-20 (Highest Priority)
  0 (Default)
 19 (Lowest Priority)
```

---

## nice

Start a process with a custom priority.

```bash
nice -n 10 command
```

Example:

```bash
nice -n 5 python app.py
```

---

## renice

Change priority of a running process.

```bash
renice 10 -p 1234
```

Example:

```bash
sudo renice -5 -p 1234
```

---

# Background Processes

## Running in Background

Use `&` at the end of a command.

```bash
sleep 100 &
```

Output:

```text
[1] 1234
```

Where:

* 1 = Job Number
* 1234 = PID

---

# Job Control

## View Jobs

```bash
jobs
```

Example:

```text
[1]+ Running sleep 100 &
```

---

## Send Process to Background

Press:

```text
Ctrl + Z
```

Then:

```bash
bg
```

---

## Bring Process to Foreground

```bash
fg
```

Specific job:

```bash
fg %1
```

---

# Killing Processes

## kill

Terminate a process by PID.

```bash
kill PID
```

Example:

```bash
kill 1234
```

---

## kill -9

Forcefully terminate a process.

```bash
kill -9 1234
```

Signal:

```text
SIGKILL (9)
```

Use only when normal termination fails.

---

## pkill

Kill processes by name.

```bash
pkill nginx
```

---

## killall

Terminate all matching processes.

```bash
killall firefox
```

---

# Linux Signals

Signals are used to communicate with processes.

View all signals:

```bash
kill -l
```

Common signals:

| Signal  | Number | Description             |
| ------- | ------ | ----------------------- |
| SIGTERM | 15     | Graceful termination    |
| SIGKILL | 9      | Force kill              |
| SIGSTOP | 19     | Pause process           |
| SIGCONT | 18     | Continue paused process |
| SIGINT  | 2      | Interrupt (Ctrl+C)      |

Examples:

```bash
kill -SIGTERM 1234
kill -9 1234
```

---

# Foreground vs Background Processes

## Foreground Process

Runs directly in the terminal.

Example:

```bash
python app.py
```

Terminal remains occupied.

---

## Background Process

Runs independently.

Example:

```bash
python app.py &
```

Terminal remains usable.

---

# Daemons

A **daemon** is a background service process.

Examples:

* sshd
* nginx
* cron
* systemd

Check daemon status:

```bash
systemctl status nginx
```

---

# Managing Services with systemctl

## Start Service

```bash
sudo systemctl start nginx
```

---

## Stop Service

```bash
sudo systemctl stop nginx
```

---

## Restart Service

```bash
sudo systemctl restart nginx
```

---

## Reload Configuration

```bash
sudo systemctl reload nginx
```

---

## Check Status

```bash
systemctl status nginx
```

---

## Enable at Boot

```bash
sudo systemctl enable nginx
```

---

## Disable at Boot

```bash
sudo systemctl disable nginx
```

---

# Monitoring Resource Usage

## CPU Usage

```bash
top
```

or

```bash
htop
```

---

## Memory Usage

```bash
free -h
```

Example Output:

```text
Total  Used  Free
16GB   8GB   8GB
```

---

## Disk Usage

```bash
df -h
```

---

# Zombie Processes

A zombie process:

* Has completed execution
* Still has an entry in the process table
* Waits for its parent process to collect exit status

Identify zombies:

```bash
ps aux | grep Z
```

Example:

```text
root  1234  Z
```

---

# Process Scheduling

Linux uses schedulers to decide CPU allocation.

Common schedulers:

* Completely Fair Scheduler (CFS)
* Real-Time Scheduler

View scheduling information:

```bash
chrt -p PID
```

Example:

```bash
chrt -p 1234
```

---

# Useful Process Management Commands

```bash
ps aux
ps -ef
top
htop
pgrep nginx
pidof nginx
pstree
jobs
bg
fg
kill PID
kill -9 PID
pkill nginx
killall firefox
nice -n 10 command
renice 10 -p PID
free -h
systemctl status nginx
```

---

# Common Interview Questions

### What is a process?

A running instance of a program.

---

### What is a PID?

A unique Process ID assigned by the kernel.

---

### Difference Between Process and Program?

| Program                | Process             |
| ---------------------- | ------------------- |
| Static file on disk    | Running instance    |
| Passive                | Active              |
| No resources allocated | Resources allocated |

---

### What is a Zombie Process?

A terminated process whose parent has not yet collected its exit status.

---

### Difference Between kill and kill -9?

| Command     | Behavior                 |
| ----------- | ------------------------ |
| kill PID    | Sends SIGTERM (graceful) |
| kill -9 PID | Sends SIGKILL (forceful) |

---

### Difference Between Foreground and Background Process?

| Foreground      | Background              |
| --------------- | ----------------------- |
| Uses terminal   | Runs independently      |
| Blocks terminal | Terminal remains usable |

---

# Summary

Process management involves:

* Viewing processes (`ps`, `top`, `htop`)
* Searching processes (`pgrep`, `pidof`)
* Managing jobs (`bg`, `fg`, `jobs`)
* Controlling priorities (`nice`, `renice`)
* Sending signals (`kill`, `pkill`, `killall`)
* Managing services (`systemctl`)
* Monitoring system resources (`free`, `top`, `df`)

Mastering these commands is essential for Linux administration, DevOps, cloud engineering, and troubleshooting production systems.

