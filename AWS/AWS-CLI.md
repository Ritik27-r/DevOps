# AWS CLI (Command Line Interface)

## What is AWS CLI?

AWS CLI is a **command-line tool** that lets you manage AWS services using terminal commands instead of the AWS Console.

It is widely used in:

* Automation
* DevOps pipelines
* Scripting
* CI/CD workflows

---

## Why AWS CLI is Important

* Faster than GUI (Console)
* Fully automatable
* Scriptable for DevOps
* Works in CI/CD pipelines
* Essential for real-world AWS jobs

---

## Installing AWS CLI

After installation, verify:

```bash id="aws_cli_01"
aws --version
```

---

## Configuring AWS CLI

```bash id="aws_config_01"
aws configure
```

You will enter:

* AWS Access Key ID
* AWS Secret Access Key
* Default region
* Output format (json/text/table)

---

## AWS CLI Authentication Flow

```text id="aws_auth_01"
CLI → Access Keys → IAM → AWS Services Access
```

---

## Basic AWS CLI Structure

```bash id="aws_basic_01"
aws <service> <operation> [parameters]
```

Example:

```bash id="aws_example_01"
aws s3 ls
```

---

## S3 Commands

### List buckets

```bash id="s3_list_01"
aws s3 ls
```

---

### Create bucket

```bash id="s3_create_01"
aws s3 mb s3://my-bucket
```

---

### Copy file to S3

```bash id="s3_cp_01"
aws s3 cp file.txt s3://my-bucket/
```

---

### Sync folders

```bash id="s3_sync_01"
aws s3 sync ./folder s3://my-bucket/
```

---

## EC2 Commands

### List instances

```bash id="ec2_list_01"
aws ec2 describe-instances
```

---

### Start instance

```bash id="ec2_start_01"
aws ec2 start-instances --instance-ids i-123456
```

---

### Stop instance

```bash id="ec2_stop_01"
aws ec2 stop-instances --instance-ids i-123456
```

---

## IAM Commands

### List users

```bash id="iam_list_01"
aws iam list-users
```

---

### List roles

```bash id="iam_roles_01"
aws iam list-roles
```

---

## VPC Commands

### List VPCs

```bash id="vpc_list_01"
aws ec2 describe-vpcs
```

---

### List subnets

```bash id="subnet_list_01"
aws ec2 describe-subnets
```

---

## CloudWatch Commands

### Get metrics

```bash id="cw_metrics_01"
aws cloudwatch list-metrics
```

---

### Describe alarms

```bash id="cw_alarms_01"
aws cloudwatch describe-alarms
```

---

## Output Formats

You can control output format:

```bash id="aws_output_01"
aws configure set output json
aws configure set output table
aws configure set output text
```

---

## AWS CLI Profiles

Used for multiple accounts:

```bash id="aws_profile_01"
aws configure --profile dev
```

Use profile:

```bash id="aws_profile_use_01"
aws s3 ls --profile dev
```

---

## AWS CLI with JSON

Most outputs are JSON:

Example:

```json id="aws_json_01"
{
  "Buckets": [
    {
      "Name": "my-bucket"
    }
  ]
}
```

---

## AWS CLI + Scripts

Example Bash automation:

```bash id="aws_script_01"
#!/bin/bash
aws s3 sync ./build s3://my-bucket/
```

---

## AWS CLI in DevOps

Used in:

* CI/CD pipelines (Jenkins, GitHub Actions)
* Infrastructure automation
* Deployment scripts
* Backup automation

---

## Real-World Example

### Deploy static website

```bash id="aws_deploy_01"
aws s3 sync ./website s3://my-site-bucket
```

---

## Common Mistakes

* Using root credentials in CLI
* Hardcoding access keys in scripts
* Wrong region configuration
* Forgetting IAM permissions
* Not using profiles for multiple accounts

---

## Best Practices

* Use IAM roles instead of access keys (when possible)
* Use named profiles
* Avoid storing credentials in code
* Enable MFA for IAM users
* Use CLI in automation pipelines

---

## Security Considerations

* Never expose access keys publicly
* Rotate keys regularly
* Use least privilege IAM policies
* Prefer role-based access

---

## AWS CLI vs Console

| Feature        | CLI    | Console |
| -------------- | ------ | ------- |
| Speed          | Fast   | Slower  |
| Automation     | Yes    | No      |
| Learning curve | Medium | Easy    |
| DevOps usage   | High   | Low     |

---

## Summary

AWS CLI allows:

* Full AWS control via terminal
* Automation and scripting
* DevOps pipeline integration
* Efficient cloud management

---

## What Next?

Next topic:

👉 **AWS-Security-Best-Practices.md** (real production security standards for AWS systems)

