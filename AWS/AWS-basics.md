# AWS Basics

## What is AWS?

Amazon Web Services (AWS) is a **cloud computing platform** that provides on-demand computing resources like servers, storage, databases, networking, and more.

Instead of owning physical hardware, you rent infrastructure from AWS.

---

## Why AWS is Used

* No need for physical servers
* Pay only for what you use (pay-as-you-go)
* Scalable on demand
* Highly available and reliable
* Global infrastructure

---

## Cloud Computing Models

### 1. IaaS (Infrastructure as a Service)

You get virtual infrastructure.

Example:

* EC2 (virtual servers)
* EBS (storage)

---

### 2. PaaS (Platform as a Service)

You deploy code without managing servers.

Example:

* Elastic Beanstalk

---

### 3. SaaS (Software as a Service)

Ready-to-use software.

Example:

* Gmail
* Google Drive

---

## AWS Global Structure

AWS is built using:

```text id="aws_geo_01"
Regions → Availability Zones → Data Centers
```

---

### Region

A **geographical area** (e.g., Mumbai, US-East).

---

### Availability Zone (AZ)

Multiple isolated data centers inside a region.

---

### Data Center

Physical machines where AWS services run.

---

## AWS Core Service Categories

### 1. Compute

* EC2
* Lambda
* ECS / EKS

---

### 2. Storage

* S3
* EBS
* EFS

---

### 3. Networking

* VPC
* Route 53
* Load Balancer

---

### 4. Security

* IAM
* KMS

---

### 5. Monitoring

* CloudWatch
* CloudTrail

---

## Pay-as-you-go Model

You are billed based on usage:

* Compute time (seconds/minutes)
* Storage used (GB)
* Network traffic

Example:

```text id="aws_bill_01"
EC2 running for 10 hours → you pay for 10 hours only
```

---

## AWS Free Tier

AWS offers free usage limits for beginners:

* EC2 (limited hours/month)
* S3 storage (limited GB)
* Lambda requests (limited invocations)

---

## Shared Responsibility Model

AWS splits responsibility:

### AWS handles:

* Physical hardware
* Data center security
* Network infrastructure

### You handle:

* Your data
* IAM access
* Application security
* Configurations

---

## AWS Console vs CLI

### AWS Management Console

* Web UI
* Beginner-friendly

### AWS CLI

* Command line tool
* Used in automation and DevOps

Example:

```bash id="aws_cli_01"
aws s3 ls
```

---

## Key AWS Concepts

### 1. Scalability

Ability to handle increased load automatically.

---

### 2. High Availability

System runs even if one server fails.

---

### 3. Fault Tolerance

System continues working despite failures.

---

### 4. Elasticity

Automatically increase/decrease resources based on demand.

---

## Example AWS Architecture (Simple Web App)

```text id="aws_arch_01"
User → Load Balancer → EC2 → Database (RDS)
                      ↓
                     S3 (static files)
```

---

## Common AWS Use Cases

* Hosting websites
* Running backend APIs
* Data storage
* Machine learning models
* CI/CD pipelines

---

## AWS Pricing Basics

You pay for:

* Compute time
* Storage
* Data transfer
* Managed services

No upfront cost required.

---

## Common Beginner Mistakes

* Leaving EC2 running (costs money)
* Misconfigured IAM roles
* Public S3 buckets (security risk)
* Ignoring billing dashboard

---

## Best Practices

* Always use IAM roles instead of root user
* Enable billing alerts
* Use free tier wisely
* Stop unused EC2 instances
* Follow least privilege principle

---

## Summary

AWS is:

* A cloud infrastructure platform
* Scalable and flexible
* Pay-as-you-go based
* Built on global distributed systems

---

## What Next?

Next topic:

👉 **AWS-Global-Infrastructure.md** (Regions, AZs, edge locations in detail)

