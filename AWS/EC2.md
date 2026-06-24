# AWS EC2 (Elastic Compute Cloud)

## What is EC2?

Amazon EC2 is a service that provides **virtual servers in the cloud**.

Instead of buying physical machines, you rent compute power on-demand.

---

## Why EC2 is Used

* Run applications on cloud servers
* Host websites and APIs
* Full control over OS and software
* Scalable compute capacity
* Pay only for usage

---

## EC2 Basics

An EC2 instance is a **virtual machine (VM)** running in AWS.

It includes:

* CPU
* RAM
* Storage
* Network interface

---

## EC2 Key Concepts

### 1. AMI (Amazon Machine Image)

An AMI is a **template for launching EC2 instances**.

It contains:

* Operating system (Linux/Windows)
* Preinstalled software
* Configuration

Example:

* Ubuntu AMI
* Amazon Linux AMI

---

### 2. Instance Types

Instance types define hardware configuration.

Format:

```text id="ec2_type_01"
t2.micro, t3.medium, m5.large
```

Categories:

* General purpose
* Compute optimized
* Memory optimized
* Storage optimized

---

### 3. Key Pair

Used for SSH login into EC2.

* Public key stored in AWS
* Private key downloaded by user

Example:

```bash id="ec2_ssh_01"
ssh -i key.pem ubuntu@public-ip
```

---

### 4. Security Groups

Act as a **virtual firewall** for EC2.

Controls:

* Inbound traffic
* Outbound traffic

Example rules:

* Allow SSH (port 22)
* Allow HTTP (port 80)

---

## EC2 Lifecycle

```text id="ec2_lifecycle_01"
Pending → Running → Stopped → Terminated
```

---

## Launching EC2 Instance

Steps:

1. Choose AMI
2. Select instance type
3. Configure network (VPC)
4. Add storage (EBS)
5. Configure security group
6. Launch instance

---

## Connecting to EC2

### Linux instance:

```bash id="ec2_connect_01"
ssh -i key.pem ubuntu@<public-ip>
```

---

## EC2 Storage (EBS)

Elastic Block Store (EBS) is:

* Persistent storage for EC2
* Survives instance restart

---

## EC2 vs Traditional Server

| Feature     | EC2               | Physical Server       |
| ----------- | ----------------- | --------------------- |
| Setup time  | Minutes           | Days                  |
| Scaling     | Easy              | Hard                  |
| Cost        | Pay-as-you-go     | Fixed cost            |
| Maintenance | AWS handles infra | You handle everything |

---

## EC2 Pricing Models

### 1. On-Demand

* Pay per hour/second
* No commitment

---

### 2. Reserved Instances

* Long-term commitment
* Cheaper pricing

---

### 3. Spot Instances

* Very cheap
* Can be terminated anytime

---

## EC2 Networking Basics

Each EC2 instance gets:

* Private IP
* Public IP (optional)
* DNS name

---

## Elastic IP

A static public IP that doesn’t change.

Use case:

* Hosting stable services
* Web servers

---

## Security Groups vs NACL

| Feature  | Security Group | NACL         |
| -------- | -------------- | ------------ |
| Level    | Instance       | Subnet       |
| Stateful | Yes            | No           |
| Rules    | Allow only     | Allow & deny |

---

## EC2 Monitoring

Using CloudWatch:

* CPU usage
* Memory (via agent)
* Disk usage
* Network traffic

---

## EC2 Auto Recovery

If instance fails:

* AWS can automatically restart it
* Or replace it in Auto Scaling group

---

## Common EC2 Commands

```bash id="ec2_cmd_01"
ssh -i key.pem ubuntu@ip
sudo apt update
sudo apt install nginx
```

---

## EC2 Use Cases

* Web hosting
* Application servers
* Backend APIs
* Dev/test environments
* CI/CD runners

---

## Common EC2 Mistakes

* Leaving instances running (cost issues)
* Opening all ports (0.0.0.0/0)
* Losing SSH key pair
* Not using security groups properly
* Ignoring backups

---

## Best Practices

* Use least privilege security groups
* Use IAM roles instead of credentials
* Stop unused instances
* Use Auto Scaling for production
* Monitor with CloudWatch

---

## EC2 Architecture Example

```text id="ec2_arch_01"
User → Load Balancer → EC2 (App Server) → Database (RDS)
```

---

## Summary

EC2 provides:

* Virtual servers in AWS
* Full OS control
* Flexible scaling
* Pay-as-you-use pricing

It is the **core compute service of AWS**.

---

## What Next?

Next topic:

👉 **S3.md** (object storage, buckets, and real-world cloud storage system)

