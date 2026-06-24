# AWS VPC (Virtual Private Cloud)

## What is VPC?

A VPC is your **private isolated network inside AWS** where you can launch resources like EC2, databases, and load balancers.

Think of it as:

> Your own data center network inside AWS

---

## Why VPC is Important

* Full network isolation
* Secure architecture design
* Control over IP ranges
* Custom routing and firewall rules
* Foundation of all AWS networking

---

## VPC Core Components

### 1. Subnets

Subnets are **smaller networks inside a VPC**.

Types:

#### Public Subnet

* Has internet access
* Used for web servers

#### Private Subnet

* No direct internet access
* Used for databases and internal services

---

## Example Subnet Layout

```text id="vpc_subnet_01"
VPC (10.0.0.0/16)
 ├── Public Subnet (10.0.1.0/24)
 └── Private Subnet (10.0.2.0/24)
```

---

## 2. Internet Gateway (IGW)

Allows communication between:

* VPC ↔ Internet

Without IGW:

* No public internet access

---

## 3. Route Tables

Define how traffic flows inside VPC.

Example:

```text id="vpc_route_01"
Destination → Target
0.0.0.0/0 → Internet Gateway
10.0.0.0/16 → Local
```

---

## 4. Security Groups

Virtual firewall for **EC2 instances**.

* Stateful
* Controls inbound/outbound traffic

---

## 5. Network ACL (NACL)

Firewall at subnet level.

* Stateless
* Allows and denies rules

---

## Security Groups vs NACL

| Feature  | Security Group | NACL         |
| -------- | -------------- | ------------ |
| Level    | Instance       | Subnet       |
| Stateful | Yes            | No           |
| Rules    | Allow only     | Allow + Deny |

---

## 6. NAT Gateway

Allows **private subnet instances to access internet**.

Example:

* EC2 in private subnet downloads updates

But:

* Internet cannot directly access private subnet

---

## NAT Flow

```text id="vpc_nat_01"
Private EC2 → NAT Gateway → Internet
```

---

## 7. Elastic IP

A static public IP used for:

* NAT Gateway
* EC2 instances
* Fixed external access

---

## VPC Architecture Example

```text id="vpc_arch_01"
Internet
   ↓
Internet Gateway
   ↓
Public Subnet → Web Server (EC2)
   ↓
Private Subnet → Database (RDS)
```

---

## VPC CIDR Block

CIDR defines IP range:

Example:

```text id="vpc_cidr_01"
10.0.0.0/16
```

This gives:

* Large IP pool inside VPC

---

## VPC Peering

Connects two VPCs:

* Same or different regions
* Private communication
* No internet required

---

## VPC Flow

```text id="vpc_flow_01"
User → Internet Gateway → Public Subnet → Private Subnet
```

---

## VPC Endpoints

Allows private access to AWS services without internet.

Example:

* EC2 → S3 without IGW

---

## Types of VPC Endpoints

* Gateway Endpoint (S3, DynamoDB)
* Interface Endpoint (most AWS services)

---

## Real-World Architecture

```text id="vpc_real_01"
User → ALB → EC2 (Public Subnet)
                 ↓
              RDS (Private Subnet)
                 ↓
                S3
```

---

## Common VPC Mistakes

* Putting database in public subnet
* Misconfigured route tables
* Missing internet gateway
* Overly open security groups (0.0.0.0/0)
* Not using private subnets

---

## Best Practices

* Always use public + private subnet architecture
* Keep databases in private subnet
* Restrict inbound traffic strictly
* Use NAT Gateway for private subnet internet access
* Design CIDR carefully

---

## VPC Use Cases

* Secure web applications
* Enterprise networks
* Microservices architecture
* Multi-tier applications
* Hybrid cloud setups

---

## Summary

VPC provides:

* Private cloud network inside AWS
* Full control over routing and security
* Isolation and security for resources
* Foundation for all AWS architectures

---

## What Next?

Next topic:

👉 **Route53.md** (DNS service — domain routing, health checks, and traffic management)

