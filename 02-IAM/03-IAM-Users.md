# IAM Users

## Learning Objectives

After completing this lesson, you will be able to:

- Understand what an IAM User is.
- Learn why IAM Users are created.
- Understand IAM User credentials.
- Create IAM Users securely.
- Follow AWS best practices for IAM Users.

---

# What is an IAM User?

An IAM User is an identity created within an AWS Account to represent a person or an application that needs access to AWS resources.

Each IAM User has its own credentials and permissions.

Think of an IAM User as an **employee ID card** inside your AWS account.

---

# Why Do We Need IAM Users?

Imagine a company with 50 employees.

Without IAM Users:

- Everyone uses the Root User.
- No accountability.
- High security risk.

With IAM Users:

- Each employee has their own login.
- Permissions can be controlled individually.
- AWS records who performed each action.

---

# Real-World Example

Company:

ABC Technologies

Employees:

- Alice (Developer)
- Bob (System Administrator)
- Charlie (Database Administrator)

AWS Account

```
AWS Account
      │
      ▼
 IAM Users
 ├── Alice
 ├── Bob
 └── Charlie
```

Each person has a separate login.

---

# IAM User Credentials

An IAM User can have two types of credentials.

## 1. Console Access

Used to log in to the AWS Management Console.

Credentials:

- Username
- Password

Example:

```
Username

alice

Password

********
```

---

## 2. Programmatic Access

Used by applications, scripts, AWS CLI, or SDKs.

Credentials:

- Access Key ID
- Secret Access Key

Example:

```
Access Key ID

AKIAxxxxxxxxxxxx

Secret Access Key

********************
```

> Never share or hard-code your access keys.

---

# IAM User Login

There are two ways to sign in.

### Root User

```
Email

+

Password
```

---

### IAM User

```
Account ID or Account Alias

+

IAM Username

+

Password
```

Example:

```
https://123456789012.signin.aws.amazon.com/console
```

or

```
https://mycompany.signin.aws.amazon.com/console
```

---

# Creating an IAM User

Steps:

1. Open IAM.
2. Choose **Users**.
3. Click **Create user**.
4. Enter a username.
5. Choose the type of access (console, programmatic, or both).
6. Assign permissions (directly or through a group).
7. Review and create.

---

# IAM User Permissions

IAM Users have **no permissions by default**.

Example:

```
New IAM User

↓

No Permissions
```

You must attach permissions using:

- IAM Policies
- IAM Groups
- IAM Roles (in some scenarios)

---

# Example Permissions

Developer:

- Start EC2
- Stop EC2
- Read S3

Database Administrator:

- Manage Amazon RDS

HR:

- No access to AWS infrastructure

---

# IAM User Lifecycle

```
Create User

↓

Assign Permissions

↓

User Works

↓

Update Permissions

↓

Disable or Delete User
```

---

# IAM User vs Root User

| Feature | Root User | IAM User |
|---------|-----------|----------|
| Number | One | Many |
| Created Automatically | Yes | No |
| Login | Email | Username |
| Permissions | Full Access | Only Assigned Permissions |
| Daily Use | No | Yes |
| MFA Supported | Yes | Yes |

---

# Best Practices

✅ Create one IAM User per person.

✅ Enable MFA.

✅ Use strong passwords.

✅ Assign permissions using Groups.

✅ Rotate access keys regularly.

✅ Remove unused users.

✅ Follow the Principle of Least Privilege.

---

# Common Mistakes

❌ Sharing one IAM User among multiple people.

✔ Each person should have their own IAM User.

---

❌ Giving AdministratorAccess to everyone.

✔ Grant only the permissions required.

---

❌ Storing Access Keys in source code.

✔ Use IAM Roles or secure secret management.

---

❌ Never deleting former employee accounts.

✔ Disable or delete unused IAM Users promptly.

---

# Real AWS Example

Company Structure

```
AWS Account
      │
      ▼
IAM Users

├── Admin
├── Developer1
├── Developer2
├── DBA
├── DevOps
└── Finance
```

Each user has different permissions based on their job role.

---

# Interview Questions

## What is an IAM User?

An IAM User is an identity in AWS that represents a person or application and has its own credentials and permissions.

---

## Does a new IAM User have permissions by default?

No.

A newly created IAM User has no permissions until they are granted.

---

## What are the two types of IAM User access?

- AWS Management Console (Username and Password)
- Programmatic Access (Access Key ID and Secret Access Key)

---

## Can multiple people share one IAM User?

No.

AWS recommends one IAM User per person for security and auditing.

---

## Should developers use the Root User?

No.

Developers should use IAM Users with only the permissions they require.

---

# Quick Revision

```
AWS Account
      │
      ▼
 IAM User
      │
Credentials
├── Console Access
└── Programmatic Access
      │
Permissions
      │
AWS Resources
```

---

# Key Takeaways

- IAM Users represent people or applications.
- Each IAM User has unique credentials.
- IAM Users start with no permissions.
- Grant permissions using Policies or Groups.
- Never use the Root User for daily work.
- Enable MFA for IAM Users whenever possible.
