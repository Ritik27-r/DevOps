# AWS Auto Scaling

## What is Auto Scaling?

AWS Auto Scaling automatically **adds or removes compute resources (usually EC2 instances)** based on demand.

It ensures your application always has the right amount of capacity.

---

## Why Auto Scaling is Important

Without Auto Scaling:

* Servers get overloaded during traffic spikes
* You overpay for unused resources
* Manual intervention is required

With Auto Scaling:

* Scales automatically up and down
* Saves cost
* Maintains performance

---

## Core Idea

```text id="asg_core_01"
Traffic ↑ → Add EC2 instances
Traffic ↓ → Remove EC2 instances
```

---

## Auto Scaling Components

### 1. Launch Template

Defines how EC2 instances are created:

* AMI
* Instance type
* Security groups
* Key pair

---

### 2. Auto Scaling Group (ASG)

A group of EC2 instances managed together.

It defines:

* Minimum capacity
* Maximum capacity
* Desired capacity

Example:

```text id="asg_group_01"
Min: 2
Desired: 3
Max: 10
```

---

### 3. Scaling Policies

Rules that decide when to scale.

---

## Types of Scaling

### 1. Dynamic Scaling

Responds to real-time metrics.

Example:

* CPU > 70% → add instance
* CPU < 30% → remove instance

---

### 2. Scheduled Scaling

Scales based on time.

Example:

* Increase capacity at 9 AM
* Reduce at 10 PM

---

### 3. Predictive Scaling

Uses machine learning to predict traffic patterns.

---

## Auto Scaling Flow

```text id="asg_flow_01"
User Traffic → Load Balancer → ASG → EC2 Instances
```

---

## CloudWatch Integration

Auto Scaling depends on CloudWatch metrics:

* CPU utilization
* Network traffic
* Request count

Example trigger:

```text id="asg_metric_01"
CPU > 70% for 5 minutes → scale out
```

---

## Health Checks

Auto Scaling constantly checks instance health.

If an instance fails:

* It is terminated
* A new one is launched automatically

---

## Minimum, Desired, Maximum Capacity

| Setting | Meaning                    |
| ------- | -------------------------- |
| Min     | Minimum running instances  |
| Desired | Target number of instances |
| Max     | Maximum allowed instances  |

---

## Scaling Out vs Scaling In

### Scaling Out

Add more instances

### Scaling In

Remove unnecessary instances

---

## Auto Scaling with Load Balancer

```text id="asg_elb_01"
User → ALB → Auto Scaling Group → EC2 Instances
```

Load balancer distributes traffic evenly.

---

## Instance Lifecycle in ASG

```text id="asg_lifecycle_01"
Pending → InService → Terminating → Terminated
```

---

## Cooldown Period

Prevents rapid scaling actions.

Example:

* Wait 5 minutes before next scaling action

---

## Termination Policy

Decides which instance gets removed:

* Oldest instance
* Least healthy instance
* Random selection

---

## Scaling Policies Types

### 1. Target Tracking

Keeps metric at a target value

Example:

* Maintain CPU at 50%

---

### 2. Step Scaling

Adds/removes instances in steps

Example:

* CPU 60% → add 1 instance
* CPU 80% → add 3 instances

---

### 3. Simple Scaling

One rule per condition

---

## Auto Scaling Example

### Web Application

```text id="asg_example_01"
Users → ALB → ASG (EC2 fleet) → Database (RDS)
```

---

## Multi-AZ Auto Scaling

Instances are distributed across AZs:

```text id="asg_az_01"
AZ-1 → EC2
AZ-2 → EC2
AZ-3 → EC2
```

---

## Benefits of Auto Scaling

* High availability
* Cost optimization
* Fault tolerance
* Automatic recovery
* Performance stability

---

## Common Mistakes

* Setting max capacity too low
* No proper CloudWatch alarms
* Ignoring health checks
* Not using multiple AZs
* Over-scaling leading to cost issues

---

## Best Practices

* Always use ALB with ASG
* Define realistic min/max limits
* Use target tracking policies
* Enable health checks
* Distribute across AZs

---

## Real-World Use Case

### E-commerce website

```text id="asg_real_01"
Flash sale → Traffic spike → ASG adds instances → Load balanced by ALB
```

---

## Summary

Auto Scaling provides:

* Automatic resource management
* Cost efficiency
* High availability
* Self-healing infrastructure

---

## What Next?

Next topic:

👉 **CloudWatch.md** (monitoring, logs, alerts, and AWS observability)

