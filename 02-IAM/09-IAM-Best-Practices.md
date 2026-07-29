# IAM Best Practices

## Learning Objectives

After completing this lesson, you will be able to:

- Understand AWS IAM security best practices.
- Learn how to protect AWS accounts.
- Apply the Principle of Least Privilege.
- Secure users, roles, and credentials.
- Follow AWS-recommended IAM guidelines.

---

# What are IAM Best Practices?

IAM Best Practices are AWS-recommended guidelines that help secure your AWS account and resources.

Following these practices reduces the risk of:

- Unauthorized access
- Accidental changes
- Data loss
- Security breaches

Think of them as **rules for keeping your AWS environment secure**.

---

# 1. Never Use the Root User for Daily Work

The Root User has unrestricted access to the entire AWS account.

Use it only for tasks that require account-level permissions, such as:

- Managing billing
- Closing the AWS account
- Changing the account email
- Certain account recovery tasks

For everything else:

- Create an IAM Administrator User.
- Sign in using the IAM User.

✅ Best Practice

```
Root User

↓

Create IAM Admin User

↓

Use IAM User Daily
```

---

# 2. Enable MFA

Always enable Multi-Factor Authentication (MFA).

Enable MFA for:

- Root User
- Administrator IAM Users
- All IAM Users (where practical)

```
Username

+

Password

+

MFA Code

↓

Secure Login
```

---

# 3. Follow the Principle of Least Privilege

Give users **only the permissions they need**.

Example:

Developer

Needs:

- Start EC2
- Stop EC2

Does NOT Need:

- Delete IAM Users
- Close AWS Account

Grant the minimum permissions required.

---

# 4. Create One IAM User Per Person

Never share AWS accounts.

Incorrect:

```
Developer Team

↓

Shared Login

❌
```

Correct:

```
Developer1

Developer2

Developer3

↓

Separate IAM Users
```

Benefits:

- Better auditing
- Individual accountability
- Easier permission management

---

# 5. Use IAM Groups

Instead of assigning permissions to each user individually:

```
Users

↓

Developers Group

↓

Policies

↓

Permissions
```

Benefits:

- Easier management
- Consistent permissions
- Faster onboarding

---

# 6. Use IAM Roles Instead of Access Keys

Avoid storing long-term access keys on:

- EC2
- Lambda
- ECS
- Applications

Instead:

```
EC2

↓

IAM Role

↓

Temporary Credentials
```

IAM Roles are more secure because credentials are temporary and managed by AWS.

---

# 7. Rotate Access Keys

If you must use Access Keys:

- Rotate them regularly.
- Delete unused keys.
- Monitor their usage.

Never keep old keys active longer than necessary.

---

# 8. Never Hard-Code Credentials

Bad Example:

```python
aws_access_key = "AKIAxxxxxxxxxxxx"
aws_secret_key = "xxxxxxxxxxxxxxxx"
```

Good Example:

Use:

- IAM Roles
- Environment variables (when appropriate)
- AWS Secrets Manager
- AWS Systems Manager Parameter Store

---

# 9. Review IAM Permissions Regularly

Review:

- Users
- Groups
- Roles
- Policies

Questions to ask:

- Does this user still need access?
- Is this policy too broad?
- Can permissions be reduced?

Regular reviews improve security.

---

# 10. Remove Unused Users

When an employee leaves:

```
Disable User

↓

Review Resources

↓

Delete User
```

Never leave unused accounts active.

---

# 11. Use Strong Password Policies

Require:

- Minimum password length
- Uppercase letters
- Lowercase letters
- Numbers
- Special characters

Encourage users to use unique passwords.

---

# 12. Monitor IAM Activity

Use:

- AWS CloudTrail
- Amazon CloudWatch
- AWS Config (where applicable)

These services help detect:

- Failed login attempts
- Permission changes
- API activity

---

# Real-World Example

Company:

ABC Technologies

```
AWS Account
      │
      ▼
Root User
      │
Enable MFA
      │
Create IAM Admin
      │
Create Groups
      │
Developers
HR
Finance
      │
Attach Policies
      │
Users Join Groups
      │
Secure Access
```

---

# Common Mistakes

❌ Using the Root User daily.

✔ Use an IAM Administrator User.

---

❌ Sharing IAM Users.

✔ One IAM User per person.

---

❌ Giving everyone AdministratorAccess.

✔ Apply Least Privilege.

---

❌ Storing Access Keys in code.

✔ Use IAM Roles or secure secret storage.

---

❌ Forgetting to remove inactive users.

✔ Disable or delete unused accounts promptly.

---

# Interview Questions

## Why should the Root User not be used daily?

Because it has unrestricted access and increases security risk.

---

## What is the Principle of Least Privilege?

Grant only the minimum permissions required to perform a task.

---

## Why are IAM Roles preferred over Access Keys?

IAM Roles provide temporary credentials and avoid storing long-term credentials.

---

## Why should each employee have their own IAM User?

For security, auditing, and accountability.

---

## Which AWS services help monitor IAM activity?

- AWS CloudTrail
- Amazon CloudWatch
- AWS Config

---

# Quick Revision

```
IAM Security

↓

Root User

↓

MFA

↓

IAM Users

↓

Groups

↓

Policies

↓

Roles

↓

Least Privilege

↓

Monitor Activity
```

---

# Key Takeaways

- Protect the Root User.
- Enable MFA.
- Use one IAM User per person.
- Assign permissions through Groups.
- Use IAM Roles instead of long-term Access Keys.
- Follow the Principle of Least Privilege.
- Rotate and remove unused credentials.
- Review IAM permissions regularly.
- Monitor account activity with CloudTrail and CloudWatch.
