# IAM Groups

## Learning Objectives

After completing this lesson, you will be able to:

- Understand what an IAM Group is.
- Learn why IAM Groups are used.
- Understand how Groups simplify permission management.
- Learn the relationship between Users, Groups, and Policies.
- Follow AWS best practices for IAM Groups.

---

# What is an IAM Group?

An IAM Group is a collection of IAM Users.

Instead of assigning permissions to each user individually, you assign permissions to the Group.

Every user in the Group automatically receives the Group's permissions.

Think of a Group as a **department** in a company.

---

# Why Do We Need IAM Groups?

Imagine a company with 100 developers.

Without Groups:

You must assign permissions to each developer one by one.

```
Developer1 → EC2 Permission

Developer2 → EC2 Permission

Developer3 → EC2 Permission

...

Developer100 → EC2 Permission
```

This takes time and is difficult to manage.

---

With Groups:

```
Developers Group

↓

EC2 + S3 Permissions

↓

Developer1

Developer2

Developer3

...

Developer100
```

Assign permissions once, and all members inherit them.

---

# Real-World Example

Company Departments

```
Company

├── Developers
├── Database Team
├── HR
├── Finance
└── Network Team
```

AWS IAM Groups

```
IAM Groups

├── Developers
├── DBA
├── HR
├── Finance
└── NetworkAdmins
```

Each department receives only the permissions required for its work.

---

# How IAM Groups Work

```
AWS Account
      │
      ▼
 IAM Groups
      │
Attach Policy
      │
Users Join Group
      │
Users Receive Permissions
```

---

# IAM Group Example

```
Developers Group

Policy:

AmazonEC2ReadOnlyAccess

Members

├── Alice
├── Bob
└── Rahul
```

All three users can view EC2 resources without assigning the policy individually.

---

# Can a User Belong to Multiple Groups?

Yes.

Example:

```
Alice

├── Developers Group
└── S3Admins Group
```

Alice receives permissions from both Groups.

---

# Can a Group Contain Another Group?

No.

IAM does **not** support nested Groups.

```
Developers

↓

Network Team

❌ Not Allowed
```

Groups can contain only IAM Users.

---

# IAM Users vs IAM Groups

| Feature | IAM User | IAM Group |
|---------|----------|-----------|
| Represents | Person or Application | Collection of Users |
| Has Credentials | Yes | No |
| Can Sign In | Yes | No |
| Can Have Policies | Yes | Yes |
| Used for Login | Yes | No |

---

# Group Permissions

Permissions are attached using IAM Policies.

Example:

```
Developers Group

↓

Policy

AmazonS3ReadOnlyAccess
```

Every member can read S3 buckets.

---

# Common AWS Managed Policies

| Policy | Purpose |
|---------|----------|
| AdministratorAccess | Full access to AWS |
| ReadOnlyAccess | Read-only access to AWS services |
| AmazonS3FullAccess | Full access to Amazon S3 |
| AmazonS3ReadOnlyAccess | Read-only access to Amazon S3 |
| AmazonEC2FullAccess | Full access to Amazon EC2 |
| AmazonEC2ReadOnlyAccess | Read-only access to Amazon EC2 |

---

# Best Practices

✅ Create Groups based on job roles.

✅ Assign permissions to Groups instead of individual users.

✅ Use the Principle of Least Privilege.

✅ Remove users from Groups when roles change.

✅ Review Group memberships regularly.

---

# Common Mistakes

❌ Giving every user AdministratorAccess.

✔ Create Groups with appropriate permissions.

---

❌ Creating a separate policy for every user.

✔ Attach policies to Groups whenever possible.

---

❌ Forgetting to remove employees from Groups after changing jobs.

✔ Update Group membership immediately.

---

# Real AWS Example

```
AWS Account

↓

IAM Groups

├── Developers
│      │
│      ├── Alice
│      ├── Bob
│      └── Rahul
│
├── NetworkAdmins
│      │
│      ├── John
│      └── Amit
│
└── HR
       │
       ├── Priya
       └── Sneha
```

Each Group has different permissions.

---

# Interview Questions

## What is an IAM Group?

An IAM Group is a collection of IAM Users that share the same permissions.

---

## Can an IAM Group have login credentials?

No.

Only IAM Users have login credentials.

---

## Can one IAM User belong to multiple Groups?

Yes.

A user can be a member of multiple Groups.

---

## Can an IAM Group contain another Group?

No.

Nested Groups are not supported in AWS IAM.

---

## Why are IAM Groups useful?

They simplify permission management by assigning permissions to multiple users at once.

---

# Quick Revision

```
IAM Groups

↓

Collection of Users

↓

Attach Policies

↓

Users Inherit Permissions
```

---

# Key Takeaways

- IAM Groups organize users with similar responsibilities.
- Groups simplify permission management.
- Users inherit permissions from their Groups.
- Users can belong to multiple Groups.
- Groups cannot contain other Groups.
- Groups do not have login credentials.
