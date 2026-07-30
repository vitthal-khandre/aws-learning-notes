# Amazon S3 Storage Classes

## Learning Objectives

After completing this lesson, you will be able to:

- Understand what S3 Storage Classes are.
- Learn when to use each Storage Class.
- Compare Standard, IA, Intelligent-Tiering, and Glacier.
- Choose the right Storage Class for different workloads.
- Understand retrieval times and costs.
- Answer common interview questions.

---

# What is a Storage Class?

A Storage Class determines:

- How your data is stored.
- How much storage costs.
- How quickly data can be retrieved.
- How durable and available the data is.

Choosing the correct Storage Class helps reduce costs while meeting application requirements.

---

# Why Do We Need Storage Classes?

Imagine you have three types of files:

1. Files you use every day.
2. Files you use once a month.
3. Files you rarely access but must keep for years.

Keeping all files in the most expensive storage wastes money.

AWS provides multiple Storage Classes so you can match storage cost to access patterns.

---

# Types of S3 Storage Classes

Amazon S3 offers these commonly used Storage Classes:

- S3 Standard
- S3 Intelligent-Tiering
- S3 Standard-Infrequent Access (Standard-IA)
- S3 One Zone-Infrequent Access (One Zone-IA)
- S3 Glacier Instant Retrieval
- S3 Glacier Flexible Retrieval
- S3 Glacier Deep Archive

---

# 1. S3 Standard

Best for:

- Frequently accessed data.

Examples:

- Websites
- Mobile applications
- Images
- Videos
- Active business files

Features:

- Low latency
- High throughput
- Multiple Availability Zones
- 99.999999999% (11 nines) durability

```
Users

↓

Read Files Frequently

↓

S3 Standard
```

---

# 2. S3 Intelligent-Tiering

Best for:

Data with **unknown or changing access patterns**.

AWS automatically moves objects between access tiers based on usage.

Examples:

- Shared company documents
- User-uploaded files
- Long-term application data

Advantages:

- Automatic optimization
- No manual management
- Helps reduce storage costs

```
Frequently Used

↓

Standard Tier

↓

Less Used

↓

Lower-Cost Tier

↓

Automatic
```

---

# 3. S3 Standard-IA

IA = Infrequent Access

Best for:

Data that is rarely accessed but must be available quickly when needed.

Examples:

- Backups
- Disaster Recovery files
- Older documents

Features:

- Lower storage cost than Standard
- Retrieval fee applies
- Multi-AZ storage

---

# 4. S3 One Zone-IA

Stores data in **one Availability Zone only**.

Best for:

- Re-creatable data
- Secondary backups
- Temporary files

Advantages:

- Lower storage cost

Disadvantage:

If the Availability Zone is permanently lost, the data may also be lost.

```
One AZ Only

↓

Lower Cost

↓

Lower Resilience
```

---

# 5. S3 Glacier Instant Retrieval

Best for:

Archive data that is rarely accessed but must be retrieved immediately.

Examples:

- Medical records
- Archived media
- Historical reports

Features:

- Very low storage cost
- Millisecond retrieval

---

# 6. S3 Glacier Flexible Retrieval

Previously known as **S3 Glacier**.

Best for:

Long-term archives that do not require instant access.

Examples:

- Compliance data
- Financial records
- Audit logs

Retrieval options:

- Expedited (minutes)
- Standard (hours)
- Bulk (hours)

---

# 7. S3 Glacier Deep Archive

Lowest-cost S3 storage class.

Best for:

Data that is rarely, if ever, accessed.

Examples:

- Legal archives
- Government records
- Long-term backups

Retrieval typically takes several hours.

---

# Comparison Table

| Storage Class | Access Frequency | Availability Zones | Retrieval Time | Typical Use |
|---------------|------------------|--------------------|----------------|-------------|
| Standard | Frequent | Multiple | Milliseconds | Websites, apps |
| Intelligent-Tiering | Unknown | Multiple | Milliseconds | Automatic optimization |
| Standard-IA | Infrequent | Multiple | Milliseconds | Backups |
| One Zone-IA | Infrequent | One | Milliseconds | Re-creatable data |
| Glacier Instant Retrieval | Rare | Multiple | Milliseconds | Archived data with immediate access |
| Glacier Flexible Retrieval | Very Rare | Multiple | Minutes to Hours | Compliance archives |
| Glacier Deep Archive | Almost Never | Multiple | Hours | Long-term archival |

---

# Which Storage Class Should You Choose?

```
Frequently Accessed?
        │
     Yes ▼
 S3 Standard

        │
     No ▼

Access Pattern Unknown?
        │
     Yes ▼
 Intelligent-Tiering

        │
     No ▼

Need Immediate Access?
        │
     Yes ▼
 Standard-IA

        │
     No ▼

Can Wait Minutes or Hours?
        │
     Yes ▼
 Glacier

        │
     Long-Term Storage?
        ▼
 Glacier Deep Archive
```

---

# Real-World Example

ABC Technologies

```
Website Images
↓

S3 Standard

------------------------

Employee Backups
↓

S3 Standard-IA

------------------------

Audit Reports
↓

Glacier Flexible Retrieval

------------------------

Legal Records (10 Years)
↓

Glacier Deep Archive
```

---

# Best Practices

✅ Use S3 Standard for active applications.

✅ Use Intelligent-Tiering when access patterns are unpredictable.

✅ Store backups in Standard-IA.

✅ Use Glacier for archives.

✅ Use Lifecycle Rules to automatically move objects between Storage Classes.

---

# Common Mistakes

❌ Keeping archive data in S3 Standard.

✔ Move it to Glacier to save money.

---

❌ Using One Zone-IA for critical production data.

✔ Store critical data in Multi-AZ Storage Classes.

---

❌ Forgetting retrieval fees for IA and Glacier classes.

✔ Consider both storage and retrieval costs.

---

# Interview Questions

## What is an S3 Storage Class?

A Storage Class defines how data is stored, accessed, and billed in Amazon S3.

---

## Which Storage Class is best for frequently accessed data?

S3 Standard.

---

## Which Storage Class automatically optimizes storage costs?

S3 Intelligent-Tiering.

---

## Which Storage Class stores data in only one Availability Zone?

S3 One Zone-IA.

---

## Which Storage Class is the cheapest?

S3 Glacier Deep Archive.

---

## Which Storage Class provides the fastest archive retrieval?

S3 Glacier Instant Retrieval.

---

# Quick Revision

```
Frequent Access

↓

S3 Standard

↓

Unknown Pattern

↓

Intelligent-Tiering

↓

Rare Access

↓

Standard-IA

↓

One AZ

↓

One Zone-IA

↓

Archive

↓

Glacier

↓

Long-Term Archive

↓

Deep Archive
```

---

# Key Takeaways

- Storage Classes help optimize storage cost.
- S3 Standard is for frequently accessed data.
- Intelligent-Tiering automatically adjusts based on access.
- Standard-IA is for infrequently accessed but quickly available data.
- One Zone-IA stores data in a single Availability Zone.
- Glacier classes are designed for archival storage.
- Glacier Deep Archive is the lowest-cost option for long-term retention.
