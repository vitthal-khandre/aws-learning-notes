# Amazon S3 Encryption

## Learning Objectives

After completing this lesson, you will be able to:

- Understand why encryption is important.
- Learn the difference between encryption at rest and in transit.
- Understand Server-Side Encryption (SSE).
- Compare SSE-S3, SSE-KMS, and SSE-C.
- Understand Client-Side Encryption.
- Choose the correct encryption method.
- Answer common interview questions.

---

# What is Encryption?

Encryption converts readable data (plaintext) into unreadable data (ciphertext).

Only someone with the correct key can decrypt and read the original data.

Example:

Before Encryption

```
Employee Salary = $5000
```

After Encryption

```
A7D93KX91PQL82...
```

Without the decryption key, the encrypted data is meaningless.

---

# Why Do We Need Encryption?

Encryption protects data from unauthorized access.

Examples:

- Customer information
- Bank records
- Medical reports
- Company backups
- HR documents

Even if someone gains access to the storage, encrypted data is difficult to read without the proper key.

---

# Types of Encryption in S3

Amazon S3 supports:

- Encryption at Rest
- Encryption in Transit

---

# 1. Encryption at Rest

Protects data while it is stored in Amazon S3.

```
Upload File

↓

Amazon S3

↓

Encrypted Storage
```

If someone accesses the storage media directly, the data remains encrypted.

---

# 2. Encryption in Transit

Protects data while it is moving between a client and Amazon S3.

Use:

- HTTPS (TLS)

```
Computer

⇄ HTTPS ⇄

Amazon S3
```

Always use HTTPS instead of HTTP when accessing S3.

---

# Server-Side Encryption (SSE)

With Server-Side Encryption, AWS encrypts the object after it reaches S3.

```
Upload File

↓

Amazon S3

↓

AWS Encrypts

↓

Stored Securely
```

There are three common Server-Side Encryption options:

- SSE-S3
- SSE-KMS
- SSE-C

---

# 1. SSE-S3

Server-Side Encryption with Amazon S3 managed keys.

AWS:

- Encrypts the object.
- Manages the encryption keys.
- Rotates keys automatically.

Best for:

- General-purpose workloads
- Easy setup
- Default encryption for many buckets

```
You Upload

↓

AWS Encrypts

↓

AWS Manages Keys
```

Advantages:

- Easy to use
- No key management
- Good default option

---

# 2. SSE-KMS

Server-Side Encryption using AWS Key Management Service (KMS).

AWS KMS allows you to:

- Control encryption keys.
- Rotate keys.
- Audit key usage with CloudTrail.
- Apply fine-grained access control.

```
Upload

↓

S3

↓

AWS KMS

↓

Encrypted Object
```

Best for:

- Financial applications
- Healthcare
- Government
- Compliance requirements

Advantages:

- More control over keys
- Audit logging
- IAM integration

---

# 3. SSE-C

Server-Side Encryption with Customer-Provided Keys.

You provide the encryption key for every upload and download request.

AWS:

- Uses your key to encrypt/decrypt.
- Does not permanently store your key.

```
Customer Key

↓

S3 Uses Key

↓

Encrypted Storage
```

Best for:

Organizations that require full control of encryption keys.

Disadvantages:

- More complex
- You are responsible for key management
- Losing the key means the data cannot be decrypted

---

# Client-Side Encryption

With Client-Side Encryption, the data is encrypted **before** it is uploaded to Amazon S3.

```
Computer

↓

Encrypt File

↓

Upload Encrypted File

↓

Amazon S3
```

AWS never sees the plaintext.

Best for:

- Highly sensitive information
- Applications with strict security requirements

---

# Comparison Table

| Feature | SSE-S3 | SSE-KMS | SSE-C | Client-Side |
|----------|--------|---------|--------|-------------|
| Who manages keys? | AWS | AWS KMS (customer controls usage) | Customer | Customer |
| Easy to use | ✅ | ✅ | ❌ | ❌ |
| Audit key usage | ❌ | ✅ | ❌ | Depends on your solution |
| Compliance support | Good | Excellent | Depends | Excellent |
| Typical use | General storage | Regulated workloads | Special requirements | Maximum control |

---

# Default Bucket Encryption

You can configure a bucket so that all newly uploaded objects are encrypted automatically.

Steps:

```
S3

↓

Bucket

↓

Properties

↓

Default Encryption

↓

Choose:

SSE-S3

or

SSE-KMS
```

This helps ensure uploads are encrypted even if the uploader forgets to specify encryption.

---

# Real-World Example

ABC Technologies stores employee salary reports.

```
Salary Report

↓

Amazon S3

↓

SSE-KMS

↓

Encrypted

↓

Only Authorized Users Can Access
```

Benefits:

- Encryption
- Audit logging
- Controlled key access

---

# Best Practices

✅ Enable default bucket encryption.

✅ Use HTTPS for all S3 access.

✅ Use SSE-KMS for sensitive or regulated data.

✅ Restrict access using IAM and Bucket Policies.

✅ Rotate customer-managed KMS keys according to organizational policy.

---

# Common Mistakes

❌ Uploading sensitive data without encryption.

✔ Enable default encryption.

---

❌ Using HTTP.

✔ Always use HTTPS.

---

❌ Giving everyone access to KMS keys.

✔ Follow the Principle of Least Privilege.

---

# Interview Questions

## What is Encryption?

Encryption converts readable data into unreadable ciphertext.

---

## What is Encryption at Rest?

Data is encrypted while stored on disk.

---

## What is Encryption in Transit?

Data is encrypted while moving across the network using HTTPS (TLS).

---

## What is SSE-S3?

Server-Side Encryption where Amazon S3 manages the encryption keys.

---

## What is SSE-KMS?

Server-Side Encryption using AWS Key Management Service, providing greater control and auditing.

---

## What is SSE-C?

Server-Side Encryption where the customer provides the encryption key for each request.

---

## What is Client-Side Encryption?

The client encrypts the data before uploading it to Amazon S3.

---

## Which encryption method provides the greatest AWS-managed control and auditing?

SSE-KMS.

---

# Quick Revision

```
Encryption

↓

At Rest

↓

In Transit

↓

SSE-S3

↓

SSE-KMS

↓

SSE-C

↓

Client-Side
```

---

# Key Takeaways

- Encrypt data both at rest and in transit.
- SSE-S3 is simple and AWS manages the keys.
- SSE-KMS provides stronger control and auditing.
- SSE-C requires the customer to supply encryption keys.
- Client-Side Encryption encrypts data before upload.
- Enable default bucket encryption for better security.
