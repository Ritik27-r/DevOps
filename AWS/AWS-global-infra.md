# AWS Global Infrastructure

## What is AWS Global Infrastructure?

AWS Global Infrastructure is the **physical and logical structure** that powers all AWS services across the world.

It is designed for:

* High availability
* Low latency
* Fault tolerance
* Global scalability

---

## Core Components

AWS infrastructure is built using:

```text id="aws_infra_01"
Regions → Availability Zones → Data Centers → Edge Locations
```

---

## 1. Regions

A **Region** is a geographic area that contains multiple data centers.

Examples:

* `ap-south-1` → Mumbai
* `us-east-1` → North Virginia
* `eu-west-1` → Ireland

---

### Why Regions Matter

* Data residency (legal requirements)
* Latency reduction
* Disaster isolation

---

### Key Rule

Each region is **completely isolated** from others.

If one region fails, others are unaffected.

---

## 2. Availability Zones (AZs)

Each Region contains multiple **Availability Zones**.

An AZ is:

* One or more physically separate data centers
* Connected with high-speed, low-latency links

Example:

```text id="aws_az_01"
Mumbai Region:
  - ap-south-1a
  - ap-south-1b
  - ap-south-1c
```

---

### Why AZs are Important

* Fault tolerance
* High availability
* Disaster recovery

---

### Best Practice

Deploy applications across **multiple AZs**.

---

## 3. Data Centers

Data centers are:

* Physical buildings
* Contain thousands of servers
* Host AWS infrastructure

AWS does NOT expose them directly.

---

## 4. Edge Locations

Edge locations are used for **fast content delivery**.

Used by:

* CloudFront (CDN)
* Route 53 (DNS)
* AWS Global Accelerator

---

### Purpose of Edge Locations

* Reduce latency
* Cache content closer to users
* Improve global performance

---

## AWS Global Network Flow

```text id="aws_flow_01"
User → Edge Location → Region → Availability Zone → Data Center
```

---

## Region vs Availability Zone

| Feature        | Region          | Availability Zone          |
| -------------- | --------------- | -------------------------- |
| Scope          | Geographic area | Data centers inside region |
| Isolation      | Fully isolated  | Connected within region    |
| Failure impact | Independent     | Region-level failover      |
| Example        | Mumbai          | ap-south-1a                |

---

## High Availability Architecture

A proper AWS setup uses multiple AZs:

```text id="aws_ha_01"
       Load Balancer
         /       \
     AZ-1        AZ-2
   EC2           EC2
     \           /
        Database (Multi-AZ)
```

---

## Fault Tolerance

AWS is designed so that:

* If one AZ fails → system continues running
* If one region fails → disaster recovery system activates

---

## Latency Optimization

AWS reduces latency using:

* Edge locations (closest to user)
* Region selection (nearest geography)
* CDN caching (CloudFront)

---

## Data Residency

Some countries require data to stay in specific regions.

Example:

* India → Mumbai region preferred
* EU → EU regions required

---

## AWS Service Availability by Region

Not all services exist in every region.

Example:

* Some AI services may be limited
* New services roll out in selected regions first

---

## Real-World Example

### Global Web App

```text id="aws_real_01"
User (India)
   ↓
Edge Location (Delhi)
   ↓
Region (Mumbai)
   ↓
EC2 + S3 + RDS
```

---

## Disaster Recovery Strategy

AWS supports multiple DR models:

### 1. Backup & Restore

* Cheapest
* Slow recovery

### 2. Pilot Light

* Minimal infrastructure running

### 3. Warm Standby

* Scaled-down version always running

### 4. Multi-Region Active-Active

* Fully live in multiple regions
* High cost, high availability

---

## Common Mistakes

* Using single AZ deployment
* Ignoring region selection
* Not planning disaster recovery
* Deploying everything in one location

---

## Best Practices

* Always use multi-AZ architecture
* Choose region closest to users
* Use edge locations for static content
* Plan for disaster recovery early
* Monitor latency and failover

---

## Summary

AWS Global Infrastructure provides:

* Global regions for isolation
* Availability zones for reliability
* Edge locations for speed
* Data centers for compute power

It is the backbone of AWS scalability and reliability.

---

## What Next?

Next topic:

👉 **IAM.md** (Identity and Access Management — the most important AWS service)

