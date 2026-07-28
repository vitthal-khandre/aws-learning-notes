# AWS Shared Responsibility Model

## Learning Objectives

After completing this lesson, you will be able to:

- Understand the AWS Shared Responsibility Model.
- Know what AWS is responsible for.
- Know what the customer is responsible for.
- Understand how responsibilities change for IaaS, PaaS, and SaaS services.

---

# What is the Shared Responsibility Model?

AWS follows a **Shared Responsibility Model**, which means:

> **AWS and the customer share the responsibility for security.**

AWS secures the **cloud infrastructure**, while the customer secures **what they put in the cloud**.

---

# Easy Way to Remember

```
AWS = Security OF the Cloud

Customer = Security IN the Cloud
```

- **OF the Cloud** → AWS protects the infrastructure.
- **IN the Cloud** → You protect your data, users, and applications.

---

# Security OF the Cloud (AWS Responsibility)

AWS is responsible for protecting the infrastructure that runs AWS services.

AWS manages:

- Physical data centers
- Servers
- Storage hardware
- Networking equipment
- Power
- Cooling
- Physical security
- Hypervisor
- Global infrastructure

```
+-------------------------+
| Physical Security       | ← AWS
+-------------------------+
| Servers                 | ← AWS
+-------------------------+
| Networking              | ← AWS
+-------------------------+
| Storage Hardware        | ← AWS
+-------------------------+
| Power & Cooling         | ← AWS
+-------------------------+
```

You cannot access or manage these components.

---

# Security IN the Cloud (Customer Responsibility)

The customer is responsible for everything they create and configure inside AWS.

Examples:

- IAM Users
- Passwords
- MFA
- EC2 Operating System
- Installed Software
- Security Groups
- Data
- Encryption settings
- S3 Bucket permissions
- Application code

```
+-------------------------+
| IAM Users               | ← Customer
+-------------------------+
| Passwords               | ← Customer
+-------------------------+
| Applications            | ← Customer
+-------------------------+
| Data                    | ← Customer
+-------------------------+
| Security Groups         | ← Customer
+-------------------------+
```

---

# Real-Life Example

Imagine you rent an apartment.

The building owner is responsible for:

- Building maintenance
- Elevator
- Water supply
- Security guards

You are responsible for:

- Locking your door
- Your furniture
- Your valuables
- Cleaning your apartment

AWS works the same way.

AWS secures the building.

You secure your belongings.

---

# Example: Amazon EC2

Suppose you launch an EC2 instance.

AWS is responsible for:

- Physical server
- Storage hardware
- Network
- Hypervisor

You are responsible for:

- Operating System updates
- Firewall rules (Security Groups)
- Installed software
- User accounts
- Data backups
- Application security

---

# Example: Amazon S3

AWS is responsible for:

- S3 infrastructure
- Storage hardware
- Service availability

You are responsible for:

- Bucket permissions
- Object encryption
- Who can access your files
- Data classification

If you accidentally make an S3 bucket public, **AWS is not responsible**—it is a customer configuration.

---

# Responsibility by Service Model

## IaaS (Example: Amazon EC2)

Customer manages:

- Operating System
- Applications
- Data
- Security configuration

AWS manages:

- Hardware
- Network
- Virtualization

---

## PaaS (Example: AWS Elastic Beanstalk)

Customer manages:

- Application code
- Data

AWS manages:

- Operating System
- Runtime
- Infrastructure

---

## SaaS (Example: Amazon WorkDocs or Microsoft 365)

Customer manages:

- User accounts
- Passwords
- Data they create

Provider manages:

- Software
- Infrastructure
- Updates

---

# Responsibility Comparison

| Component | AWS | Customer |
|-----------|:---:|:--------:|
| Physical Data Centers | ✅ | ❌ |
| Servers | ✅ | ❌ |
| Networking | ✅ | ❌ |
| Storage Hardware | ✅ | ❌ |
| Hypervisor | ✅ | ❌ |
| Operating System (EC2) | ❌ | ✅ |
| Applications | ❌ | ✅ |
| IAM Users | ❌ | ✅ |
| Passwords | ❌ | ✅ |
| Security Groups | ❌ | ✅ |
| Data | ❌ | ✅ |
| S3 Bucket Permissions | ❌ | ✅ |

---

# Common Mistakes

### Mistake 1

❌ "AWS backs up my EC2 automatically."

✔ No. You should configure backups (for example, Amazon EBS snapshots or AWS Backup).

---

### Mistake 2

❌ "AWS secures my passwords."

✔ You must create strong passwords, enable MFA, and manage IAM users securely.

---

### Mistake 3

❌ "AWS prevents me from making an S3 bucket public."

✔ AWS provides tools and best practices, but you are responsible for your bucket configuration.

---

# Best Practices

✅ Enable Multi-Factor Authentication (MFA)

✅ Follow the principle of least privilege for IAM permissions

✅ Encrypt sensitive data

✅ Regularly back up important data

✅ Keep EC2 operating systems updated

✅ Monitor activity using AWS services such as CloudTrail and CloudWatch

---

# Interview Questions

## What is the AWS Shared Responsibility Model?

AWS and the customer share responsibility for security. AWS secures the cloud infrastructure, while the customer secures their data, applications, and configurations.

---

## What does AWS mean by "Security OF the Cloud"?

AWS is responsible for protecting the infrastructure that runs AWS services.

---

## What does "Security IN the Cloud" mean?

Customers are responsible for protecting their workloads, data, identities, and configurations.

---

## Who is responsible for IAM users?

The customer.

---

## Who is responsible for the physical data center?

AWS.

---

## Who is responsible for the operating system on an EC2 instance?

The customer.

---

# Quick Revision

```
AWS Responsibilities

✔ Data Centers
✔ Hardware
✔ Networking
✔ Storage
✔ Hypervisor

----------------------------

Customer Responsibilities

✔ IAM
✔ Passwords
✔ MFA
✔ Operating System
✔ Applications
✔ Data
✔ Security Groups
✔ S3 Permissions
```

---

# Key Takeaways

- AWS secures the **cloud infrastructure**.
- Customers secure **their resources and data**.
- Responsibility depends on the AWS service being used.
- More managed services (PaaS and SaaS) reduce the customer's operational responsibilities.
- Understanding the Shared Responsibility Model is essential for designing secure AWS solutions.
