# IAM Interview Questions

## Objective

This document contains the most common AWS IAM interview questions with simple answers for beginners and intermediate learners.

---

# Beginner Level

## 1. What is IAM?

**Answer:**

IAM (Identity and Access Management) is an AWS service used to securely manage users, groups, roles, and permissions for AWS resources.

---

## 2. Why is IAM important?

**Answer:**

IAM helps organizations:

- Control access to AWS resources.
- Improve security.
- Grant only required permissions.
- Track user activity.

---

## 3. Is IAM a Global or Regional service?

**Answer:**

IAM is a **Global Service**.

Users, Groups, Roles, and Policies are available across all AWS Regions in the account.

**Interview Tip:** Don't confuse IAM with regional services like EC2 or VPC.

---

## 4. What is an AWS Account?

**Answer:**

An AWS Account is the primary account that owns and manages AWS resources.

Every AWS Account has exactly one Root User.

---

## 5. What is the Root User?

**Answer:**

The Root User is created automatically when an AWS account is created.

It has unrestricted access to all AWS services and resources.

---

## 6. Should the Root User be used daily?

**Answer:**

No.

AWS recommends creating an IAM Administrator User and using that for daily administration.

---

## 7. What is an IAM User?

**Answer:**

An IAM User is an identity that represents a person or application.

Each IAM User has its own credentials and permissions.

---

## 8. What is an IAM Group?

**Answer:**

An IAM Group is a collection of IAM Users.

Permissions are assigned to the Group, and all members inherit those permissions.

---

## 9. Can one IAM User belong to multiple Groups?

**Answer:**

Yes.

A user can be a member of multiple IAM Groups.

---

## 10. Can an IAM Group contain another Group?

**Answer:**

No.

AWS IAM does not support nested Groups.

---

# Intermediate Level

## 11. What is an IAM Policy?

**Answer:**

An IAM Policy is a JSON document that defines what actions are allowed or denied on AWS resources.

---

## 12. What are the types of IAM Policies?

**Answer:**

- AWS Managed Policy
- Customer Managed Policy
- Inline Policy

---

## 13. What is the Principle of Least Privilege?

**Answer:**

Grant users only the permissions they need to perform their tasks.

---

## 14. What is the difference between an IAM User and an IAM Role?

| IAM User | IAM Role |
|----------|----------|
| Permanent identity | Temporary identity |
| Username & Password | No permanent credentials |
| Used mainly by people | Used by AWS services and temporary access |
| Can have Access Keys | Uses temporary credentials |

---

## 15. What is an IAM Role?

**Answer:**

An IAM Role is an AWS identity that provides temporary permissions to users or AWS services.

---

## 16. Why should EC2 use IAM Roles instead of Access Keys?

**Answer:**

IAM Roles provide temporary credentials managed by AWS, eliminating the need to store long-term access keys on the instance.

---

## 17. What is MFA?

**Answer:**

Multi-Factor Authentication (MFA) adds an additional verification step, such as a one-time code from an authenticator app, to improve account security.

---

## 18. Should MFA be enabled for the Root User?

**Answer:**

Yes.

AWS strongly recommends enabling MFA for the Root User immediately after creating the account.

---

## 19. What is Authentication?

**Answer:**

Authentication verifies the identity of a user or application.

Example:

Username + Password + MFA

---

## 20. What is Authorization?

**Answer:**

Authorization determines what actions an authenticated identity is allowed to perform.

IAM Policies are used for authorization.

---

# Advanced Level

## 21. Which takes priority: Allow or Explicit Deny?

**Answer:**

Explicit Deny always overrides Allow.

---

## 22. What happens when an IAM User has no policy attached?

**Answer:**

The user has no permissions to perform AWS actions, even though they can authenticate if they have valid credentials.

---

## 23. What is a Trust Policy?

**Answer:**

A Trust Policy defines who is allowed to assume an IAM Role.

---

## 24. What is the difference between a Trust Policy and a Permissions Policy?

| Trust Policy | Permissions Policy |
|--------------|--------------------|
| Who can assume the role | What the role can do |

---

## 25. Can an IAM Role have Access Keys?

**Answer:**

No.

IAM Roles use temporary security credentials provided by AWS.

---

## 26. Which AWS services commonly use IAM Roles?

**Answer:**

- Amazon EC2
- AWS Lambda
- Amazon ECS
- AWS CloudFormation
- AWS Backup

---

## 27. What is the default permission for a new IAM User?

**Answer:**

None.

A new IAM User has no permissions until policies are attached directly or through Groups.

---

## 28. Where should permissions normally be assigned?

**Answer:**

To IAM Groups rather than directly to individual users, whenever appropriate.

---

## 29. Why is sharing IAM Users a bad practice?

**Answer:**

Sharing accounts reduces accountability, weakens security, and makes auditing difficult.

Each person should have their own IAM User.

---

## 30. How can you improve IAM security?

**Answer:**

- Enable MFA
- Use IAM Roles
- Apply Least Privilege
- Review permissions regularly
- Remove unused users
- Rotate Access Keys
- Monitor activity using CloudTrail

---

# Scenario-Based Questions

## Q31

An EC2 instance needs access to an S3 bucket.

Should you store Access Keys on the server?

**Answer:**

No.

Attach an IAM Role with the required S3 permissions to the EC2 instance.

---

## Q32

A developer can log in but cannot launch EC2 instances.

What is the likely problem?

**Answer:**

The developer is authenticated successfully but lacks the required IAM permissions (authorization).

---

## Q33

A user belongs to two Groups.

One policy allows deleting S3 buckets.

Another policy explicitly denies deleting S3 buckets.

Can the user delete the bucket?

**Answer:**

No.

Explicit Deny overrides Allow.

---

## Q34

An employee leaves the company.

What should you do?

**Answer:**

Disable or delete the IAM User, remove unnecessary access, and review credentials and permissions.

---

## Q35

A Lambda function needs to access DynamoDB.

Should you create an IAM User for Lambda?

**Answer:**

No.

Create an IAM Role with the required DynamoDB permissions and assign it to the Lambda function.

---

# Rapid Fire Questions

| Question | Answer |
|----------|--------|
| IAM is Global or Regional? | Global |
| Root User Count | One |
| Default IAM User Permissions | None |
| Policy Format | JSON |
| Who can assume a Role? | Users, AWS Services, Applications (if trusted) |
| Does a Role have a Password? | No |
| Does a Group have Login Credentials? | No |
| Authentication means? | Verify Identity |
| Authorization means? | Verify Permissions |
| Explicit Deny wins? | Yes |
| MFA belongs to? | Authentication |
| Least Privilege? | Minimum Required Permissions |

---

# Interview Tips

### Always remember these facts:

- IAM is a Global service.
- Root User should not be used daily.
- New IAM Users have no permissions by default.
- Groups simplify permission management.
- Roles provide temporary credentials.
- Policies are written in JSON.
- Explicit Deny overrides Allow.
- Enable MFA for the Root User and privileged IAM Users.
- Use IAM Roles for AWS services like EC2 and Lambda.
- Follow the Principle of Least Privilege.

---

# Final Revision Diagram

```
AWS Account
      │
      ▼
Root User
      │
Create IAM Users
      │
Join Groups
      │
Groups have Policies
      │
Permissions
      │
AWS Resources
      │
───────────────
IAM Roles
      │
Temporary Credentials
      │
AWS Services
      │
───────────────
Authentication
      │
Who are you?
      │
───────────────
Authorization
      │
What can you do?
```

---

# Final Key Takeaways

- IAM secures access to AWS resources.
- Users represent people or applications.
- Groups simplify permission management.
- Policies define permissions.
- Roles provide temporary credentials.
- MFA strengthens authentication.
- Follow Least Privilege.
- Protect the Root User.
- Monitor IAM activity with CloudTrail.
