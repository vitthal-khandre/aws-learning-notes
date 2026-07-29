# AWS Account and Root User

## Learning Objectives

After completing this lesson, you will be able to:

- Understand what an AWS Account is.
- Understand what the Root User is.
- Know the responsibilities of the Root User.
- Learn why the Root User should not be used daily.
- Secure your AWS account using AWS best practices.

---

# What is an AWS Account?

An AWS Account is your personal or organization's account that gives you access to AWS services.

Think of it as your **main AWS identity**.

When you create an AWS account, AWS automatically creates:

- One AWS Account
- One Root User
- One 12-digit AWS Account ID

Example:

```
AWS Account

Account ID

123456789012
```

Every AWS resource you create belongs to this account.

Examples:

- EC2 Instances
- S3 Buckets
- IAM Users
- VPCs
- RDS Databases

---

# Creating an AWS Account

To create an AWS account, you need:

- Email address
- Password
- Phone number
- Credit/Debit card
- Identity verification

Even if you only use the AWS Free Tier, AWS requires a payment method for account verification.

---

# What is the Root User?

The Root User is the **first user** created automatically when you sign up for AWS.

It has **unrestricted access** to every AWS service and resource in your account.

You log in using:

- Email address
- Password

```
AWS Account
      │
      ▼
 Root User
      │
 Full Access
```

There is only **one Root User** per AWS account.

---

# Root User Permissions

The Root User can:

- Create IAM Users
- Create IAM Roles
- Manage billing and payments
- Change account settings
- Delete AWS resources
- Close the AWS account
- Access every AWS service

No IAM User has these permissions unless they are explicitly granted.

---

# Root User vs IAM User

| Feature | Root User | IAM User |
|---------|-----------|----------|
| Created Automatically | ✅ Yes | ❌ No |
| Login | Email + Password | Username + Password |
| Full Access | ✅ Yes | Depends on Policy |
| Billing Access | ✅ Yes | Only if allowed |
| Delete AWS Account | ✅ Yes | Usually No |
| Daily Use | ❌ Not Recommended | ✅ Recommended |

---

# Why Shouldn't You Use the Root User Daily?

Imagine your house has one **master key**.

That master key opens:

- Main Door
- Bedroom
- Locker
- Garage

Would you give everyone the master key?

**No.**

Instead, each family member gets their own key.

AWS works the same way.

The Root User is the master key.

Create IAM Users for everyday work.

---

# Recommended AWS Account Setup

```
AWS Account
      │
      ▼
 Root User
      │
 Enable MFA
      │
 Create IAM Administrator User
      │
 Log out from Root User
      │
 Use IAM User Daily
```

This is the setup recommended by AWS.

---

# Secure the Root User

Immediately after creating your AWS account:

## Step 1

Enable Multi-Factor Authentication (MFA).

---

## Step 2

Create an Administrator IAM User.

---

## Step 3

Stop using the Root User for daily work.

---

## Step 4

Store the Root User credentials safely.

---

## Step 5

Use the Root User only for account-level tasks.

---

# Tasks That Require the Root User

Some actions are intended to be performed using the Root User or require special account-level permissions.

Examples include:

- Changing the account email address
- Closing the AWS account
- Changing payment methods
- Managing billing information
- Certain account recovery operations

For normal administration (creating EC2, S3, IAM users, etc.), use an IAM administrator user instead.

---

# Real-World Example

Suppose your company has:

- 1 AWS Account
- 20 Employees

Bad Practice:

```
20 Employees

↓

Use Root User

❌ Unsafe
```

Good Practice:

```
Root User

↓

Create IAM Users

↓

Developer
Tester
HR
Admin
Manager
```

Each person has their own login and only the permissions they need.

---

# Best Practices

✅ Enable MFA on the Root User.

✅ Never share the Root User password.

✅ Create an IAM Administrator User immediately.

✅ Use IAM Users for daily work.

✅ Keep Root credentials in a secure password manager.

✅ Enable billing alerts.

---

# Common Mistakes

❌ Using the Root User every day.

✔ Use an IAM User instead.

---

❌ Sharing the Root User password.

✔ Create separate IAM Users.

---

❌ Not enabling MFA.

✔ Always enable MFA.

---

❌ Saving the Root password in a text file.

✔ Use a secure password manager.

---

# Interview Questions

## What is an AWS Account?

An AWS Account is the primary account used to access and manage AWS resources.

---

## What is the Root User?

The Root User is the first identity created automatically with full access to all AWS services and resources.

---

## Should the Root User be used for daily work?

No.

Create an IAM Administrator User and use that for everyday administration.

---

## Why is the Root User important?

It has unrestricted access and is required for certain account-level management tasks.

---

## How many Root Users can an AWS account have?

Only one.

---

# Quick Revision

```
AWS Account

↓

Root User

↓

Enable MFA

↓

Create IAM Administrator User

↓

Use IAM User Daily
```

---

# Key Takeaways

- Every AWS account has one Root User.
- The Root User has unrestricted access.
- Use the Root User only for account-level tasks.
- Create an IAM Administrator User immediately after creating your account.
- Enable MFA to protect the Root User.
