# IAM Policies

## Learning Objectives

After completing this lesson, you will be able to:

- Understand what an IAM Policy is.
- Learn how policies control permissions.
- Understand Allow and Deny.
- Learn the structure of a JSON policy.
- Differentiate between AWS Managed and Customer Managed Policies.
- Follow IAM policy best practices.

---

# What is an IAM Policy?

An IAM Policy is a JSON document that defines:

- What actions are allowed or denied.
- Which AWS resources are affected.
- Under what conditions the permissions apply.

Think of a policy as a **rulebook**.

Without a policy:

```
IAM User

↓

No Permissions
```

With a policy:

```
IAM User

↓

IAM Policy

↓

Can Access AWS Resources
```

---

# Why Do We Need Policies?

Imagine an office building.

Employees have ID cards.

The ID card determines:

- Which doors they can open.
- Which rooms they cannot enter.

AWS Policies work exactly the same way.

They decide:

- What a user can do.
- What a user cannot do.

---

# How Policies Work

```
IAM User
      │
      ▼
IAM Policy
      │
      ▼
AWS Resources
```

Policies can also be attached to:

- IAM Groups
- IAM Roles

---

# Types of IAM Policies

AWS supports three common types.

## 1. AWS Managed Policies

Created and maintained by AWS.

Examples:

- AdministratorAccess
- ReadOnlyAccess
- AmazonS3FullAccess
- AmazonEC2ReadOnlyAccess

Advantages:

- Ready to use
- Maintained by AWS
- Updated automatically

---

## 2. Customer Managed Policies

Created by you.

Example:

Allow:

- Read S3

Deny:

- Delete S3 Buckets

Advantages:

- Fully customizable
- Reusable across multiple users, groups, and roles

---

## 3. Inline Policies

A policy attached directly to a single user, group, or role.

Characteristics:

- Exists only on that identity.
- Not reusable.

AWS generally recommends Customer Managed Policies instead of Inline Policies when possible.

---

# Policy Structure

IAM Policies use JSON.

Example:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "s3:ListBucket",
      "Resource": "*"
    }
  ]
}
```

---

# Understanding Policy Elements

## Version

Specifies the policy language version.

```json
"Version": "2012-10-17"
```

---

## Statement

Contains one or more permission rules.

```json
"Statement": []
```

---

## Effect

Determines whether the action is allowed or denied.

Values:

- Allow
- Deny

Example:

```json
"Effect": "Allow"
```

---

## Action

Specifies the AWS API actions that are allowed or denied.

Example:

```json
"Action": "ec2:StartInstances"
```

Multiple actions:

```json
"Action": [
    "ec2:StartInstances",
    "ec2:StopInstances"
]
```

---

## Resource

Specifies which AWS resources the policy applies to.

Example:

```json
"Resource":"*"
```

Specific S3 bucket:

```json
"Resource":"arn:aws:s3:::company-backup"
```

---

# Allow vs Deny

Allow:

```
User

↓

Can Create EC2
```

Deny:

```
User

↓

Cannot Delete S3 Bucket
```

Important:

**An explicit Deny always overrides an Allow.**

---

# Example Policy

Allow listing S3 buckets.

```json
{
  "Version":"2012-10-17",
  "Statement":[
    {
      "Effect":"Allow",
      "Action":"s3:ListAllMyBuckets",
      "Resource":"*"
    }
  ]
}
```

---

# Policy Attachment

Policies can be attached to:

```
IAM User

↓

IAM Group

↓

IAM Role
```

The same Customer Managed Policy can be attached to multiple identities.

---

# AWS Managed Policy Examples

| Policy | Purpose |
|---------|----------|
| AdministratorAccess | Full access to AWS |
| ReadOnlyAccess | Read-only access |
| AmazonS3ReadOnlyAccess | Read-only S3 |
| AmazonS3FullAccess | Full S3 |
| AmazonEC2ReadOnlyAccess | Read-only EC2 |
| AmazonEC2FullAccess | Full EC2 |

---

# Principle of Least Privilege

Give users only the permissions they need.

Example:

Developer

Needs:

- Start EC2
- Stop EC2

Does NOT Need:

- Delete IAM Users
- Close AWS Account

Always avoid granting unnecessary permissions.

---

# Best Practices

✅ Prefer Groups over assigning policies directly to users.

✅ Use AWS Managed Policies when they meet your needs.

✅ Create Customer Managed Policies for custom permissions.

✅ Follow the Principle of Least Privilege.

✅ Review policies regularly.

✅ Remove unused permissions.

---

# Common Mistakes

❌ Giving AdministratorAccess to every user.

✔ Grant only the required permissions.

---

❌ Using Resource:"*" everywhere.

✔ Limit access to specific resources whenever possible.

---

❌ Ignoring Explicit Deny.

✔ Remember: Deny overrides Allow.

---

# Real AWS Example

Company:

ABC Technologies

Groups:

```
Developers

↓

Customer Managed Policy

↓

Allow:

EC2 Start

EC2 Stop

EC2 Describe
```

Developers cannot modify IAM or billing.

---

# Interview Questions

## What is an IAM Policy?

An IAM Policy is a JSON document that defines permissions for AWS resources.

---

## What language are IAM Policies written in?

JSON.

---

## What are the main policy types?

- AWS Managed Policies
- Customer Managed Policies
- Inline Policies

---

## What is the difference between Allow and Deny?

Allow grants permission.

Explicit Deny blocks permission and overrides Allow.

---

## What is the Principle of Least Privilege?

Grant only the permissions required to perform a task.

---

# Quick Revision

```
IAM Policy

↓

JSON Document

↓

Allow

or

Deny

↓

AWS Resources
```

---

# Key Takeaways

- IAM Policies define permissions.
- Policies are written in JSON.
- Policies can be attached to Users, Groups, and Roles.
- AWS provides Managed Policies, and you can create your own.
- Explicit Deny overrides Allow.
- Always follow the Principle of Least Privilege.
