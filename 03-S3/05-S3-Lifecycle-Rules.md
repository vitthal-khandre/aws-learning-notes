# Amazon S3 Lifecycle Rules

## Learning Objectives

After completing this lesson, you will be able to:

- Understand what Lifecycle Rules are.
- Automatically move objects between Storage Classes.
- Automatically delete old objects.
- Manage previous object versions.
- Reduce Amazon S3 storage costs.
- Answer common interview questions.

---

# What are Lifecycle Rules?

Lifecycle Rules are automated policies that tell Amazon S3 what to do with objects as they get older.

Examples:

- Move old files to a cheaper Storage Class.
- Delete temporary files after a certain number of days.
- Delete old versions of objects.

Instead of manually managing files, AWS performs these actions automatically.

---

# Why Do We Need Lifecycle Rules?

Imagine a company creates a backup every day.

```
Day 1 → backup.zip

Day 2 → backup.zip

Day 3 → backup.zip

...

Day 365 → backup.zip
```

Without Lifecycle Rules:

- Storage keeps growing.
- Costs increase.
- Manual cleanup is required.

With Lifecycle Rules:

```
0–30 Days
↓

S3 Standard

31–90 Days
↓

Standard-IA

91–365 Days
↓

Glacier Flexible Retrieval

After 365 Days
↓

Delete Automatically
```

Storage is optimized without manual work.

---

# What Can Lifecycle Rules Do?

Lifecycle Rules can:

- Transition objects to another Storage Class.
- Expire (delete) objects.
- Delete previous object versions.
- Remove incomplete Multipart Uploads.

---

# Transition Action

A Transition moves an object to a different Storage Class.

Example:

```
Upload File

↓

S3 Standard

↓

After 30 Days

↓

Standard-IA

↓

After 180 Days

↓

Glacier Flexible Retrieval
```

The object remains the same, but storage costs decrease.

---

# Expiration Action

Expiration permanently deletes objects after a specified period.

Example:

```
logs.txt

↓

Created Today

↓

After 90 Days

↓

Deleted Automatically
```

Useful for:

- Log files
- Temporary reports
- Test data

---

# Noncurrent Version Expiration

Works only with Versioning enabled.

Example:

```
report.pdf

↓

Version 1

↓

Version 2

↓

Version 3

↓

Delete Version 1 After 60 Days
```

This keeps only recent versions and saves storage costs.

---

# Abort Incomplete Multipart Uploads

Large files may use Multipart Upload.

Sometimes uploads fail before completion.

Lifecycle Rules can automatically remove these incomplete uploads.

Example:

```
5 GB Upload

↓

Interrupted

↓

Incomplete Upload

↓

Delete After 7 Days
```

---

# Lifecycle Rule Components

A Lifecycle Rule usually contains:

- Rule Name
- Scope (Entire Bucket or Prefix)
- Filter (Optional)
- Actions
- Timing (Days)

Example:

```
Rule Name

Archive-Old-Files

↓

Prefix

backups/

↓

30 Days

↓

Move to Standard-IA

↓

180 Days

↓

Move to Glacier Flexible Retrieval

↓

365 Days

↓

Delete
```

---

# Applying Rules to Specific Folders

Remember:

S3 folders are prefixes.

Example:

```
Bucket

company-data

│
├── images/
├── backups/
└── logs/
```

Rule:

```
Only Apply To

backups/
```

Images and logs remain unaffected.

---

# Real-World Example

ABC Technologies stores daily database backups.

Policy:

```
First 30 Days

↓

S3 Standard

↓

31–180 Days

↓

Standard-IA

↓

181–365 Days

↓

Glacier Flexible Retrieval

↓

After 1 Year

↓

Delete
```

Benefits:

- Lower storage costs.
- Automatic management.
- No manual cleanup.

---

# Best Practices

✅ Use Lifecycle Rules for backups.

✅ Move old files to cheaper Storage Classes.

✅ Delete temporary files automatically.

✅ Delete old object versions if Versioning is enabled.

✅ Test rules before applying them to production.

---

# Common Mistakes

❌ Keeping old backups in S3 Standard forever.

✔ Move them to cheaper Storage Classes.

---

❌ Forgetting old object versions.

✔ Configure Noncurrent Version Expiration.

---

❌ Deleting data without verifying retention requirements.

✔ Confirm business and legal retention policies first.

---

# Interview Questions

## What is an S3 Lifecycle Rule?

An automated policy that transitions or deletes S3 objects based on age or other criteria.

---

## Why are Lifecycle Rules used?

To reduce storage costs and automate object management.

---

## Can Lifecycle Rules move objects to Glacier?

Yes.

Lifecycle Rules can transition objects to Glacier storage classes.

---

## Can Lifecycle Rules delete objects?

Yes.

Objects can be automatically deleted after a specified number of days.

---

## Can Lifecycle Rules delete previous versions?

Yes.

When Versioning is enabled, they can remove noncurrent object versions.

---

## Can Lifecycle Rules remove incomplete Multipart Uploads?

Yes.

They can automatically abort incomplete Multipart Uploads after a defined number of days.

---

# Quick Revision

```
Upload File

↓

S3 Standard

↓

Lifecycle Rule

↓

Standard-IA

↓

Glacier

↓

Delete
```

---

# Key Takeaways

- Lifecycle Rules automate storage management.
- Transition actions move objects to cheaper Storage Classes.
- Expiration actions permanently delete objects.
- Noncurrent Version Expiration manages previous object versions.
- Lifecycle Rules help reduce storage costs and administrative effort.
