# IAM Hands-on Lab

## Lab Overview

In this lab, you will build a secure AWS IAM environment from scratch.

You will:

- Secure the Root User
- Create an Administrator User
- Create IAM Groups
- Create IAM Users
- Attach Policies
- Enable MFA
- Test Permissions
- Create an IAM Role
- Verify Least Privilege

This lab combines everything learned in the IAM section.

---

# Lab Architecture

```
                          AWS Account
                               │
                     Root User (MFA Enabled)
                               │
                 Create Administrator User
                               │
                      IAM Administrator
                               │
      ┌───────────────┬───────────────┬───────────────┐
      │               │               │
 Developers      NetworkAdmins       HR
      │               │               │
 AmazonEC2      Administrator      ReadOnly
 ReadOnly          Access            Access
      │               │               │
 ┌────┴────┐          │               │
 │         │          │               │
alice     bob      adminuser       priya
```

---

# Lab Prerequisites

Before starting, make sure you have:

- AWS Free Tier Account
- Root User credentials
- Authenticator App
  - Google Authenticator
  - Microsoft Authenticator
  - Authy

---

# Part 1 – Secure the Root User

## Step 1

Sign in as the Root User.

```
https://aws.amazon.com/
```

---

## Step 2

Open:

```
IAM → Dashboard
```

---

## Step 3

Enable MFA for the Root User.

Use:

- Authenticator App

---

## Verify

Root User now requires:

- Email
- Password
- MFA Code

---

# Part 2 – Create an IAM Administrator User

Go to:

```
IAM → Users → Create User
```

Create:

```
Username

adminuser
```

Enable:

```
AWS Management Console Access
```

Attach Policy:

```
AdministratorAccess
```

Sign out.

Log in using:

```
IAM User

adminuser
```

From now on, use **adminuser** for daily work.

---

# Part 3 – Create IAM Groups

Go to:

```
IAM → User Groups
```

Create these Groups:

```
Developers

NetworkAdmins

HR
```

---

# Part 4 – Attach Policies

Attach the following AWS Managed Policies.

| Group | Policy |
|---------|----------------------------|
| Developers | AmazonEC2ReadOnlyAccess |
| NetworkAdmins | AdministratorAccess *(Lab Only)* |
| HR | ReadOnlyAccess |

---

# Part 5 – Create IAM Users

Create these users.

```
alice

bob

priya
```

Enable Console Access.

---

# Part 6 – Assign Users to Groups

| User | Group |
|-------|-----------|
| alice | Developers |
| bob | NetworkAdmins |
| priya | HR |

---

# Part 7 – Test Permissions

## Test User: Alice

Login as:

```
alice
```

Expected:

✅ View EC2

❌ Launch EC2

❌ Delete EC2

---

## Test User: Priya

Expected:

✅ View AWS resources

❌ Create resources

---

## Test User: Bob

Expected:

✅ Administrator Access

---

# Part 8 – Enable MFA for Users

Enable MFA for:

- adminuser
- alice
- bob
- priya

Use:

Authenticator App

---

# Part 9 – Create an IAM Role

Go to:

```
IAM → Roles
```

Create:

```
EC2-S3-ReadOnly
```

Trusted Entity:

```
AWS Service

↓

EC2
```

Attach Policy:

```
AmazonS3ReadOnlyAccess
```

---

# Part 10 – Launch an EC2 Instance

Launch:

```
Amazon Linux
```

Attach:

```
EC2-S3-ReadOnly
```

---

# Part 11 – Test the Role

Connect to EC2.

Run:

```bash
aws sts get-caller-identity
```

Expected:

Temporary credentials are used.

Run:

```bash
aws s3 ls
```

Expected:

S3 buckets are listed.

No Access Keys required.

---

# Part 12 – Review IAM

Open:

```
IAM Dashboard
```

Verify:

- MFA Enabled
- Users
- Groups
- Roles
- Policies

Everything should be configured correctly.

---

# Challenge Exercise

Create a new group:

```
S3Admins
```

Attach:

```
AmazonS3FullAccess
```

Create:

```
john
```

Add john to:

```
S3Admins
```

Verify:

- Can create S3 buckets
- Cannot manage IAM Users

---

# Cleanup

Delete:

- Test Users
- Test Groups
- Test Role
- Test EC2 Instance

Keep:

- Root User
- adminuser

---

# Lab Summary

You successfully learned how to:

- Secure the Root User
- Enable MFA
- Create IAM Users
- Create Groups
- Attach Policies
- Create IAM Roles
- Test Permissions
- Follow Least Privilege

These are the same tasks performed by AWS administrators in real environments.

---

# Common Troubleshooting

## "Access Denied"

Possible causes:

- Wrong IAM Policy
- User not in the correct Group
- Explicit Deny in a Policy

---

## Cannot Assume Role

Check:

- Trust Policy
- Role attached to EC2
- Permissions Policy

---

## MFA Not Working

Verify:

- Device time is correct
- QR code was scanned correctly
- Enter consecutive MFA codes during setup

---

# Key Takeaways

- Never use the Root User for daily work.
- Always enable MFA.
- Assign permissions through Groups.
- Use IAM Roles for AWS services.
- Verify permissions before granting additional access.
