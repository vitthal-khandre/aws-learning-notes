# Amazon S3 Hands-on Lab

## Lab Objectives

In this lab, you will learn how to:

- Create S3 buckets
- Upload and manage objects
- Enable Versioning
- Configure Lifecycle Rules
- Enable Default Encryption
- Configure Bucket Policies
- Host a Static Website
- Enable Transfer Acceleration
- Configure Event Notifications
- Explore Replication (Optional)

---

# Lab Scenario

ABC Technologies wants to migrate its company website and backups to Amazon S3.

Requirements:

- Website files should be publicly accessible.
- Backup files must remain private.
- Enable Versioning for backups.
- Automatically archive and delete old backups.
- Encrypt all uploaded files.
- Trigger a notification when new images are uploaded.

---

# AWS Architecture

```
                    Internet
                        │
                        ▼
              Website Endpoint
                        │
                        ▼
             website-bucket
                        │
        ┌───────────────┴───────────────┐
        ▼                               ▼
 Static Website                  Public Read Policy

                       

             backup-bucket
                    │
      ┌─────────────┼─────────────┐
      ▼             ▼             ▼
 Versioning   Lifecycle Rule   Encryption
                    │
                    ▼
         (Optional) Replication

                    │
                    ▼
             Event Notification
                    │
                    ▼
                 Lambda
```

---

# Step 1 – Create Buckets

Create two buckets.

Bucket 1

```
vk-static-website-demo
```

Bucket 2

```
vk-backup-demo
```

Keep bucket names globally unique.

---

# Step 2 – Upload Objects

Website bucket

```
index.html
error.html
style.css
logo.png
```

Backup bucket

```
backup.zip
database.sql
report.pdf
```

---

# Step 3 – Enable Versioning

Open:

```
Backup Bucket

↓

Properties

↓

Bucket Versioning

↓

Enable
```

Verify that uploading a new version of the same file creates multiple versions.

---

# Step 4 – Enable Default Encryption

Open:

```
Bucket

↓

Properties

↓

Default Encryption
```

Choose:

```
SSE-S3
```

(Optional: Use SSE-KMS if you want to explore KMS.)

---

# Step 5 – Create Lifecycle Rule

Open:

```
Management

↓

Lifecycle Rules

↓

Create Rule
```

Rule:

```
Rule Name

Archive-Backups
```

Transition

```
30 Days

↓

Standard-IA
```

Transition

```
180 Days

↓

Glacier Flexible Retrieval
```

Expiration

```
365 Days

↓

Delete
```

---

# Step 6 – Configure Static Website Hosting

Website Bucket

↓

Properties

↓

Static Website Hosting

Enable

```
Index Document

index.html
```

```
Error Document

error.html
```

---

# Step 7 – Configure Bucket Policy

Allow public read access **only** for the website bucket.

Example:

```json
{
  "Version":"2012-10-17",
  "Statement":[
    {
      "Effect":"Allow",
      "Principal":"*",
      "Action":"s3:GetObject",
      "Resource":"arn:aws:s3:::vk-static-website-demo/*"
    }
  ]
}
```

> ⚠️ For this lab only, disable **Block Public Access** on the website bucket. Do **not** do this for buckets containing private data.

---

# Step 8 – Verify Website

Copy the Website Endpoint.

Open it in your browser.

Expected Result:

```
My Company Website
```

should appear.

---

# Step 9 – Enable Transfer Acceleration

Website Bucket

↓

Properties

↓

Transfer Acceleration

↓

Enable

Verify the accelerate endpoint:

```
https://vk-static-website-demo.s3-accelerate.amazonaws.com
```

---

# Step 10 – Configure Event Notification

Create a Lambda function named:

```
ImageProcessor
```

Configure:

Event:

```
Object Created
```

Prefix:

```
images/
```

Suffix:

```
.jpg
```

Destination:

```
Lambda
```

Upload:

```
images/photo.jpg
```

Verify Lambda execution in CloudWatch Logs.

---

# Step 11 – (Optional) Configure Replication

Create another bucket:

```
vk-backup-dr
```

Enable Versioning on both buckets.

Create a Cross-Region Replication (CRR) rule.

Upload:

```
test.txt
```

Verify it appears in the destination bucket.

---

# Step 12 – Test Versioning

Upload:

```
report.pdf
```

Upload another file with the same name.

Open:

```
Versions
```

Verify:

```
Version 1

Version 2
```

---

# Step 13 – Verify Encryption

Select any uploaded object.

Open:

```
Properties
```

Verify:

```
Server-side encryption

↓

SSE-S3
```

---

# Step 14 – Cleanup

Delete:

- Website bucket
- Backup bucket
- Replication bucket (if created)
- Lambda function (optional)

Remember:

Buckets must be empty before deletion.

---

# Lab Checklist

| Task | Status |
|------|--------|
| Created Buckets | ☐ |
| Uploaded Files | ☐ |
| Enabled Versioning | ☐ |
| Enabled Encryption | ☐ |
| Configured Lifecycle Rule | ☐ |
| Hosted Static Website | ☐ |
| Added Bucket Policy | ☐ |
| Enabled Transfer Acceleration | ☐ |
| Configured Event Notification | ☐ |
| Tested Versioning | ☐ |
| Verified Encryption | ☐ |
| (Optional) Configured Replication | ☐ |
| Cleaned Up Resources | ☐ |

---

# Troubleshooting

## Website shows "Access Denied"

Check:

- Bucket Policy
- Block Public Access
- Object permissions
- Correct Website Endpoint

---

## Lifecycle Rule not running immediately

Lifecycle actions are asynchronous.

They may take time to execute.

---

## Replication not working

Verify:

- Versioning enabled on both buckets
- IAM Role exists
- Replication rule is enabled

---

## Lambda not triggered

Check:

- Event notification configuration
- Prefix and suffix filters
- Lambda permissions
- CloudWatch Logs

---

# Real-World Scenario

Company:

ABC Technologies

Requirements:

- Public website
- Secure backups
- Automatic lifecycle management
- Encrypted storage
- Automatic image processing

AWS Services Used:

- Amazon S3
- IAM
- Lambda
- CloudWatch
- (Optional) KMS
- (Optional) Cross-Region Replication

---

# Interview Questions

## Which S3 features did you configure?

- Bucket creation
- Versioning
- Lifecycle Rules
- Encryption
- Bucket Policy
- Static Website Hosting
- Transfer Acceleration
- Event Notifications
- Replication (optional)

---

## Why enable Versioning?

To protect against accidental deletion or overwriting of objects.

---

## Why use Lifecycle Rules?

To reduce storage costs by automatically transitioning or deleting old objects.

---

## Why use Event Notifications?

To automate workflows such as image processing or alerts.

---

## Why use Transfer Acceleration?

To improve upload and download performance for users far from the bucket's Region.

---

# Key Takeaways

- Amazon S3 is more than object storage—it provides security, automation, lifecycle management, and website hosting.
- Versioning protects your data.
- Lifecycle Rules reduce costs.
- Encryption protects stored data.
- Bucket Policies control access.
- Event Notifications enable automation.
- Transfer Acceleration improves global performance.
- Replication enhances disaster recovery.
