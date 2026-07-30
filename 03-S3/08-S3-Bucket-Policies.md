# Amazon S3 Bucket Policies

## Learning Objectives

After completing this lesson, you will be able to:

- Understand what a Bucket Policy is.
- Learn the structure of a Bucket Policy.
- Understand Version, Statement, Effect, Principal, Action, and Resource.
- Write simple Bucket Policies.
- Restrict access using IP addresses.
- Allow cross-account access.
- Answer common interview questions.

---

# What is a Bucket Policy?

A Bucket Policy is a **resource-based JSON policy** attached directly to an S3 bucket.

It defines **who** can access the bucket and **what** actions they are allowed (or denied) to perform.

```
User

↓

Bucket Policy

↓

Amazon S3 Bucket
```

---

# Why Do We Need Bucket Policies?

Bucket Policies help when you want to:

- Share data with another AWS account.
- Allow a specific IAM Role.
- Restrict access by IP address.
- Host a public static website.
- Allow AWS services (like CloudFront) to access the bucket.

---

# Bucket Policy Structure

Every Bucket Policy contains:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Principal": {},
      "Action": [],
      "Resource": ""
    }
  ]
}
```

---

# Understanding Each Field

## 1. Version

Specifies the policy language version.

```json
"Version": "2012-10-17"
```

Use this version for almost all AWS policies.

---

## 2. Statement

Contains one or more permission rules.

Example:

```json
"Statement": [
  {
    ...
  },
  {
    ...
  }
]
```

Each statement is evaluated independently.

---

## 3. Effect

Defines whether the rule allows or denies access.

Possible values:

```text
Allow

Deny
```

Example:

```json
"Effect": "Allow"
```

Remember:

> **Explicit Deny always overrides Allow.**

---

## 4. Principal

Specifies **who** the policy applies to.

Examples:

Everyone:

```json
"Principal": "*"
```

Specific AWS Account:

```json
"Principal": {
    "AWS":"arn:aws:iam::111122223333:root"
}
```

Specific IAM Role:

```json
"Principal": {
    "AWS":"arn:aws:iam::111122223333:role/AppRole"
}
```

---

## 5. Action

Specifies what operations are allowed or denied.

Examples:

```text
s3:GetObject
s3:PutObject
s3:DeleteObject
s3:ListBucket
```

Multiple actions:

```json
"Action":[
    "s3:GetObject",
    "s3:PutObject"
]
```

---

## 6. Resource

Specifies which bucket or objects the policy applies to.

Bucket only:

```text
arn:aws:s3:::company-data
```

Objects inside bucket:

```text
arn:aws:s3:::company-data/*
```

Notice:

- No `/*` → Bucket
- With `/*` → Objects inside the bucket

---

# Example 1: Read-Only Access

Allow anyone to read objects.

```json
{
  "Version":"2012-10-17",
  "Statement":[
    {
      "Effect":"Allow",
      "Principal":"*",
      "Action":"s3:GetObject",
      "Resource":"arn:aws:s3:::company-images/*"
    }
  ]
}
```

Use only for public content such as website images.

---

# Example 2: Allow a Specific IAM Role

```json
{
  "Version":"2012-10-17",
  "Statement":[
    {
      "Effect":"Allow",
      "Principal":{
        "AWS":"arn:aws:iam::111122223333:role/AppRole"
      },
      "Action":"s3:GetObject",
      "Resource":"arn:aws:s3:::company-data/*"
    }
  ]
}
```

Only the specified IAM Role can read objects.

---

# Example 3: Allow Cross-Account Access

Account A owns the bucket.

Account B needs access.

```json
"Principal": {
    "AWS":"arn:aws:iam::222233334444:root"
}
```

This grants permissions to the specified AWS account.

---

# Example 4: Restrict Access by IP Address

Allow access only from the corporate office.

```json
{
  "Version":"2012-10-17",
  "Statement":[
    {
      "Effect":"Allow",
      "Principal":"*",
      "Action":"s3:GetObject",
      "Resource":"arn:aws:s3:::company-data/*",
      "Condition":{
        "IpAddress":{
          "aws:SourceIp":"203.0.113.10/32"
        }
      }
    }
  ]
}
```

Useful for office-only access.

---

# Example 5: Deny Object Deletion

```json
{
  "Version":"2012-10-17",
  "Statement":[
    {
      "Effect":"Deny",
      "Principal":"*",
      "Action":"s3:DeleteObject",
      "Resource":"arn:aws:s3:::company-data/*"
    }
  ]
}
```

Nobody can delete objects unless another policy and conditions explicitly allow it without being overridden by this deny.

---

# Bucket Policy Evaluation

```
Request

↓

Authentication

↓

IAM Policy

↓

Bucket Policy

↓

Allow?

↓

Yes

↓

Access Granted
```

If any policy contains an **Explicit Deny**, access is denied.

---

# Real-World Example

ABC Technologies stores backups.

Requirements:

- Backup Server → Read & Write
- Employees → Read Only
- Internet → No Access

Solution:

- IAM Role for backup server
- Bucket Policy allowing that role
- Block Public Access enabled

```
Backup Server

↓

IAM Role

↓

Bucket Policy

↓

S3 Bucket

↓

Private
```

---

# Best Practices

✅ Follow the Principle of Least Privilege.

✅ Keep Block Public Access enabled unless public access is required.

✅ Use IAM Roles instead of root users.

✅ Use conditions (IP, VPC endpoint, MFA where applicable) to restrict access.

✅ Test policies in a non-production environment.

---

# Common Mistakes

❌ Setting:

```json
"Principal":"*"
```

without understanding the impact.

✔ Use only when intentional (for example, public website assets).

---

❌ Forgetting `/*` when granting object access.

✔ Use:

```text
arn:aws:s3:::bucket-name/*
```

for objects.

---

❌ Using the root account for applications.

✔ Use IAM Roles.

---

# Interview Questions

## What is a Bucket Policy?

A resource-based JSON policy attached to an S3 bucket that controls access.

---

## What are the main components of a Bucket Policy?

- Version
- Statement
- Effect
- Principal
- Action
- Resource

---

## What does Principal specify?

The AWS identity (or identities) the policy applies to.

---

## What is the difference between:

```
arn:aws:s3:::bucket
```

and

```
arn:aws:s3:::bucket/*
```

- First refers to the bucket.
- Second refers to objects inside the bucket.

---

## Which rule overrides all others?

Explicit Deny.

---

## Can Bucket Policies provide cross-account access?

Yes.

---

# Quick Revision

```
Bucket Policy

↓

Version

↓

Statement

↓

Effect

↓

Principal

↓

Action

↓

Resource
```

---

# Key Takeaways

- Bucket Policies are resource-based JSON policies.
- They control who can access a bucket and its objects.
- Principal specifies the user, role, account, or service.
- Action specifies allowed or denied operations.
- Resource specifies the bucket or object ARN.
- Explicit Deny always overrides Allow.
