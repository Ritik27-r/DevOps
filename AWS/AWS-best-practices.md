# AWS Security Best Practices

## Why AWS Security Matters

In AWS, **security is your responsibility**, not just AWS’s.

One misconfiguration can lead to:

* Data leaks
* Unauthorized access
* High billing damage
* Full account compromise

---

## Shared Responsibility Model (Quick Recap)

```text id="sec_shared_01"
AWS → Secures infrastructure
You  → Secures data, access, configuration
```

---

## 1. IAM Security (Most Important)

### Use Least Privilege

Give only required permissions.

❌ Bad:

```text id="sec_iam_bad_01"
Full admin access to everyone
```

✅ Good:

```text id="sec_iam_good_01"
Only S3 read access for app user
```

---

### Enable MFA (Multi-Factor Authentication)

Protects accounts with:

* Password + OTP

---

### Avoid Root User

Root should only be used for:

* Account setup
* Billing

Never use for daily tasks.

---

### Use IAM Roles Instead of Keys

Roles are:

* Temporary
* Safer
* Automatically managed

---

## 2. Access Key Security

❌ Never:

* Hardcode keys in code
* Upload keys to GitHub

✅ Always:

* Rotate keys regularly
* Use environment variables or roles

---

## 3. S3 Security

### Keep Buckets Private by Default

❌ Dangerous:

* Public S3 buckets with sensitive data

---

### Enable Encryption

Use:

* SSE-S3
* SSE-KMS

---

### Enable Versioning

Protects against accidental deletion.

---

## 4. VPC Security

### Use Private Subnets for Sensitive Data

Example:

```text id="sec_vpc_01"
Database → Private Subnet (no internet access)
```

---

### Restrict Security Groups

❌ Bad:

```text id="sec_sg_bad_01"
0.0.0.0/0 on all ports
```

---

## 5. EC2 Security

### Use Key Pairs Securely

* Never share `.pem` files
* Restrict file permissions:

```bash id="sec_ec2_01"
chmod 400 key.pem
```

---

### Disable Unused Ports

Only open required ports:

* 22 (SSH)
* 80 (HTTP)
* 443 (HTTPS)

---

### Use IAM Roles for EC2

Avoid storing credentials on instance.

---

## 6. Network Security

### Security Groups (Instance Level)

* Allow only required traffic

### NACLs (Subnet Level)

* Extra layer of filtering

---

## 7. Monitoring & Logging

### Enable CloudTrail

Tracks:

* API calls
* User actions
* Security events

---

### Use CloudWatch Alarms

Alert on:

* High CPU usage
* Unauthorized access attempts

---

## 8. Encryption

### At Rest

* S3 encryption
* EBS encryption
* RDS encryption

### In Transit

* Use HTTPS (TLS)
* Encrypt API calls

---

## 9. Logging & Auditing

Use:

* CloudTrail (audit logs)
* CloudWatch Logs (system logs)

---

## 10. Network Security Best Practices

* Use private subnets for backend systems
* Use NAT Gateway for controlled internet access
* Use VPC endpoints for private AWS service access

---

## 11. Account-Level Security

* Enable billing alerts
* Enable MFA for root user
* Monitor unusual activity
* Use separate accounts for dev/prod

---

## 12. Security Automation

Use:

* AWS Config (compliance checks)
* GuardDuty (threat detection)
* Security Hub (central security view)

---

## 13. Common Security Mistakes

* Public S3 buckets
* Open security groups (0.0.0.0/0 everywhere)
* Hardcoded credentials
* No MFA enabled
* Ignoring logs and alerts

---

## 14. Real-World Secure Architecture

```text id="sec_arch_01"
User → CloudFront → ALB → EC2 (Private Subnet) → RDS (Encrypted)
                         ↓
                    CloudWatch + CloudTrail
```

---

## 15. Security Checklist

Before deploying:

* IAM roles configured
* MFA enabled
* S3 buckets private
* Security groups restricted
* Logs enabled
* Encryption enabled
* No root usage

---

## Summary

AWS security is built on:

* IAM control
* Network isolation (VPC)
* Encryption
* Monitoring
* Logging

Security is not optional—it is a **core design requirement**.

---

## What Next?

Next topic:

👉 **AWS-Interview-Notes.md** (important concepts, questions, and real interview scenarios)

