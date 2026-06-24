# AWS Elastic Load Balancing (ELB)

## What is ELB?

Elastic Load Balancing is a service that **distributes incoming traffic across multiple targets** like EC2 instances, containers, or IP addresses.

It ensures:

* High availability
* Fault tolerance
* Better performance

---

## Why Load Balancing is Needed

Without a load balancer:

* One server gets overloaded
* Single point of failure
* Poor user experience

With ELB:

* Traffic is distributed evenly
* Failed servers are automatically removed

---

## How ELB Works

```text id="elb_flow_01"
User → Load Balancer → Multiple EC2 Instances
```

---

## Types of Load Balancers

### 1. Application Load Balancer (ALB)

Works at **Layer 7 (HTTP/HTTPS)**

Used for:

* Web applications
* APIs
* Microservices

Supports:

* Path-based routing
* Host-based routing

Example:

```text id="alb_01"
/api → Backend service
/web → Frontend service
```

---

### 2. Network Load Balancer (NLB)

Works at **Layer 4 (TCP/UDP)**

Used for:

* High performance apps
* Real-time traffic
* Low latency systems

---

### 3. Gateway Load Balancer (GWLB)

Used for:

* Security appliances
* Firewalls
* Network inspection tools

---

## ALB vs NLB

| Feature         | ALB           | NLB                   |
| --------------- | ------------- | --------------------- |
| Layer           | 7 (HTTP)      | 4 (TCP)               |
| Routing         | Smart routing | Fast routing          |
| Use case        | Web apps      | High performance apps |
| SSL termination | Yes           | Limited               |

---

## Target Groups

A target group is a set of resources ELB routes traffic to.

Example:

```text id="tg_01"
Target Group → EC2 Instances
```

---

## Health Checks

Load balancer continuously checks instance health.

If unhealthy:

* Instance is removed automatically

Example:

```text id="hc_01"
GET /health → 200 OK = healthy
```

---

## Load Balancing Algorithms

### 1. Round Robin

Requests distributed evenly.

---

### 2. Least Connections

Sends traffic to least busy server.

---

### 3. Weighted Routing

Based on assigned weight.

---

## ELB Architecture Example

```text id="elb_arch_01"
User
 ↓
Application Load Balancer
 ↓
EC2 (AZ-1)   EC2 (AZ-2)
 ↓
Database (RDS Multi-AZ)
```

---

## Cross-Zone Load Balancing

Distributes traffic across multiple Availability Zones evenly.

---

## Sticky Sessions

Also called session affinity:

* User always routed to same instance

Used when:

* Session data stored locally

---

## SSL/TLS Termination

ELB can handle HTTPS encryption:

```text id="ssl_01"
User HTTPS → Load Balancer → HTTP to backend
```

---

## Security Groups with ELB

* ALB has its own security group
* Must allow inbound traffic (80/443)
* Backend EC2 allows only ALB traffic

---

## ELB + Auto Scaling

Load balancer works with Auto Scaling:

```text id="asg_elb_01"
Traffic increases → Auto Scaling adds EC2 → ELB distributes traffic
```

---

## Monitoring ELB

Using CloudWatch:

* Request count
* Latency
* Error rates
* Healthy hosts

---

## Common ELB Mistakes

* Not configuring health checks
* Opening backend instances to public internet
* Wrong target group configuration
* Ignoring HTTPS setup
* Not enabling multi-AZ deployment

---

## Best Practices

* Always use ALB for web apps
* Enable health checks
* Deploy across multiple AZs
* Use HTTPS with SSL certificates
* Keep backend instances private

---

## Real-World Example

### Scalable Web App

```text id="elb_real_01"
User → Route 53 → ALB → EC2 (Auto Scaling Group) → RDS
```

---

## Summary

ELB provides:

* Traffic distribution
* High availability
* Fault tolerance
* Scalability
* Secure routing

---

## What Next?

Next topic:

👉 **Auto-Scaling.md** (automatic scaling of EC2 instances based on demand)

