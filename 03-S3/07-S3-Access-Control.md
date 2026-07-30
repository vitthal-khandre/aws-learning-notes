# Amazon S3 Access Control

## Learning Objectives

After completing this lesson, you will be able to:

- Understand how access to S3 is controlled.
- Learn IAM Policies, Bucket Policies, and ACLs.
- Understand Block Public Access.
- Learn Object Ownership.
- Understand Public vs Private buckets.
- Apply S3 security best practices.
- Answer common interview questions.

---

# Why is Access Control Important?

By default, Amazon S3 keeps your data private.

Access Control determines:

- Who can access a bucket?
- Who can access an object?
- What actions can they perform?
- Can anonymous users access the data?

Without proper access control:

- Sensitive data may become public.
- Unauthorized users may modify or delete files.
- Organizations may experience security incidents.

---

# S3 Access Control Methods

Amazon S3 provides four main ways to control access:

1. IAM Policies
2. Bucket Policies
3. Access Control Lists (ACLs)
4. Block Public Access

```
               Amazon S3
                    │
     ┌──────────────┼──────────────┐
     │              │              │
 IAM Policies  Bucket Policies    ACLs
                    │
          Block Public Access
```

---

# 1. IAM Policies

IAM Policies define what authenticated IAM Users, Groups, or Roles can do.

Example:

Developer

↓

IAM Policy

↓

Can Read Objects

↓

Cannot Delete Objects

Example Policy:

```json
{
  "Effect": "Allow",
  "Action": [
    "s3:GetObject"
  ],
  "Resource": "arn:aws:s3:::company-data/*"
}
```

Best For:

- Users inside your AWS account.
- EC2, Lambda, and other AWS services using IAM Roles.

---

# 2. Bucket Policies

A Bucket Policy is a resource-based JSON policy attached directly to an S3 bucket.

It defines who can access that bucket.

Example:

```
Bucket

company-data

↓

Bucket Policy

↓

Allow Read Access

↓

Specific IAM Role
```

Example Policy:

```json
{
  "Version":"2012-10-17",
  "Statement":[
    {
      "Effect":"Allow",
      "Principal":{
        "AWS":"arn:aws:iam::111122223333:role/EC2-S3-ReadOnly"
      },
      "Action":"s3:GetObject",
      "Resource":"arn:aws:s3:::company-data/*"
    }
  ]
}
```

Bucket Policies are commonly used for:

- Cross-account access
- Static website hosting
- Restricting access by IP address
- Allowing specific AWS services

---

# 3. Access Control Lists (ACLs)

ACLs are an older access control mechanism.

They can be applied to:

- Buckets
- Individual Objects

Permissions include:

- READ
- WRITE
- READ_ACP
- WRITE_ACP
- FULL_CONTROL

Today, AWS recommends using IAM Policies and Bucket Policies instead of ACLs whenever possible.

---

# 4. Block Public Access

Block Public Access is one of the most important S3 security features.

When enabled:

- Public Bucket Policies are blocked.
- Public ACLs are ignored or blocked.
- Anonymous internet users cannot access the bucket.

```
Internet

↓

Blocked

↓

Amazon S3 Bucket
```

AWS recommends keeping **Block Public Access enabled** unless public access is intentionally required.

---

# Object Ownership

Object Ownership determines who owns objects uploaded to a bucket.

Recommended setting:

```
Bucket owner enforced
```

Benefits:

- Bucket owner owns all uploaded objects.
- ACLs are disabled.
- Simpler permission management.

This is the AWS recommended configuration for most workloads.

---

# Public vs Private Bucket

## Private Bucket

```
Bucket

↓

IAM User

↓

Allowed

Internet

↓

Denied
```

Use for:

- Backups
- Company documents
- Financial records
- HR data

---

## Public Bucket

```
Internet

↓

Public Bucket

↓

Images

HTML

CSS

JavaScript
```

Use only for:

- Static website assets
- Public downloads
- Public documentation

Never store confidential data in a public bucket.

---

# How AWS Evaluates Permissions

When a request is made:

```
Request

↓

Authentication

↓

IAM Policy

↓

Bucket Policy

↓

ACL (if enabled)

↓

Block Public Access

↓

Allow or Deny
```

Important Rules:

- Explicit **Deny** overrides any **Allow**.
- If no policy allows the action, access is denied by default.

---

# Real-World Example

ABC Technologies

```
Private Bucket

employee-records

↓

IAM Role

↓

Read/Write

↓

Block Public Access

Enabled
```

Only authorized employees can access the data.

---

# Best Practices

✅ Keep buckets private by default.

✅ Enable Block Public Access.

✅ Prefer IAM Policies and Bucket Policies over ACLs.

✅ Use Bucket owner enforced Object Ownership.

✅ Follow the Principle of Least Privilege.

---

# Common Mistakes

❌ Making an entire bucket public.

✔ Share only the specific objects that must be public.

---

❌ Using ACLs for new designs.

✔ Use IAM Policies and Bucket Policies.

---

❌ Disabling Block Public Access unnecessarily.

✔ Leave it enabled unless there is a valid business need.

---

# Interview Questions

## What are the four main S3 access control mechanisms?

- IAM Policies
- Bucket Policies
- ACLs
- Block Public Access

---

## Which access control method is recommended for IAM Users?

IAM Policies.

---

## What is a Bucket Policy?

A resource-based JSON policy attached to an S3 bucket that controls access.

---

## Are ACLs recommended for new applications?

No.

AWS recommends IAM Policies, Bucket Policies, and Bucket owner enforced Object Ownership instead.

---

## What does Block Public Access do?

It prevents buckets and objects from becoming publicly accessible through public policies or ACLs.

---

## Which rule always wins?

Explicit Deny.

---

# Quick Revision

```
IAM Policies

↓

Bucket Policies

↓

ACLs

↓

Block Public Access

↓

Secure Bucket
```

---

# Key Takeaways

- S3 buckets are private by default.
- IAM Policies control access for IAM identities.
- Bucket Policies control access to buckets and objects.
- ACLs are legacy and generally avoided.
- Block Public Access should remain enabled unless public access is intentionally required.
- Explicit Deny always overrides Allow.
