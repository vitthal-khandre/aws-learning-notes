# Introduction to IAM

## Learning Objectives

After completing this lesson, you will be able to:

- Understand what IAM is.
- Know why IAM is important.
- Identify the main IAM components.
- Understand where IAM is used.

---

# What is IAM?

IAM stands for:

**Identity and Access Management**

IAM is the AWS service used to control **who can access AWS resources** and **what actions they are allowed to perform**.

Think of IAM as the **security guard** for your AWS account.

---

# Why is IAM Important?

Imagine a company with 100 employees.

Without IAM:

- Everyone logs in using the same account.
- Anyone can delete servers.
- Anyone can change billing information.
- There is no way to know who made changes.

This is insecure.

With IAM:

- Every employee has their own account.
- Each employee gets only the permissions they need.
- AWS records who performed each action.

---

# Real-Life Example

Imagine an office building.

Employees have different access:

- Receptionist → Reception only
- HR → HR Office
- IT Team → Server Room
- CEO → Entire Building

AWS IAM works in the same way.

Users receive permissions based on their job role.

---

# What Can IAM Control?

IAM controls access to AWS services such as:

- Amazon EC2
- Amazon S3
- Amazon RDS
- Amazon VPC
- AWS Lambda
- CloudWatch

Example:

```
Developer

↓

Can Create EC2

Can Read S3

Cannot Delete IAM Users
```

---

# Main IAM Components

IAM consists of four main components.

## 1. Users

Represents a person or application.

Example:

- Alice
- Bob
- Rahul

---

## 2. Groups

A collection of users.

Example:

Developers Group

```
Developers

├── Alice

├── Bob

└── Rahul
```

---

## 3. Roles

Temporary permissions that can be assumed by AWS services or users.

Example:

```
EC2 Instance

↓

IAM Role

↓

Access Amazon S3
```

---

## 4. Policies

Policies define permissions.

Example:

Allow:

- Read S3
- Launch EC2

Deny:

- Delete IAM Users

---

# How IAM Works

```
AWS Account

↓

IAM

├── Users
├── Groups
├── Roles
└── Policies

↓

AWS Resources
```

IAM decides who can access AWS resources and what actions they can perform.

---

# Example Scenario

A company has:

- 1 Administrator
- 5 Developers
- 2 Database Administrators

Permissions:

Administrator

- Full Access

Developers

- EC2
- S3

Database Team

- RDS Only

IAM ensures each team has only the permissions they need.

---

# Benefits of IAM

✅ Improved Security

✅ Individual User Accounts

✅ Fine-Grained Permissions

✅ Temporary Access with Roles

✅ Audit and Accountability

---

# Best Practices

- Never share accounts.
- Create an IAM User for every person.
- Enable MFA.
- Use IAM Groups for permission management.
- Follow the Principle of Least Privilege.

---

# Interview Questions

## What is IAM?

IAM (Identity and Access Management) is an AWS service used to securely manage users, permissions, and access to AWS resources.

---

## Why is IAM important?

IAM helps organizations control access, improve security, and ensure users have only the permissions they require.

---

## Name the four IAM components.

- Users
- Groups
- Roles
- Policies

---

# Quick Revision

IAM

↓

Identity and Access Management

↓

Controls

- Who can access AWS
- What they can do

↓

Uses

- Users
- Groups
- Roles
- Policies

---

# Key Takeaways

- IAM is the foundation of AWS security.
- IAM controls access to AWS resources.
- Users, Groups, Roles, and Policies are the four main IAM components.
- Following IAM best practices helps protect AWS accounts.
