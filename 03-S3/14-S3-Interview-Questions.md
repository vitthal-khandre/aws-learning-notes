# Amazon S3 Interview Questions

## Introduction

This document contains frequently asked interview questions on Amazon S3.

Difficulty Levels:

🟢 Beginner

🟡 Intermediate

🔴 Scenario-Based

---

# 🟢 Beginner Questions

## 1. What is Amazon S3?

Amazon S3 (Simple Storage Service) is a highly durable, scalable, and secure object storage service provided by AWS.

It stores data as:

- Buckets
- Objects

---

## 2. What is a Bucket?

A bucket is a container used to store objects.

Example:

```
Bucket

company-backups
```

---

## 3. What is an Object?

An object is a file stored inside an S3 bucket.

Examples:

- photo.jpg
- report.pdf
- backup.zip

Each object consists of:

- Data
- Metadata
- Unique Key

---

## 4. What is an Object Key?

The Object Key is the unique name (path) of an object inside a bucket.

Example:

```
images/logo.png
```

---

## 5. What is the maximum size of an S3 object?

Maximum object size:

```
5 TB
```

Objects larger than 100 MB should generally use Multipart Upload for better performance and reliability.

---

## 6. Is Amazon S3 a file system?

No.

Amazon S3 is an Object Storage service, not a traditional file system.

---

## 7. Is S3 regional or global?

Buckets are created in a specific AWS Region.

Bucket names are globally unique.

---

## 8. What is S3 durability?

Amazon S3 is designed for:

```
99.999999999%

(11 Nines)
```

durability.

---

## 9. What is availability?

Availability measures how often a service is accessible.

Durability protects against data loss.

---

## 10. Name some S3 Storage Classes.

- Standard
- Intelligent-Tiering
- Standard-IA
- One Zone-IA
- Glacier Instant Retrieval
- Glacier Flexible Retrieval
- Glacier Deep Archive

---

# 🟡 Intermediate Questions

## 11. What is Versioning?

Versioning keeps multiple versions of an object to protect against accidental deletion or overwriting.

---

## 12. Why use Lifecycle Rules?

To automatically:

- Move objects to cheaper storage classes.
- Delete old objects.
- Manage noncurrent versions.

---

## 13. What is Server-Side Encryption?

AWS encrypts objects after they are uploaded.

Examples:

- SSE-S3
- SSE-KMS
- SSE-C

---

## 14. Difference between SSE-S3 and SSE-KMS?

| SSE-S3 | SSE-KMS |
|---------|---------|
| AWS manages keys | AWS KMS manages keys with customer control |
| Easy to configure | More control and auditing |
| Good default | Best for compliance and regulated workloads |

---

## 15. What is Bucket Versioning used for?

To recover previous object versions.

---

## 16. What is a Bucket Policy?

A resource-based JSON policy attached directly to a bucket.

---

## 17. Difference between IAM Policy and Bucket Policy?

| IAM Policy | Bucket Policy |
|------------|---------------|
| Identity-based | Resource-based |
| Attached to Users, Groups, Roles | Attached to Buckets |

---

## 18. What is Block Public Access?

A security feature that prevents buckets and objects from becoming publicly accessible through public policies or ACLs.

---

## 19. What is an ACL?

Access Control List.

A legacy permission mechanism for buckets and objects.

AWS recommends using IAM Policies and Bucket Policies instead.

---

## 20. What is Static Website Hosting?

A feature that allows Amazon S3 to host static websites containing HTML, CSS, JavaScript, and images.

---

## 21. Can S3 host dynamic websites?

No.

S3 only hosts static content.

---

## 22. What is Cross-Region Replication (CRR)?

CRR automatically copies objects to another bucket in a different AWS Region.

---

## 23. What is Same-Region Replication (SRR)?

SRR copies objects to another bucket in the same Region.

---

## 24. Is Versioning required for Replication?

Yes.

Versioning must be enabled on both source and destination buckets.

---

## 25. What is S3 Transfer Acceleration?

A feature that speeds up uploads and downloads by using AWS Edge Locations and the AWS Global Network.

---

## 26. What are S3 Event Notifications?

They trigger AWS services or send notifications when specific S3 events occur.

Destinations:

- AWS Lambda
- Amazon SNS
- Amazon SQS

---

# 🔴 Scenario-Based Questions

## 27. A company wants to reduce S3 storage costs without deleting data. What would you recommend?

Use Lifecycle Rules to transition older objects to cheaper storage classes such as Standard-IA or Glacier.

---

## 28. Users accidentally overwrite important files. How can you prevent data loss?

Enable Versioning.

---

## 29. A website consists only of HTML, CSS, JavaScript, and images. Which AWS service would you use?

Amazon S3 Static Website Hosting.

For production, use CloudFront in front of S3.

---

## 30. A company requires copies of data in another AWS Region for Disaster Recovery.

Use Cross-Region Replication (CRR).

---

## 31. A company has global users experiencing slow uploads.

Enable S3 Transfer Acceleration.

---

## 32. Images uploaded to S3 should automatically be resized.

Use:

S3 Event Notification

↓

AWS Lambda

---

## 33. Sensitive files must be encrypted and audited.

Use:

SSE-KMS

because it supports key management, IAM integration, and audit logging.

---

## 34. Developers should have read-only access to an S3 bucket.

Create an IAM Policy granting:

```
s3:GetObject
```

Attach it to the developers' IAM Group or Role.

---

## 35. Only users from the corporate office IP should access the bucket.

Use a Bucket Policy with an IP address condition.

---

## 36. Existing objects are not replicating to the destination bucket. Why?

Because S3 Replication copies only new objects by default.

Use S3 Batch Replication to replicate existing objects.

---

## 37. Someone accidentally made the bucket public.

How would you secure it?

- Enable Block Public Access.
- Review and update Bucket Policies.
- Remove unnecessary public permissions.
- Verify IAM permissions.

---

## 38. What happens if an IAM Policy allows access but a Bucket Policy explicitly denies it?

Explicit Deny overrides Allow.

---

## 39. What is the difference between durability and availability?

Durability:

Protection against data loss.

Availability:

How often the service is accessible.

---

## 40. What is Multipart Upload?

Multipart Upload divides a large object into smaller parts and uploads them in parallel.

Benefits:

- Faster uploads
- Better reliability
- Resume failed uploads

Recommended for large files.

---

# Rapid Fire Questions

| Question | Answer |
|----------|--------|
| S3 stands for? | Simple Storage Service |
| Storage type? | Object Storage |
| Max object size? | 5 TB |
| Storage classes? | 7+ |
| Versioning required for CRR? | Yes |
| Public website? | Static Website Hosting |
| Encryption? | SSE-S3, SSE-KMS, SSE-C |
| Lifecycle purpose? | Cost optimization |
| Replication types? | SRR, CRR |
| Event destinations? | Lambda, SNS, SQS |
| Transfer Acceleration uses? | Edge Locations |
| Bucket Policy type? | Resource-based |
| IAM Policy type? | Identity-based |
| Explicit Deny wins? | Yes |
| Block Public Access recommended? | Yes |

---

# Memory Tricks

### Storage Classes

```
S
I
IA
OZ
GI
GF
DA
```

- S → Standard
- I → Intelligent-Tiering
- IA → Standard-IA
- OZ → One Zone-IA
- GI → Glacier Instant Retrieval
- GF → Glacier Flexible Retrieval
- DA → Glacier Deep Archive

---

### Replication

```
SRR

↓

Same Region

CRR

↓

Cross Region
```

---

### Encryption

```
SSE-S3

↓

AWS manages keys

SSE-KMS

↓

AWS KMS manages keys

SSE-C

↓

Customer supplies keys
```

---

### Access Control

```
IAM

↓

Identity

Bucket Policy

↓

Bucket

ACL

↓

Legacy

Block Public Access

↓

Security
```

---

# Final Revision Checklist

✅ Buckets

✅ Objects

✅ Storage Classes

✅ Versioning

✅ Lifecycle Rules

✅ Encryption

✅ Bucket Policies

✅ Access Control

✅ Static Website Hosting

✅ Replication

✅ Transfer Acceleration

✅ Event Notifications

✅ Hands-on Lab

---

# Key Takeaways

- Amazon S3 is AWS's object storage service.
- Use Versioning for data protection.
- Use Lifecycle Rules for cost optimization.
- Use SSE-KMS for stronger security and auditing.
- Keep Block Public Access enabled unless public access is intentional.
- Use CRR for disaster recovery.
- Use Event Notifications for automation.
- Use Transfer Acceleration for faster long-distance uploads.
