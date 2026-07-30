# Amazon S3 Event Notifications

## Learning Objectives

After completing this lesson, you will be able to:

- Understand S3 Event Notifications.
- Learn which events Amazon S3 can detect.
- Send notifications to AWS services.
- Automate workflows using S3 events.
- Understand common real-world use cases.
- Answer interview questions.

---

# What are S3 Event Notifications?

S3 Event Notifications allow Amazon S3 to automatically send a notification or trigger another AWS service when a specific event occurs.

Example:

```
Upload Image

↓

Amazon S3

↓

Trigger Event

↓

AWS Lambda

↓

Resize Image
```

No manual action is required.

---

# Why Do We Need Event Notifications?

Without Event Notifications:

```
Upload File

↓

Administrator checks bucket

↓

Processes file manually
```

With Event Notifications:

```
Upload File

↓

S3 Detects Event

↓

Automatically Triggers AWS Service
```

Benefits:

- Automation
- Faster processing
- No manual intervention
- Event-driven architecture

---

# Supported Events

Amazon S3 can detect many events.

Common examples:

- Object Created
- Object Deleted
- Object Restore Completed
- Replication Completed
- Lifecycle Transition
- Lifecycle Expiration

Most commonly used:

```
Object Created

↓

File Uploaded
```

and

```
Object Deleted

↓

File Removed
```

---

# Supported Destinations

Amazon S3 can send notifications to:

- AWS Lambda
- Amazon SNS
- Amazon SQS

```
Amazon S3

│
├── AWS Lambda
├── Amazon SNS
└── Amazon SQS
```

---

# 1. AWS Lambda

Lambda runs code automatically.

Example:

```
Upload image.jpg

↓

S3

↓

Lambda

↓

Resize Image

↓

Save Thumbnail
```

Common use cases:

- Image resizing
- Video conversion
- Virus scanning
- File validation
- Metadata extraction

---

# 2. Amazon SNS

SNS sends notifications to subscribers.

Example:

```
Upload Report

↓

S3

↓

SNS

↓

Email

SMS

Application
```

Use cases:

- Alert administrators
- Notify users
- Broadcast messages

---

# 3. Amazon SQS

SQS stores messages for processing.

Example:

```
Upload File

↓

S3

↓

SQS Queue

↓

Application Reads Queue

↓

Process File
```

Useful when:

- Large numbers of uploads occur.
- Processing should happen later.
- Applications need reliable message handling.

---

# Event Flow

```
User Uploads File

↓

Amazon S3

↓

Event Notification

↓

Lambda

↓

Process File
```

---

# Event Filtering

You can trigger notifications only for specific objects.

Example:

Only trigger for:

```
images/
```

or

```
uploads/
```

You can also filter by file extension.

Example:

```
.jpg

.png

.pdf
```

Example:

```
images/

↓

photo.jpg

↓

Trigger Lambda

------------

documents/

↓

report.pdf

↓

No Trigger
```

---

# Real-World Example

A company allows customers to upload profile pictures.

```
Customer Uploads

↓

S3 Bucket

↓

Lambda

↓

Resize Image

↓

Store Thumbnail
```

Everything happens automatically.

---

# Another Example

Users upload invoices.

```
Upload Invoice

↓

S3

↓

SNS

↓

Finance Team Receives Email
```

---

# Best Practices

✅ Filter events using prefixes and suffixes.

✅ Use Lambda for lightweight processing.

✅ Use SQS for high-volume workloads.

✅ Monitor Lambda execution with CloudWatch.

✅ Avoid unnecessary event triggers.

---

# Common Mistakes

❌ Triggering Lambda for every object.

✔ Filter only required folders or file types.

---

❌ Creating notification loops.

Example:

Lambda writes a new object back into the same bucket and triggers itself repeatedly.

✔ Write processed files to a different prefix or bucket.

---

❌ Forgetting IAM permissions.

✔ Ensure S3 can invoke Lambda or publish to SNS/SQS.

---

# Interview Questions

## What are S3 Event Notifications?

A feature that automatically sends notifications or triggers AWS services when events occur in an S3 bucket.

---

## Which AWS services can S3 send notifications to?

- AWS Lambda
- Amazon SNS
- Amazon SQS

---

## Can S3 trigger Lambda?

Yes.

---

## Can Event Notifications be filtered?

Yes.

You can filter by object prefix and suffix.

---

## Name one real-world use case.

Automatically resize uploaded images using AWS Lambda.

---

# Quick Revision

```
Upload File

↓

Amazon S3

↓

Event

↓

Lambda

SNS

SQS
```

---

# Key Takeaways

- S3 Event Notifications automate workflows.
- Common events include object creation and deletion.
- Notifications can be sent to Lambda, SNS, or SQS.
- Prefix and suffix filters reduce unnecessary processing.
- Event-driven architectures improve scalability and automation.
