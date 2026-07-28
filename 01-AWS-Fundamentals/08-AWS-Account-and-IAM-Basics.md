# AWS Account and IAM Basics

## Learning Objectives

After completing this lesson, you will be able to:

- Understand what an AWS Account is.
- Learn what IAM (Identity and Access Management) is.
- Know the difference between the Root User and IAM Users.
- Understand IAM Users, Groups, Roles, and Policies.
- Follow AWS security best practices.

---

# What is an AWS Account?

An AWS Account is your personal or organization's account used to access AWS services.

Think of it as the **main account** that owns all your AWS resources.

When you create an AWS account, AWS creates:

- One Root User
- One AWS Account ID (12-digit number)

Example:

```
AWS Account

Account ID

1234-5678-9012
```

Everything you create belongs to this AWS Account.

---

# What is the Root User?

The Root User is the first user created when you sign up for AWS.

It has **full access** to every AWS service and resource.

You log in using:

- Email address
- Password

```
AWS Account

↓

Root User

↓

Full Access
```

---

## Root User Permissions

The Root User can:

- Create IAM Users
- Delete the AWS Account
- Change billing information
- Access all AWS services
- Manage payment methods
- Close the AWS account

Because it has unlimited permissions, it should be used **only for account-level tasks**.

---

# Why Shouldn't You Use the Root User Daily?

Imagine the Root User is the **master key** to a building.

If someone steals that key, they can open every room.

Instead, create separate keys for each employee.

That's exactly what IAM does.

---

# What is IAM?

IAM stands for:

**Identity and Access Management**

IAM helps you securely control:

- Who can access AWS
- What they can do
- Which AWS resources they can use

IAM is a **free AWS service**.

---

# IAM Components

IAM consists of four main components:

1. Users
2. Groups
3. Roles
4. Policies

```
IAM

├── Users
├── Groups
├── Roles
└── Policies
```

---

# IAM User

An IAM User represents a person or application that needs access to AWS.

Examples:

- Administrator
- Developer
- System Administrator
- DevOps Engineer

Each IAM User has unique credentials.

```
Company

↓

IAM Users

- John
- Priya
- Rahul
```

---

# IAM Group

An IAM Group is a collection of IAM Users.

Instead of assigning permissions to each user individually, assign permissions to the group.

Example:

```
Developers Group

├── John
├── Priya
└── Rahul
```

All members inherit the group's permissions.

---

# IAM Role

An IAM Role provides temporary permissions.

Roles are commonly used by:

- EC2 instances
- Lambda functions
- AWS services
- Applications

Unlike IAM Users, roles do **not** have permanent passwords or access keys.

Example:

```
EC2 Instance

↓

IAM Role

↓

Access Amazon S3
```

---

# IAM Policy

A Policy is a JSON document that defines permissions.

Example:

```
Allow

↓

Amazon S3

↓

Read Only
```

Policies answer questions like:

- Can this user create an EC2 instance?
- Can this role read an S3 bucket?
- Can this group delete IAM users?

---

# IAM Authentication

IAM Users can sign in using:

- Username
- Password

For programmatic access:

- Access Key ID
- Secret Access Key

Never share access keys.

---

# Multi-Factor Authentication (MFA)

MFA adds an extra layer of security.

Instead of only:

```
Password
```

You also provide:

```
Password

+

One-Time Code
```

Even if someone knows your password, they cannot log in without the second factor.

---

# IAM Best Practices

✅ Use the Root User only when necessary.

✅ Enable MFA on the Root User.

✅ Create IAM Users for daily work.

✅ Assign permissions through IAM Groups.

✅ Use IAM Roles for AWS services.

✅ Follow the Principle of Least Privilege.

✅ Rotate access keys regularly.

---

# Root User vs IAM User

| Feature | Root User | IAM User |
|----------|-----------|----------|
| Created Automatically | Yes | No |
| Full Access | Yes | Depends on permissions |
| Daily Use | No | Yes |
| Can Delete AWS Account | Yes | No (unless explicitly allowed) |
| Recommended for Daily Work | ❌ No | ✅ Yes |

---

# Real-World Example

A company has:

- 1 IT Manager
- 5 Developers
- 2 Database Administrators

Instead of everyone using the Root User:

```
AWS Account

↓

Root User

↓

Create IAM Users

↓

Developers Group

↓

Developer Permissions
```

Each employee gets only the permissions needed for their job.

---

# Common Mistakes

❌ Using the Root User for daily work.

✔ Create IAM Users instead.

---

❌ Sharing one AWS account password.

✔ Give each person their own IAM User.

---

❌ Giving AdministratorAccess to everyone.

✔ Grant only the permissions required.

---

# Interview Questions

## What is an AWS Account?

An AWS Account is the main account that owns and manages AWS resources.

---

## What is IAM?

IAM (Identity and Access Management) is the AWS service used to manage users, groups, roles, and permissions.

---

## What is the difference between the Root User and an IAM User?

The Root User has unrestricted access to the AWS account and is created automatically.

An IAM User is created by the account administrator and has only the permissions that are granted.

---

## What is an IAM Role?

An IAM Role provides temporary permissions that can be assumed by AWS services, applications, or users.

---

## What is an IAM Policy?

An IAM Policy is a JSON document that defines what actions are allowed or denied.

---

# Quick Revision

```
AWS Account

↓

Root User

↓

Create IAM

↓

Users

↓

Groups

↓

Roles

↓

Policies
```

---

# Key Takeaways

- Every AWS account has one Root User.
- Use the Root User only for account-level tasks.
- IAM is used to securely control access to AWS resources.
- IAM includes Users, Groups, Roles, and Policies.
- Enable MFA and follow the Principle of Least Privilege.
