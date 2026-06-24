# Linux Networking

## Introduction

Networking in Linux allows systems to communicate with each other over local networks and the internet. Linux provides powerful tools for network configuration, troubleshooting, monitoring, and security.

---

# Networking Fundamentals

## Key Terms

### IP Address

A unique address assigned to a device on a network.

Example IPv4:

```text
192.168.1.10
```

Example IPv6:

```text
2001:db8::1
```

---

### Subnet Mask

Defines the network and host portions of an IP address.

Example:

```text
255.255.255.0
```

CIDR notation:

```text
192.168.1.0/24
```

---

### Gateway

A router that connects a local network to external networks.

Example:

```text
192.168.1.1
```

---

### DNS (Domain Name System)

Converts domain names into IP addresses.

Example:

```text
google.com → 142.250.x.x
```

---

### Port

A logical communication endpoint.

Common ports:

| Port | Service    |
| ---- | ---------- |
| 22   | SSH        |
| 53   | DNS        |
| 80   | HTTP       |
| 443  | HTTPS      |
| 3306 | MySQL      |
| 5432 | PostgreSQL |

---

# Network Configuration

## View Network Interfaces

```bash
ip link
```

Example output:

```text
1: lo
2: eth0
3: wlan0
```

---

## View IP Addresses

```bash
ip addr
```

Short version:

```bash
ip a
```

---

## View Routing Table

```bash
ip route
```

Example:

```text
default via 192.168.1.1 dev eth0
192.168.1.0/24 dev eth0
```

---

## Display Network Statistics

```bash
ip -s link
```

---

# Interface Management

## Enable Interface

```bash
sudo ip link set eth0 up
```

---

## Disable Interface

```bash
sudo ip link set eth0 down
```

---

## Assign Static IP

```bash
sudo ip addr add 192.168.1.100/24 dev eth0
```

---

## Remove IP Address

```bash
sudo ip addr del 192.168.1.100/24 dev eth0
```

---

# Hostname Management

## View Hostname

```bash
hostname
```

---

## Set Temporary Hostname

```bash
sudo hostname server01
```

---

## Set Permanent Hostname

```bash
sudo hostnamectl set-hostname server01
```

Verify:

```bash
hostnamectl
```

---

# DNS Configuration

## View DNS Servers

```bash
cat /etc/resolv.conf
```

Example:

```text
nameserver 8.8.8.8
nameserver 1.1.1.1
```

---

## Test DNS Resolution

```bash
nslookup google.com
```

Alternative:

```bash
dig google.com
```

---

# Connectivity Testing

## ping

Tests network connectivity.

```bash
ping google.com
```

Limit packets:

```bash
ping -c 4 google.com
```

---

## traceroute

Shows path packets take.

Install:

```bash
sudo apt install traceroute
```

Usage:

```bash
traceroute google.com
```

---

## tracepath

Alternative to traceroute.

```bash
tracepath google.com
```

---

# Network Connections

## netstat

View network connections.

```bash
netstat -tulnp
```

Options:

| Option | Meaning   |
| ------ | --------- |
| -t     | TCP       |
| -u     | UDP       |
| -l     | Listening |
| -n     | Numeric   |
| -p     | Process   |

---

## ss

Modern replacement for netstat.

```bash
ss -tulnp
```

View established connections:

```bash
ss -tan
```

---

# Port Checking

## Check Open Ports

```bash
ss -tuln
```

---

## Check Specific Port

```bash
nc -zv localhost 22
```

Example:

```bash
nc -zv google.com 443
```

---

# Downloading Data

## curl

Retrieve data from URLs.

```bash
curl https://example.com
```

Download file:

```bash
curl -O https://example.com/file.zip
```

View headers:

```bash
curl -I https://google.com
```

---

## wget

Download files.

```bash
wget https://example.com/file.zip
```

Resume download:

```bash
wget -c https://example.com/file.zip
```

---

# SSH (Secure Shell)

## Connect to Remote Server

```bash
ssh user@server_ip
```

Example:

```bash
ssh ubuntu@192.168.1.100
```

---

## Connect Using Custom Port

```bash
ssh -p 2222 user@server_ip
```

---

## Copy File Using SCP

Upload:

```bash
scp file.txt user@server:/home/user/
```

Download:

```bash
scp user@server:/home/user/file.txt .
```

---

# Network Monitoring

## Monitor Bandwidth

Install:

```bash
sudo apt install iftop
```

Run:

```bash
sudo iftop
```

---

## Real-Time Traffic Monitoring

Install:

```bash
sudo apt install nload
```

Run:

```bash
nload
```

---

## Interface Statistics

```bash
cat /proc/net/dev
```

---

# Firewall Basics

## UFW (Ubuntu Firewall)

Enable firewall:

```bash
sudo ufw enable
```

---

## Check Status

```bash
sudo ufw status
```

---

## Allow SSH

```bash
sudo ufw allow 22
```

---

## Allow HTTP

```bash
sudo ufw allow 80
```

---

## Allow HTTPS

```bash
sudo ufw allow 443
```

---

## Delete Rule

```bash
sudo ufw delete allow 80
```

---

# Packet Analysis

## tcpdump

Capture packets.

Install:

```bash
sudo apt install tcpdump
```

Capture traffic:

```bash
sudo tcpdump
```

Capture on interface:

```bash
sudo tcpdump -i eth0
```

Capture SSH traffic:

```bash
sudo tcpdump port 22
```

Save capture:

```bash
sudo tcpdump -w capture.pcap
```

---

# NetworkManager

## View Connections

```bash
nmcli connection show
```

---

## View Devices

```bash
nmcli device status
```

---

## Connect to Wi-Fi

```bash
nmcli dev wifi list
```

Connect:

```bash
nmcli dev wifi connect "WiFi_Name" password "Password"
```

---

# Common Troubleshooting Workflow

## Step 1: Verify Interface

```bash
ip addr
```

---

## Step 2: Verify Gateway

```bash
ip route
```

---

## Step 3: Ping Local Gateway

```bash
ping 192.168.1.1
```

---

## Step 4: Ping Public IP

```bash
ping 8.8.8.8
```

If this works but domain names fail, DNS is the problem.

---

## Step 5: Test DNS

```bash
nslookup google.com
```

or

```bash
dig google.com
```

---

## Step 6: Check Open Ports

```bash
ss -tulnp
```

---

## Step 7: Check Firewall

```bash
sudo ufw status
```

---

# Useful Files

| File                    | Purpose                |
| ----------------------- | ---------------------- |
| /etc/hosts              | Local hostname mapping |
| /etc/resolv.conf        | DNS servers            |
| /etc/hostname           | System hostname        |
| /etc/network/interfaces | Debian network config  |
| /etc/netplan/*.yaml     | Ubuntu network config  |
| /etc/ssh/sshd_config    | SSH server settings    |

---

# Essential Networking Commands

```bash
ip addr
ip route
ping
traceroute
tracepath
ss
netstat
curl
wget
ssh
scp
nslookup
dig
tcpdump
nmcli
ufw
```

---

# Summary

Networking skills are essential for Linux administration, DevOps, cloud computing, and cybersecurity.

Master these topics in order:

1. IP Addressing
2. Routing
3. DNS
4. SSH
5. Network Troubleshooting
6. Firewalls
7. Packet Analysis
8. Network Monitoring

After networking, the next recommended notes are:

* Process-Management.md
* Package-Management.md
* Systemd-and-Services.md
* Storage-and-Disks.md
* Bash-Scripting.md
* Linux-Security.md
* DevOps-Linux.md

