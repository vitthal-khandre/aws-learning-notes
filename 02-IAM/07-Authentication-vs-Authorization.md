# Authentication vs Authorization

## Learning Objectives

After completing this lesson, you will be able to:

- Understand Authentication.
- Understand Authorization.
- Learn the differences between them.
- See how AWS IAM uses both.
- Answer common interview questions.

---

# What is Authentication?

Authentication is the process of **verifying your identity**.

It answers the question:

> **Who are you?**

Before AWS gives you access, it checks that you are really who you claim to be.

---

# Authentication Examples

You prove your identity using:

- Username and Password
- Multi-Factor Authentication (MFA)
- Access Key ID and Secret Access Key
- Temporary credentials (IAM Roles)

Example:

```
Login

↓

Username

+

Password

↓

AWS Verifies Identity

↓

Authenticated
```

---

# Real-Life Example

Imagine entering your office.

The security guard asks for your employee ID card.

If the ID card is valid:

✅ You are allowed to enter the building.

The guard has verified your identity.

This is **Authentication**.

---

# AWS Authentication

AWS supports several authentication methods.

## 1. Root User

Login using:

- Email
- Password

---

## 2. IAM User

Login using:

- Username
- Password

---

## 3. MFA

Adds an extra verification step.

```
Password

+

One-Time Code
```

---

## 4. Access Keys

Used by:

- AWS CLI
- SDKs
- Applications

Credentials:

- Access Key ID
- Secret Access Key

---

## 5. IAM Roles

AWS provides temporary credentials after a role is assumed.

---

# What is Authorization?

Authorization is the process of deciding **what an authenticated identity is allowed to do**.

It answers the question:

> **What are you allowed to do?**

Authorization happens **after Authentication**.

---

# Real-Life Example

After entering the office:

The security system checks your access card.

Can you enter:

- Server Room?
- HR Office?
- Finance Department?

Different employees have different permissions.

This is **Authorization**.

---

# AWS Authorization

AWS IAM uses:

- Policies
- Groups
- Roles

to determine permissions.

Example:

```
Developer

↓

Allowed

- Start EC2
- Stop EC2

Not Allowed

- Delete IAM Users
```

---

# How Authentication and Authorization Work Together

```
User

↓

Authentication

↓

Identity Verified

↓

Authorization

↓

Permissions Checked

↓

Access Granted or Denied
```

---

# Example Scenario

Alice signs in to AWS.

Step 1

Authentication

```
Username

alice

Password

********

↓

Verified
```

Step 2

Authorization

IAM checks Alice's policies.

Alice has:

- Read S3
- Start EC2

Alice does NOT have:

- Delete IAM Users

Result:

```
Allowed:

EC2
S3

Denied:

IAM Delete
```

---

# Authentication vs Authorization

| Authentication | Authorization |
|---------------|---------------|
| Verifies identity | Determines permissions |
| Happens first | Happens after authentication |
| Uses passwords, MFA, access keys | Uses IAM Policies |
| Answers "Who are you?" | Answers "What can you do?" |

---

# AWS Services Involved

Authentication

- Root User
- IAM User
- IAM Identity Center (AWS IAM Identity Center)
- MFA
- Access Keys
- IAM Roles (temporary credentials)

Authorization

- IAM Policies
- IAM Groups
- IAM Roles
- Resource-based Policies

---

# Best Practices

✅ Enable MFA.

✅ Use IAM Users instead of the Root User.

✅ Follow the Principle of Least Privilege.

✅ Review permissions regularly.

✅ Avoid sharing credentials.

---

# Common Mistakes

❌ Thinking login means full access.

✔ Login only proves identity.

Permissions are checked separately.

---

❌ Giving AdministratorAccess to everyone.

✔ Grant only required permissions.

---

❌ Confusing Authentication with Authorization.

✔ Authentication = Identity

✔ Authorization = Permissions

---

# Real AWS Example

Company

```
AWS Account

↓

IAM User

↓

Authentication

↓

IAM Policy

↓

Authorization

↓

Access EC2
```

Without a policy, the user can log in but cannot perform AWS actions.

---

# Interview Questions

## What is Authentication?

Authentication verifies the identity of a user or application.

---

## What is Authorization?

Authorization determines what actions an authenticated identity is allowed to perform.

---

## Which happens first?

Authentication.

---

## Which AWS service manages Authentication and Authorization?

AWS Identity and Access Management (IAM).

---

## What is the difference between Authentication and Authorization?

Authentication verifies identity.

Authorization grants or denies permissions.

---

# Quick Revision

```
Authentication

↓

Who are you?

↓

Authorization

↓

What can you do?
```

---

# Key Takeaways

- Authentication verifies identity.
- Authorization determines permissions.
- Authentication always happens before Authorization.
- IAM uses policies to authorize actions.
- MFA strengthens Authentication.
