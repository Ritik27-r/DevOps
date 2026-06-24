# AWS CloudWatch

## What is CloudWatch?

AWS CloudWatch is a **monitoring and observability service** used to track the performance, health, and logs of AWS resources and applications.

It helps you answer:

> “What is happening inside my AWS system right now?”

---

## Why CloudWatch is Important

* Monitors infrastructure in real time
* Detects system failures
* Triggers automatic actions
* Helps in debugging and performance tuning
* Essential for production systems

---

## Core Components of CloudWatch

### 1. Metrics

Metrics are **time-ordered data points**.

Examples:

* CPU utilization
* Disk usage
* Network traffic

---

## Example Metric Flow

```text id="cw_metric_01"
EC2 → CPU Usage → CloudWatch Metric → Dashboard
```

---

### 2. Logs

CloudWatch Logs store **application and system logs**.

Examples:

* Application logs
* System logs
* Lambda logs

---

### 3. Alarms

Alarms trigger actions when metrics cross a threshold.

Example:

```text id="cw_alarm_01"
CPU > 80% → Send alert / trigger Auto Scaling
```

---

### 4. Dashboards

Custom dashboards visualize metrics and logs.

Used for:

* System overview
* Real-time monitoring
* Business metrics tracking

---

## CloudWatch Architecture

```text id="cw_arch_01"
AWS Resources → Metrics/Logs → CloudWatch → Dashboard/Alarm → Action
```

---

## Metrics in Detail

Metrics are:

* Stored in time series
* Collected automatically for AWS services
* Can be custom-defined

Example:

* EC2 CPU usage every 5 minutes

---

## Logs in CloudWatch

CloudWatch Logs are organized into:

* Log groups
* Log streams

Example:

```text id="cw_logs_01"
/aws/ec2/app-logs
```

---

## CloudWatch Alarms

Alarms can:

* Send notifications (SNS)
* Trigger Auto Scaling
* Stop/terminate EC2 instances

---

## Alarm States

| State             | Meaning            |
| ----------------- | ------------------ |
| OK                | Everything normal  |
| ALARM             | Threshold breached |
| INSUFFICIENT_DATA | Not enough data    |

---

## CloudWatch Events (EventBridge)

Used for:

* Event-driven automation
* Triggering Lambda functions
* Scheduling tasks

Example:

```text id="cw_event_01"
EC2 stopped → Trigger Lambda → Send notification
```

---

## CloudWatch + EC2

Monitors:

* CPU utilization
* Disk I/O
* Network traffic

Example:

```text id="cw_ec2_01"
EC2 → CloudWatch Agent → Metrics → Alarm
```

---

## CloudWatch + Auto Scaling

```text id="cw_asg_01"
CPU > 70% → CloudWatch Alarm → Auto Scaling → Add EC2
```

---

## Custom Metrics

You can send your own metrics:

Example:

* Active users
* Orders per minute
* API latency

---

## CloudWatch Logs Insights

Used to query logs:

Example query:

```text id="cw_query_01"
fields @timestamp, @message
| sort @timestamp desc
```

---

## Log Retention

You can set retention policies:

* 1 day
* 7 days
* 30 days
* Indefinite

---

## CloudWatch Agent

Installed on EC2 to collect:

* Memory usage
* Disk usage
* Custom logs

---

## CloudWatch Use Cases

* System monitoring
* Application debugging
* Performance optimization
* Security auditing
* Infrastructure automation

---

## Real-World Example

### Web Application Monitoring

```text id="cw_real_01"
User → Application → EC2 → CloudWatch Logs + Metrics → Alarm → Auto Scaling
```

---

## Common Mistakes

* Not setting up alarms
* Ignoring log retention costs
* Not using CloudWatch Agent
* Overlooking custom metrics
* Poor dashboard design

---

## Best Practices

* Always set CPU and memory alarms
* Use dashboards for visibility
* Enable log retention policies
* Use custom metrics for business KPIs
* Integrate with SNS for alerts

---

## CloudWatch vs CloudTrail

| Feature | CloudWatch     | CloudTrail    |
| ------- | -------------- | ------------- |
| Purpose | Monitoring     | Auditing      |
| Focus   | Performance    | API activity  |
| Data    | Metrics & logs | Event history |

---

## Summary

CloudWatch provides:

* Real-time monitoring
* Log management
* Alerting system
* Infrastructure visibility

It is essential for **production-grade AWS systems**.

---

## What Next?

Next topic:

👉 **AWS-CLI.md** (command-line automation for AWS services)

