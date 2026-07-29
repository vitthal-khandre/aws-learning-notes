# IAM Roles

## Learning Objectives

After completing this lesson, you will be able to:

- Understand what an IAM Role is.
- Learn why IAM Roles are used.
- Understand temporary credentials.
- Know the difference between Users and Roles.
- Learn common real-world use cases.
- Follow IAM Role best practices.

---

# What is an IAM Role?

An IAM Role is an AWS identity that provides **temporary permissions** to perform specific tasks.

Unlike an IAM User, an IAM Role does **not** have:

- Username
- Password
- Permanent Access Keys

Instead, AWS provides **temporary security credentials** when the role is assumed.

---

# Why Do We Need IAM Roles?

Imagine an EC2 server needs to read files from an S3 bucket.

Option 1 (Bad Practice)

```
Store AWS Access Keys
Inside EC2 Server

↓

Security Risk
```

If someone steals the server or its configuration, they may also obtain the access keys.

Option 2 (Best Practice)

```
EC2 Instance

↓

IAM Role

↓

Temporary Credentials

↓

Access Amazon S3
```

No permanent credentials are stored on the server.

---

# Real-Life Example

Imagine visiting a company office.

At reception, you receive a **temporary visitor badge**.

- Valid only for today.
- Gives access only to approved areas.
- Returned before leaving.

An IAM Role works the same way.

```
Visitor

↓

Temporary Badge

↓

Limited Access

↓

Badge Expires
```

---

# How IAM Roles Work

```
AWS Resource

↓

Assume Role

↓

Temporary Credentials

↓

Access AWS Services
```

---

# Who Can Assume a Role?

IAM Roles can be assumed by:

- IAM Users
- EC2 Instances
- Lambda Functions
- ECS Tasks
- AWS Services
- Applications
- Users from another AWS Account (if allowed)
- Federated users (for example, from an identity provider)

---

# Common IAM Role Use Cases

## 1. EC2 Accessing S3

```
EC2

↓

IAM Role

↓

Amazon S3
```

No Access Keys required.

---

## 2. Lambda Accessing DynamoDB

```
Lambda

↓

IAM Role

↓

Amazon DynamoDB
```

---

## 3. Cross-Account Access

Company A

↓

IAM Role

↓

Company B AWS Account
```

Allows controlled access between AWS accounts.

---

## 4. AWS Services

Many AWS services use IAM Roles automatically.

Examples:

- EC2
- Lambda
- ECS
- AWS Backup
- CloudFormation

---

# Temporary Credentials

IAM Roles use:

- Temporary Access Key ID
- Temporary Secret Access Key
- Session Token

AWS automatically rotates and expires these credentials.

This is more secure than long-lived credentials.

---

# IAM User vs IAM Role

| Feature | IAM User | IAM Role |
|----------|----------|----------|
| Username | Yes | No |
| Password | Yes | No |
| Permanent Access Keys | Yes | No |
| Temporary Credentials | No | Yes |
| Used by People | Yes | Sometimes |
| Used by AWS Services | Rarely | Yes |

---

# Trust Policy

Every IAM Role contains a **Trust Policy**.

The Trust Policy defines:

**Who is allowed to assume the role.**

Example:

```
EC2

↓

Allowed

↓

Assume Role
```

Without a trust relationship, the role cannot be assumed.

---

# Permissions Policy

An IAM Role also has one or more **Permissions Policies**.

These define:

**What actions the role is allowed to perform** after it has been assumed.

Example:

```
Role

↓

Read S3

Write CloudWatch Logs

Access DynamoDB
```

Think of it this way:

- **Trust Policy** → *Who can use the role?*
- **Permissions Policy** → *What can the role do?*

---

# Example Architecture

```
EC2 Instance

↓

IAM Role

↓

Amazon S3

↓

Read Files
```

No passwords.

No Access Keys.

Only temporary credentials.

---

# Best Practices

✅ Use IAM Roles instead of storing Access Keys.

✅ Grant only required permissions.

✅ Use Roles for EC2 and Lambda.

✅ Review Role permissions regularly.

✅ Follow the Principle of Least Privilege.

---

# Common Mistakes

❌ Saving Access Keys inside EC2 instances.

✔ Attach an IAM Role instead.

---

❌ Giving a Role AdministratorAccess unnecessarily.

✔ Grant only the permissions needed.

---

❌ Forgetting to review Role permissions.

✔ Audit Roles regularly.

---

# Real AWS Example

A photo-processing application:

```
Users

↓

Upload Image

↓

Amazon S3

↓

Lambda Function

↓

IAM Role

↓

Read Image

↓

Resize Image

↓

Save to S3
```

The Lambda function accesses S3 using its IAM Role—no permanent credentials are stored.

---

# Interview Questions

## What is an IAM Role?

An IAM Role is an AWS identity that provides temporary permissions to users or AWS services.

---

## Does an IAM Role have a username and password?

No.

IAM Roles do not have login credentials.

---

## Why are IAM Roles more secure than Access Keys?

Because they use temporary credentials that expire automatically.

---

## What is the difference between a Trust Policy and a Permissions Policy?

A Trust Policy defines **who can assume the role**.

A Permissions Policy defines **what actions the role can perform**.

---

## Name some AWS services that commonly use IAM Roles.

- Amazon EC2
- AWS Lambda
- Amazon ECS
- AWS CloudFormation

---

# Quick Revision

```
IAM Role

↓

Temporary Identity

↓

Temporary Credentials

↓

AWS Services

↓

AWS Resources
```

---

# Key Takeaways

- IAM Roles provide temporary permissions.
- Roles do not have usernames or passwords.
- AWS services commonly use IAM Roles.
- Roles improve security by avoiding long-lived credentials.
- Every Role has a Trust Policy and one or more Permissions Policies.
