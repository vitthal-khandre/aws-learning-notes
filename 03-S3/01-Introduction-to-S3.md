# Introduction to Amazon S3

## Learning Objectives

After completing this lesson, you will be able to:

- Understand what Amazon S3 is.
- Learn why S3 is called an Object Storage service.
- Understand Buckets and Objects.
- Learn common real-world use cases.
- Understand key S3 features.
- Know S3 limits and characteristics.
- Answer common interview questions.

---

# What is Amazon S3?

Amazon S3 (Simple Storage Service) is a cloud storage service provided by AWS.

It allows you to store and retrieve any amount of data from anywhere over the internet.

Think of S3 as an **unlimited online hard drive** that is highly durable, scalable, and secure.

---

# Why is it called "Simple Storage Service"?

AWS designed S3 to make storing and retrieving files simple.

Instead of managing disks or servers, you simply:

- Create a Bucket
- Upload Objects (files)
- Download Objects when needed

AWS manages the storage infrastructure for you.

---

# What is Object Storage?

Amazon S3 is an **Object Storage** service.

Unlike a traditional file system, S3 stores data as **Objects**.

Each Object consists of:

- File (Data)
- Metadata (Information about the file)
- Unique Identifier (Object Key)

Example:

```
Object

↓

photo.jpg

↓

Metadata

↓

Created: 30-Jul-2026

↓

Key

↓

photos/photo.jpg
```

---

# Bucket vs Object

## Bucket

A Bucket is a container that stores Objects.

Think of it as a folder at the highest level.

Example:

```
Bucket

company-backup
```

---

## Object

An Object is the actual file stored inside a Bucket.

Examples:

```
resume.pdf

photo.jpg

backup.zip

video.mp4
```

---

# Simple Diagram

```
Amazon S3

↓

Bucket

company-data

↓

Objects

resume.pdf

invoice.xlsx

photo.jpg

backup.zip
```

---

# Real-Life Example

Imagine a warehouse.

Warehouse

↓

Shelves

↓

Boxes

In Amazon S3:

Warehouse = AWS S3

Shelf = Bucket

Box = Object

---

# Common S3 Use Cases

Amazon S3 is used for:

- File Storage
- Backup and Restore
- Static Website Hosting
- Application Assets (images, videos)
- Log Storage
- Data Archiving
- Software Downloads
- Big Data
- Machine Learning datasets

---

# Key Features of Amazon S3

## 1. Highly Durable

Amazon S3 is designed for **99.999999999% (11 nines)** durability.

This means your data is extremely unlikely to be lost.

---

## 2. Highly Available

S3 stores data across multiple Availability Zones within a Region.

If one Availability Zone fails, your data remains available.

---

## 3. Scalable

Store:

- 10 files
- 10 million files
- Billions of files

No storage planning is required.

---

## 4. Secure

Supports:

- IAM Policies
- Bucket Policies
- Encryption
- Access Control Lists (ACLs)
- MFA Delete (for versioned buckets)

---

## 5. Pay Only for What You Use

You pay based on:

- Storage used
- Requests
- Data transferred out
- Optional features (such as replication)

No upfront investment is required.

---

# S3 is a Regional Service

A Bucket is created in a specific AWS Region.

Example:

```
Mumbai

ap-south-1
```

Although the Bucket belongs to one Region, AWS stores the data redundantly across multiple Availability Zones within that Region.

---

# S3 Naming Rules

Bucket names:

- Must be globally unique.
- Must be between 3 and 63 characters.
- Can contain lowercase letters, numbers, and hyphens (-).
- Cannot contain uppercase letters or spaces.

Example:

```
company-backup-2026
```

Invalid examples:

```
CompanyBackup
My Bucket
```

---

# S3 Storage Limits

## Bucket Limit

You can create many buckets in an AWS account (AWS has a default quota that can be increased if needed).

---

## Object Size

Minimum:

```
0 Bytes
```

Maximum:

```
5 TB
```

For objects larger than 5 GB, AWS recommends using Multipart Upload.

---

# How S3 Works

```
User

↓

Upload File

↓

Amazon S3 Bucket

↓

Store Object

↓

Download Anytime
```

---

# Example

```
Bucket

company-backup

↓

employee.pdf

database.sql

photo.png

logs.zip
```

---

# S3 vs Local Storage

| Local Hard Disk | Amazon S3 |
|-----------------|-----------|
| Limited size | Virtually unlimited |
| Hardware maintenance required | Managed by AWS |
| Single location | Multiple Availability Zones |
| Risk of disk failure | Extremely durable |
| Difficult to scale | Automatically scalable |

---

# Best Practices

✅ Use meaningful Bucket names.

✅ Enable Versioning for important data.

✅ Enable Encryption.

✅ Use IAM and Bucket Policies.

✅ Avoid making Buckets public unless required.

---

# Common Mistakes

❌ Storing sensitive data in a public Bucket.

✔ Keep Buckets private by default.

---

❌ Using weak permissions.

✔ Apply the Principle of Least Privilege.

---

❌ Forgetting Versioning.

✔ Enable Versioning for important Buckets.

---

# Real AWS Example

Company:

ABC Technologies

```
Amazon S3

↓

Bucket

abc-backup

↓

daily-backup.zip

↓

Stored Across Multiple AZs

↓

Safe Backup
```

---

# Interview Questions

## What is Amazon S3?

Amazon S3 is AWS's object storage service used to store and retrieve data from anywhere.

---

## What does S3 stand for?

Simple Storage Service.

---

## What is stored in an S3 Bucket?

Objects.

---

## What is an Object?

A file along with its metadata and unique key.

---

## Is S3 a Regional or Global service?

S3 Buckets are created in a Region, and the data is stored redundantly across multiple Availability Zones within that Region.

---

## What is the maximum object size?

5 TB.

---

## What is the durability of Amazon S3?

99.999999999% (11 nines).

---

# Quick Revision

```
Amazon S3

↓

Bucket

↓

Objects

↓

Highly Durable

↓

Highly Scalable

↓

Secure

↓

Pay As You Go
```

---

# Key Takeaways

- Amazon S3 is an Object Storage service.
- Data is stored as Objects inside Buckets.
- Buckets are created in a specific AWS Region.
- S3 provides 11 nines of durability.
- The maximum object size is 5 TB.
- S3 is used for backups, websites, logs, media, and much more.
