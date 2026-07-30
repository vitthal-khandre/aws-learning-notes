# Amazon S3 Versioning

## Learning Objectives

After completing this lesson, you will be able to:

- Understand what S3 Versioning is.
- Learn how Version IDs work.
- Understand Delete Markers.
- Recover deleted or overwritten files.
- Learn about MFA Delete.
- Understand real-world use cases.
- Answer common interview questions.

---

# What is S3 Versioning?

S3 Versioning is a feature that keeps multiple versions of the same object in a bucket.

Instead of replacing or permanently deleting a file, S3 stores each change as a new version.

Think of it like **Microsoft Word's version history** or **Git commits**.

---

# Why Do We Need Versioning?

Without Versioning:

```
Upload report.pdf

↓

Edit report.pdf

↓

Upload Again

↓

Old File Lost Forever
```

With Versioning:

```
report.pdf

↓

Version 1

↓

Version 2

↓

Version 3

↓

All Versions Preserved
```

If you make a mistake, you can restore an older version.

---

# How Versioning Works

Suppose you upload:

```
employee-list.xlsx
```

First upload:

```
Version ID

111AAA
```

After editing and uploading again:

```
Version ID

222BBB
```

Upload again:

```
Version ID

333CCC
```

The bucket now contains:

```
employee-list.xlsx

↓

Version 3 (Current)

↓

Version 2

↓

Version 1
```

---

# Version ID

Every object version has a unique Version ID assigned by AWS.

Example:

```
Object

photo.jpg

↓

Version ID

X1A2B3C4

↓

Current Version
```

Version IDs are generated automatically.

---

# Enabling Versioning

Versioning is enabled **at the bucket level**.

Steps:

```
S3

↓

Bucket

↓

Properties

↓

Bucket Versioning

↓

Enable
```

Once enabled:

- New uploads receive Version IDs.
- Existing objects also begin receiving versions when updated.

---

# Can Versioning Be Disabled?

No.

Once Versioning is enabled, it cannot be permanently turned off.

You can only **Suspend** Versioning.

Possible states:

- Unversioned (before enabling)
- Enabled
- Suspended

---

# What Happens When You Upload Again?

Example:

Before:

```
logo.png

↓

Version 1
```

Upload a new logo:

```
logo.png

↓

Version 2 (Current)

↓

Version 1
```

The previous version is still available.

---

# What Happens When You Delete an Object?

Without Versioning:

```
Delete logo.png

↓

Gone Forever
```

With Versioning:

```
Delete logo.png

↓

Delete Marker Created

↓

Old Versions Still Exist
```

The file appears deleted, but previous versions remain.

---

# Delete Marker

A Delete Marker is a special marker that becomes the current version when you delete an object in a versioned bucket.

Example:

```
photo.jpg

↓

Delete Marker

↓

Version 3

↓

Version 2

↓

Version 1
```

The data is not removed.

Only the Delete Marker hides it.

---

# Recovering a Deleted Object

To restore:

1. Open the bucket.
2. Show Versions.
3. Delete the Delete Marker (or make an older version current).
4. The object becomes accessible again.

---

# Permanently Deleting an Object

To permanently remove data from a versioned bucket:

- Delete the specific object version.

Deleting only the Delete Marker does not remove older versions.

---

# MFA Delete

MFA Delete adds extra protection.

When enabled:

- Deleting object versions requires MFA.
- Disabling Versioning requires MFA.

Benefits:

- Protects against accidental or malicious deletion.

Note:

MFA Delete is supported in specific management scenarios and is less commonly used than Versioning itself.

---

# Storage Cost

Every version consumes storage.

Example:

```
Version 1

10 MB

Version 2

12 MB

Version 3

15 MB

Total Storage

37 MB
```

Old versions increase storage usage until they are deleted or managed with Lifecycle Rules.

---

# Real-World Example

Company:

ABC Technologies

```
employee.xlsx

↓

Version 1

↓

Version 2

↓

Version 3

↓

Version 4
```

An employee accidentally overwrites the file.

The administrator restores Version 3.

No data is lost.

---

# Best Practices

✅ Enable Versioning on important buckets.

✅ Combine Versioning with Lifecycle Rules.

✅ Enable Server-Side Encryption.

✅ Monitor storage usage because old versions consume space.

---

# Common Mistakes

❌ Assuming Delete removes data permanently.

✔ In a versioned bucket, Delete usually creates a Delete Marker.

---

❌ Forgetting that old versions still incur storage charges.

✔ Configure Lifecycle Rules to expire old versions when appropriate.

---

❌ Enabling Versioning after data loss.

✔ Enable Versioning before storing important data.

---

# Interview Questions

## What is S3 Versioning?

S3 Versioning stores multiple versions of an object to protect against accidental overwrite or deletion.

---

## Can Versioning be disabled?

No.

It can only be suspended after being enabled.

---

## What is a Version ID?

A unique identifier assigned to each version of an object.

---

## What is a Delete Marker?

A special marker that hides the current object after deletion while keeping previous versions.

---

## Can deleted objects be recovered?

Yes.

If Versioning is enabled, you can recover objects by removing the Delete Marker or restoring an earlier version.

---

## Does Versioning increase storage cost?

Yes.

Each version occupies storage and is billed until removed.

---

# Quick Revision

```
Bucket

↓

Versioning Enabled

↓

Version 1

↓

Version 2

↓

Version 3

↓

Delete Marker

↓

Recover Anytime
```

---

# Key Takeaways

- Versioning protects against accidental overwrite and deletion.
- Every version receives a unique Version ID.
- Deleting an object creates a Delete Marker instead of immediately removing data.
- Previous versions remain available until explicitly deleted.
- Versioning cannot be turned off, only suspended.
- Old versions consume storage and should be managed with Lifecycle Rules.
