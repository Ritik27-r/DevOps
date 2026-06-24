# AWS Interview Notes

## Purpose of This File

This file is a **quick revision guide** for AWS interviews:

* Core concepts
* Common questions
* Real-world scenarios
* Architecture thinking

---

## 1. Basic AWS Questions

### What is AWS?

AWS is a cloud platform that provides:

* Compute
* Storage
* Networking
* Databases
* Security services

---

### What is Cloud Computing?

On-demand delivery of computing resources over the internet with:

* Pay-as-you-go pricing
* Scalability
* No hardware management

---

### What are the types of cloud models?

* IaaS → EC2
* PaaS → Elastic Beanstalk
* SaaS → Gmail, Google Drive

---

## 2. Core AWS Services Questions

### What is EC2?

EC2 is a virtual server in AWS used to run applications.

Key points:

* Resizable compute
* Pay-per-use
* Full OS control

---

### What is S3?

S3 is object storage used for:

* Files
* Backups
* Static websites

Features:

* Highly durable
* Scalable
* Secure

---

### What is IAM?

IAM manages:

* Users
* Roles
* Permissions

Most important AWS service for security.

---

## 3. Networking Questions

### What is a VPC?

A VPC is a private network inside AWS where you deploy resources securely.

---

### Public vs Private Subnet?

| Public Subnet   | Private Subnet     |
| --------------- | ------------------ |
| Internet access | No direct internet |
| Web servers     | Databases          |

---

### What is NAT Gateway?

Allows private subnet to access internet securely without being exposed.

---

## 4. Load Balancing Questions

### What is ELB?

Elastic Load Balancer distributes traffic across multiple instances.

Types:

* ALB (HTTP/HTTPS)
* NLB (TCP/UDP)

---

### Why use Load Balancer?

* High availability
* Fault tolerance
* Traffic distribution

---

## 5. Auto Scaling Questions

### What is Auto Scaling?

Automatically adjusts number of EC2 instances based on demand.

---

### Difference between scaling types?

* Scale out → Add instances
* Scale in → Remove instances

---

## 6. Storage Questions

### Difference: S3 vs EBS vs EFS

| Service | Type   | Use Case       |
| ------- | ------ | -------------- |
| S3      | Object | Files, backups |
| EBS     | Block  | EC2 storage    |
| EFS     | File   | Shared storage |

---

## 7. Security Questions

### What is Shared Responsibility Model?

AWS secures infrastructure, user secures data and access.

---

### What is IAM policy?

A JSON document that defines permissions for AWS resources.

---

### What is MFA?

Multi-Factor Authentication adds extra security layer using OTP.

---

## 8. Monitoring Questions

### What is CloudWatch?

Service used for:

* Monitoring metrics
* Logs
* Alerts

---

### Difference: CloudWatch vs CloudTrail

| CloudWatch  | CloudTrail           |
| ----------- | -------------------- |
| Monitoring  | Logging API activity |
| Performance | Audit history        |

---

## 9. DNS Questions

### What is Route 53?

AWS DNS service used for:

* Domain routing
* Traffic management
* Health checks

---

## 10. Scenario-Based Questions

### Q1: How will you design a highly available web app?

Answer:

```text id="aws_scenario_01"
Route 53 → Load Balancer → EC2 (Multi-AZ) → RDS (Multi-AZ) → S3
```

---

### Q2: How do you secure an AWS environment?

* IAM least privilege
* MFA enabled
* Private subnets for DB
* Security groups restricted
* Encryption enabled
* Logging enabled

---

### Q3: What happens if EC2 fails?

* Auto Scaling replaces instance
* Load Balancer removes unhealthy instance
* Traffic redirected to healthy instance

---

## 11. Common Interview Traps

* Confusing Security Group vs NACL
* Not knowing VPC basics
* Ignoring IAM importance
* Weak understanding of networking
* Not explaining architecture clearly

---

## 12. Real-World Architecture Answer

Always structure like this:

```text id="aws_arch_ans_01"
User → Route 53 → CloudFront → ALB → EC2 (ASG)
                               ↓
                            RDS (Private Subnet)
                               ↓
                              S3
```

---

## 13. Important One-Liners

* IAM = Identity & Access Management
* S3 = Object Storage
* EC2 = Virtual Server
* VPC = Private Network
* ELB = Traffic Distributor
* CloudWatch = Monitoring
* Route 53 = DNS

---

## 14. Final Interview Advice

* Always explain with architecture diagrams
* Focus on real-world usage
* Don’t memorize—understand flow
* Security is always important
* Keep answers structured

---

## Summary

AWS interviews test:

* Core services
* Networking (very important)
* Security mindset
* Architecture thinking
* Real-world problem solving

---

## End of AWS Section

You now have a complete AWS knowledge base in your repo:

* Basics → Architecture → IAM → EC2 → S3 → VPC → Networking → Security → Interview prep

---

If you want next step, I can build:

👉 **Terraform folder (Infrastructure as Code — very high-value DevOps skill)**
or
👉 **Kubernetes deep advanced level (production-grade setups)**
or
👉 **CI/CD pipeline notes (Jenkins + GitHub Actions)**

