# AWS IAM (Identity and Access Management)

## What is IAM?

AWS IAM is a service used to **control access to AWS resources securely**.

It defines:

* Who can access AWS (identity)
* What they can access (permissions)
* How they can access it (policies)

---

## Why IAM is Important

IAM is the **most critical AWS service** because:

* It controls security of your entire AWS account
* Misconfiguration can lead to data leaks or full compromise
* It enforces the “least privilege principle”

---

## IAM Core Components

### 1. Users

An IAM User represents a person or application.

Example:

* Developer
* Admin
* CI/CD tool

Each user has:

* Username
* Password (optional)
* Access keys (for CLI/API)

---

### 2. Groups

A group is a collection of users.

Example:

```text id="iam_group_01"
Developers Group → S3 + EC2 access
Admins Group → Full access
```

Groups simplify permission management.

---

### 3. Roles

Roles are temporary identities assigned to:

* AWS services (EC2, Lambda)
* External users
* Applications

Example:

* EC2 accessing S3 without storing credentials

---

### 4. Policies

Policies define **permissions in JSON format**.

Example:

```json id="iam_policy_01"
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "s3:*",
      "Resource": "*"
    }
  ]
}
```

---

## IAM Permission Structure

```text id="iam_perm_01"
Who (User/Role) → Policy → What (Resource Access)
```

---

## Types of Policies

### 1. AWS Managed Policies

Created and maintained by AWS.

### 2. Customer Managed Policies

Created by you.

### 3. Inline Policies

Directly attached to a user or role.

---

## Authentication vs Authorization

| Concept        | Meaning         |
| -------------- | --------------- |
| Authentication | Who you are     |
| Authorization  | What you can do |

---

## IAM Best Practices

### 1. Never use root user

Root user should only be used for:

* Account setup
* Billing configuration

---

### 2. Enable MFA (Multi-Factor Authentication)

Adds extra security layer:

* Password + OTP

---

### 3. Follow Least Privilege

Give only required permissions:

❌ Bad:

```text id="iam_bad_01"
S3 full access to everyone
```

✅ Good:

```text id="iam_good_01"
Only required bucket access
```

---

### 4. Use IAM Roles instead of Access Keys

Roles are:

* Safer
* Temporary
* Automatically rotated

---

### 5. Rotate Access Keys

Avoid long-term static credentials.

---

## IAM Access Keys

Used for CLI and SDK access:

```text id="iam_keys_01"
Access Key ID + Secret Access Key
```

Used in:

* AWS CLI
* Applications
* Automation scripts

---

## IAM with AWS CLI Example

```bash id="iam_cli_01"
aws configure
```

You enter:

* Access Key
* Secret Key
* Region
* Output format

---

## IAM Role Example (EC2)

Instead of storing credentials:

```text id="iam_role_01"
EC2 → IAM Role → S3 Access
```

No manual keys required.

---

## IAM Policy Structure Breakdown

```json id="iam_policy_02"
{
  "Effect": "Allow",
  "Action": "ec2:DescribeInstances",
  "Resource": "*"
}
```

### Meaning:

* Effect → Allow or Deny
* Action → What operation
* Resource → What resource

---

## Common IAM Mistakes

* Using root account for daily work
* Giving full admin access unnecessarily
* Not enabling MFA
* Hardcoding access keys in code
* Ignoring role-based access

---

## Security Risks in IAM

* Leaked access keys
* Over-permissive policies
* Publicly exposed credentials
* Missing MFA protection

---

## IAM Workflow Example

```text id="iam_flow_01"
User → Login → IAM Authentication → Policy Check → Access Granted/Denied
```

---

## Real-World Use Case

### EC2 accessing S3 safely

```text id="iam_real_01"
EC2 Instance
   ↓
IAM Role attached
   ↓
S3 bucket access granted
```

No credentials stored inside server.

---

## IAM Policy Evaluation Logic

AWS evaluates permissions like this:

1. Explicit Deny → Always wins
2. Allow → If no deny exists
3. Default → Deny everything

---

## IAM Summary

IAM provides:

* Secure identity management
* Fine-grained access control
* Role-based security model
* Central security system for AWS

---

## What Next?

Next topic:

👉 **EC2.md** (core AWS compute service — virtual servers in the cloud)

