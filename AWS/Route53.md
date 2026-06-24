# AWS Route 53 (DNS Service)

## What is Route 53?

Amazon Route 53 is a **highly available and scalable Domain Name System (DNS) service**.

It converts:

> Domain names → IP addresses

Example:

```text id="r53_dns_01"
google.com → 142.250.190.14
```

---

## Why Route 53 is Used

* Domain registration
* DNS routing
* Traffic management
* Health checking
* High availability routing

---

## DNS Basics

DNS works like a phonebook:

```text id="dns_basic_01"
User types domain → DNS finds IP → Connect to server
```

---

## Route 53 Core Components

### 1. Domain Registration

You can buy domains directly in Route 53:

* example.com
* myapp.io

---

### 2. Hosted Zones

A hosted zone is a **container for DNS records**.

Types:

* Public Hosted Zone (internet)
* Private Hosted Zone (VPC only)

---

## 3. DNS Records

### A Record

Maps domain → IPv4 address

```text id="r53_a_01"
example.com → 192.0.2.1
```

---

### AAAA Record

Maps domain → IPv6 address

---

### CNAME Record

Maps domain → another domain

```text id="r53_cname_01"
www.example.com → example.com
```

---

### MX Record

Handles email routing

---

### TXT Record

Stores text data (used for verification)

---

## Route 53 Routing Policies

### 1. Simple Routing

One domain → one IP

---

### 2. Weighted Routing

Distributes traffic based on weights

```text id="r53_weight_01"
70% → Server A
30% → Server B
```

---

### 3. Latency-Based Routing

Routes users to **nearest server**

Example:

* India users → Mumbai region
* US users → Virginia region

---

### 4. Failover Routing

Primary + backup setup

```text id="r53_failover_01"
Primary server → Active
Backup server → Activated if failure
```

---

### 5. Geolocation Routing

Routes based on user location

---

## Route 53 Health Checks

Monitors:

* Server uptime
* Endpoint availability
* Application health

If failure detected:

* Traffic is redirected

---

## DNS Resolution Flow

```text id="dns_flow_01"
User → Route 53 → DNS Lookup → IP Address → Server
```

---

## Route 53 + AWS Architecture

```text id="r53_arch_01"
User → Route 53 → Load Balancer → EC2 → Database
```

---

## TTL (Time To Live)

Defines how long DNS records are cached.

Example:

```text id="r53_ttl_01"
TTL = 60 seconds → Faster updates but more queries
TTL = 3600 seconds → Slower updates but cached longer
```

---

## Public vs Private Hosted Zones

| Feature  | Public Zone | Private Zone  |
| -------- | ----------- | ------------- |
| Access   | Internet    | VPC only      |
| Use case | Websites    | Internal apps |

---

## Route 53 Use Cases

* Website hosting
* Load balancing traffic
* Disaster recovery
* Multi-region deployment
* API routing

---

## Real-World Example

### Global Web App

```text id="r53_real_01"
User (India)
   ↓
Route 53
   ↓
Mumbai Region (Low latency)
   ↓
EC2 + ALB
```

---

## Common Route 53 Mistakes

* Wrong DNS records (A vs CNAME confusion)
* High TTL causing slow updates
* Misconfigured failover routing
* Not setting health checks
* Using single region routing

---

## Best Practices

* Use low TTL for frequently changing apps
* Enable health checks
* Use latency-based routing for global apps
* Use failover for disaster recovery
* Keep DNS records clean and minimal

---

## Route 53 vs Traditional DNS

| Feature          | Route 53     | Traditional DNS |
| ---------------- | ------------ | --------------- |
| Scalability      | Global       | Limited         |
| Health checks    | Yes          | No              |
| Routing policies | Advanced     | Basic           |
| Integration      | AWS services | Limited         |

---

## Summary

Route 53 provides:

* Domain management
* DNS resolution
* Traffic routing
* Health-based failover
* Global scalability

---

## What Next?

Next topic:

👉 **Elastic-Load-Balancing.md** (traffic distribution, ALB, NLB, and scaling architecture)

