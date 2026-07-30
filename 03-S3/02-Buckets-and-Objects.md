# Buckets and Objects

## Learning Objectives

After completing this lesson, you will be able to:

- Understand what Buckets and Objects are.
- Learn how S3 organizes data.
- Understand Object Keys.
- Learn how folders work in S3.
- Understand Object Metadata.
- Learn Bucket naming rules.
- Understand Object URLs.
- Answer common interview questions.

---

# What is a Bucket?

A Bucket is a container that stores objects (files).

Think of a Bucket as the highest-level storage container in Amazon S3.

Examples:

```
company-backups

employee-documents

website-assets

application-logs
```

Every object must belong to exactly one bucket.

---

# What is an Object?

An Object is the actual data stored inside a bucket.

Examples:

```
resume.pdf

photo.jpg

database.sql

backup.zip

video.mp4
```

Each object contains:

- Data (the file itself)
- Metadata
- Object Key (unique name)
- Version ID (if Versioning is enabled)

---

# Bucket and Object Relationship

```
Amazon S3
      │
      ▼
Bucket
      │
      ▼
Objects
```

Example:

```
Bucket

company-data

│
├── employee.pdf
├── logo.png
├── backup.zip
└── reports.xlsx
```

---

# Bucket Naming Rules

Bucket names must:

- Be globally unique.
- Be between 3 and 63 characters.
- Use lowercase letters only.
- Contain numbers if needed.
- Use hyphens (-).
- Not contain spaces.
- Not contain uppercase letters.
- Not look like an IP address.

Valid:

```
company-backup

company-backup-2026

my-images
```

Invalid:

```
CompanyBackup

My Bucket

192.168.1.1
```

---

# Why Must Bucket Names Be Globally Unique?

S3 bucket names are shared across all AWS customers.

Only one AWS account in the world can own a bucket named:

```
company-backup
```

If that name already exists, you must choose another.

Example:

```
vk-company-backup-2026
```

---

# What is an Object Key?

Every object has a unique identifier called an Object Key.

Example:

```
employee.pdf
```

or

```
images/logo.png
```

The combination of:

```
Bucket Name + Object Key
```

uniquely identifies an object.

Example:

```
Bucket

company-data

Object Key

reports/2026/july.pdf
```

---

# Folder Structure in S3

S3 does **not** have real folders like Windows or Linux.

Folders are created by using prefixes in the object key.

Example:

```
reports/2026/july.pdf
```

Object Key:

```
reports/2026/july.pdf
```

AWS Console displays:

```
reports/

↓

2026/

↓

july.pdf
```

The folders are a visual representation of the object key.

---

# Example Structure

```
Bucket

company-data

│
├── images/
│      ├── logo.png
│      └── banner.jpg
│
├── documents/
│      ├── policy.pdf
│      └── salary.xlsx
│
└── backups/
       └── database.sql
```

Actual Object Keys:

```
images/logo.png

images/banner.jpg

documents/policy.pdf

documents/salary.xlsx

backups/database.sql
```

---

# Object Metadata

Metadata is information about the object.

Examples:

- File Size
- Content Type
- Last Modified Date
- Storage Class
- Encryption Status
- Custom Metadata

Example:

```
photo.jpg

↓

Size

2 MB

↓

Content-Type

image/jpeg

↓

Storage Class

Standard
```

---

# Object URL

Every object has a URL.

Example:

```
https://company-data.s3.ap-south-1.amazonaws.com/logo.png
```

URL format:

```
https://bucket-name.s3.region.amazonaws.com/object-key
```

Note:

The object is only accessible if permissions allow it.

---

# Bucket Region

A bucket belongs to one AWS Region.

Example:

```
Mumbai

ap-south-1
```

The bucket cannot later be moved to another Region.

If you need another Region, create a new bucket and copy the data.

---

# Bucket Limits

Default bucket quota:

AWS allows many buckets per account (the default quota can be increased if required).

Each bucket can store:

- Millions
- Billions
- Trillions of objects

There is no practical limit on the number of objects.

---

# Object Size

Minimum:

```
0 Bytes
```

Maximum:

```
5 TB
```

For objects larger than **5 GB**, use Multipart Upload.

---

# Real-World Example

Company:

ABC Technologies

```
Amazon S3

↓

Bucket

abc-company-data

│
├── HR/
│     ├── employees.xlsx
│     └── payroll.pdf
│
├── IT/
│     ├── backup.zip
│     └── scripts/
│            setup.sh
│
└── Marketing/
      └── logo.png
```

---

# Best Practices

✅ Use meaningful bucket names.

✅ Organize objects using prefixes.

✅ Keep buckets private by default.

✅ Enable Versioning for important buckets.

✅ Use Lifecycle Rules for old files.

---

# Common Mistakes

❌ Thinking folders are real directories.

✔ They are prefixes in the object key.

---

❌ Using uppercase letters in bucket names.

✔ Use lowercase only.

---

❌ Making buckets public accidentally.

✔ Keep Block Public Access enabled unless required.

---

# Interview Questions

## What is a Bucket?

A Bucket is a container used to store objects in Amazon S3.

---

## What is an Object?

An Object is a file stored in an S3 bucket along with its metadata and object key.

---

## Are folders real in Amazon S3?

No.

Folders are logical prefixes in the object key.

---

## What makes an object unique?

The combination of:

- Bucket Name
- Object Key

---

## Can two buckets have the same name?

No.

Bucket names are globally unique.

---

## Can a bucket be moved to another Region?

No.

Create a new bucket in the target Region and copy the data.

---

# Quick Revision

```
Amazon S3
     │
     ▼
Bucket
     │
     ▼
Objects
     │
     ▼
Object Key
     │
     ▼
Metadata
```

---

# Key Takeaways

- Buckets contain objects.
- Objects are files with metadata.
- Bucket names are globally unique.
- S3 folders are prefixes, not real directories.
- Object keys identify files within a bucket.
- Buckets belong to one AWS Region.
- A single object can be up to 5 TB.
