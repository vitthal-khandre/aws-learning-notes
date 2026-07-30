# Amazon S3 Replication

## Learning Objectives

After completing this lesson, you will be able to:

- Understand Amazon S3 Replication.
- Learn the difference between CRR and SRR.
- Understand replication requirements.
- Learn what is and isn't replicated.
- Understand real-world disaster recovery scenarios.
- Answer common interview questions.

---

# What is S3 Replication?

Amazon S3 Replication automatically copies objects from one S3 bucket to another.

Whenever a new object is uploaded, AWS copies it to the destination bucket according to the replication rule.

```
Source Bucket

↓

Replication Rule

↓

Destination Bucket
```

---

# Why Do We Need Replication?

Replication is commonly used for:

- Disaster Recovery (DR)
- Backup
- High Availability
- Compliance
- Low-latency access for users in different regions

Example:

```
Mumbai Region

↓

Source Bucket

↓

Automatically Replicated

↓

Singapore Region

↓

Backup Bucket
```

If the primary Region becomes unavailable, a copy of the data already exists in another Region.

---

# Types of Replication

Amazon S3 supports:

- Same-Region Replication (SRR)
- Cross-Region Replication (CRR)

---

# 1. Same-Region Replication (SRR)

SRR copies objects to another bucket in the **same AWS Region**.

Example:

```
Region

ap-south-1 (Mumbai)

↓

Bucket A

↓

Replication

↓

Bucket B
```

### Common Use Cases

- Development → Testing
- Production → Analytics
- Log aggregation
- Separate backup bucket in the same Region

---

# 2. Cross-Region Replication (CRR)

CRR copies objects to a bucket in a **different AWS Region**.

Example:

```
Mumbai

↓

Source Bucket

↓

Replication

↓

Singapore

↓

Destination Bucket
```

### Common Use Cases

- Disaster Recovery
- Regulatory compliance
- Global applications
- Lower latency for users in another Region

---

# Replication Requirements

Before replication works:

### 1. Versioning

Versioning must be enabled on:

- Source bucket
- Destination bucket

Without Versioning, replication cannot be configured.

---

### 2. Destination Bucket

The destination bucket must already exist.

AWS does not create it automatically.

---

### 3. IAM Role

AWS creates or uses an IAM Role that grants S3 permission to replicate objects.

---

### 4. Replication Rule

You define:

- Source bucket
- Destination bucket
- Scope (all objects or selected prefixes/tags)

---

# How Replication Works

```
Upload photo.jpg

↓

Source Bucket

↓

Replication Rule

↓

Destination Bucket

↓

photo.jpg
```

Replication happens automatically after upload.

---

# What Gets Replicated?

By default:

✅ New objects uploaded after replication is enabled.

Optional settings can also replicate:

- Delete markers
- Object tags
- Object metadata
- Object ACLs (if ACLs are used)
- Encrypted objects (with proper configuration)

---

# What Does NOT Get Replicated Automatically?

- Existing objects already in the bucket before replication is enabled.
- Objects that fail replication due to missing permissions or configuration.

If you want to copy existing objects, you can use **S3 Batch Replication**.

---

# Delete Marker Replication

When Versioning is enabled:

Deleting an object usually creates a **Delete Marker**.

You can choose whether Delete Markers should also be replicated.

```
Delete Object

↓

Delete Marker

↓

Replicate?

↓

Yes or No
```

---

# Replication Time

Replication is generally asynchronous.

```
Upload

↓

Source Bucket

↓

Replication

↓

Destination Bucket
```

The copy usually appears within a short time, but it is not guaranteed to be instantaneous.

AWS also offers **S3 Replication Time Control (RTC)** for workloads requiring predictable replication times.

---

# Replication Flow

```
User Uploads File

↓

Source Bucket

↓

Versioning Enabled

↓

Replication Rule

↓

Destination Bucket

↓

Object Copied
```

---

# Real-World Example

ABC Technologies

Primary Office:

Mumbai

Backup Site:

Singapore

```
Employee Data

↓

Mumbai Bucket

↓

CRR

↓

Singapore Bucket
```

Benefits:

- Disaster Recovery
- Geographic redundancy
- Business continuity

---

# SRR vs CRR

| Feature | SRR | CRR |
|---------|-----|-----|
| Region | Same | Different |
| Disaster Recovery | Limited | Excellent |
| Compliance | Sometimes | Excellent |
| Latency Optimization | No | Yes |
| Backup in another Region | No | Yes |

---

# Best Practices

✅ Enable Versioning before configuring replication.

✅ Use CRR for Disaster Recovery.

✅ Use SRR for internal workflows within the same Region.

✅ Encrypt replicated data if storing sensitive information.

✅ Monitor replication status.

---

# Common Mistakes

❌ Forgetting to enable Versioning.

✔ Versioning is mandatory.

---

❌ Assuming old objects are replicated automatically.

✔ Only new objects are replicated by default.

---

❌ Thinking replication is instant.

✔ Replication is asynchronous.

---

# Interview Questions

## What is Amazon S3 Replication?

A feature that automatically copies objects from one S3 bucket to another.

---

## What are the two types of replication?

- Same-Region Replication (SRR)
- Cross-Region Replication (CRR)

---

## Is Versioning required?

Yes.

Versioning must be enabled on both source and destination buckets.

---

## Does replication copy existing objects?

Not by default.

Use S3 Batch Replication for existing objects.

---

## Which replication type is best for Disaster Recovery?

Cross-Region Replication (CRR).

---

## Is replication synchronous?

No.

It is asynchronous.

---

# Quick Revision

```
Upload Object

↓

Source Bucket

↓

Versioning

↓

Replication Rule

↓

Destination Bucket
```

---

# Key Takeaways

- Replication automatically copies objects between buckets.
- SRR works within the same Region.
- CRR works across different Regions.
- Versioning is required.
- By default, only new objects are replicated.
- Replication is asynchronous.
