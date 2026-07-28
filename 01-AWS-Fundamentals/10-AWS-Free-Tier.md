# AWS Free Tier

## Learning Objectives

After completing this lesson, you will be able to:

- Understand what the AWS Free Tier is.
- Learn the different types of AWS Free Tier offers.
- Know which popular AWS services are included.
- Avoid unexpected AWS charges.

---

# What is the AWS Free Tier?

The AWS Free Tier allows you to use selected AWS services **free of charge**, within specific usage limits.

It is designed for:

- Beginners learning AWS
- Students
- Developers
- Testing applications
- Hands-on practice

> **Important:** Free does **not** mean unlimited. If you exceed the free limits, AWS will charge you according to its pricing.

---

# Types of AWS Free Tier

AWS offers three types of Free Tier benefits.

## 1. Free Trials

Some services are free for a limited period after you start using them.

Example:

- 30 days
- 60 days

---

## 2. 12-Month Free Tier

Some services are free for the first **12 months** after creating a new AWS account, up to specific monthly limits.

Examples include:

- Amazon EC2 (selected instance types)
- Amazon S3
- Amazon RDS

---

## 3. Always Free

Some AWS services include a free monthly allowance that does not expire, although usage limits still apply.

Examples:

- AWS Lambda
- Amazon DynamoDB (limited usage)
- Amazon CloudWatch (limited usage)

---

# Popular AWS Free Tier Services

| Service | Example Free Tier Benefit* |
|----------|----------------------------|
| Amazon EC2 | Limited monthly usage of eligible instance types |
| Amazon S3 | Limited storage and requests |
| Amazon RDS | Limited database usage |
| AWS Lambda | Monthly free request and compute allowance |
| Amazon DynamoDB | Limited monthly capacity and storage |
| Amazon CloudWatch | Limited monitoring and logs |

> *Benefits and limits can change. Always check the official AWS Free Tier page.

---

# Example

Suppose you create:

- 1 EC2 instance
- 1 S3 bucket
- 1 RDS database

If all of them stay **within the Free Tier limits**, your cost can be **$0**.

If you exceed those limits:

```
Within Limit

Cost = $0

------------

Above Limit

Pay only for the additional usage
```

---

# Real-Life Example

Imagine your electricity company gives you:

- 100 free units every month.

If you use:

80 units

You pay:

$0

If you use:

120 units

You pay only for the extra 20 units.

AWS Free Tier works in a similar way.

---

# Common Mistakes

## Mistake 1

❌ Leaving EC2 instances running when you are not using them.

✔ Stop or terminate resources you no longer need.

---

## Mistake 2

❌ Forgetting to delete unused EBS volumes.

✔ Delete unused storage to avoid charges.

---

## Mistake 3

❌ Creating unsupported instance types.

✔ Verify that the service or instance type is eligible for the Free Tier.

---

## Mistake 4

❌ Forgetting about snapshots and backups.

✔ Snapshots, backups, and additional storage may incur charges if they exceed Free Tier limits.

---

# Best Practices

✅ Use only eligible Free Tier services.

✅ Delete unused resources.

✅ Monitor your usage regularly.

✅ Set up billing alerts.

✅ Review your monthly billing dashboard.

---

# AWS Billing Dashboard

AWS provides tools to monitor costs.

Useful services include:

- AWS Billing Dashboard
- AWS Cost Explorer
- AWS Budgets

These tools help you:

- View current charges
- Track spending trends
- Set budget alerts
- Identify unexpected costs

---

# How to Avoid Charges

1. Stop or terminate unused EC2 instances.
2. Delete unused EBS volumes and snapshots.
3. Remove unused S3 buckets and objects.
4. Use only Free Tier eligible services.
5. Check the Billing Dashboard regularly.
6. Create an AWS Budget with alerts.

---

# Interview Questions

## What is the AWS Free Tier?

The AWS Free Tier allows eligible customers to use selected AWS services within defined usage limits at no cost.

---

## Is the AWS Free Tier unlimited?

No.

It has usage limits, and exceeding them results in charges.

---

## Name three AWS services commonly included in the Free Tier.

- Amazon EC2
- Amazon S3
- Amazon RDS

---

## How can you avoid unexpected AWS charges?

- Monitor usage.
- Delete unused resources.
- Configure billing alerts.
- Stay within Free Tier limits.

---

# Quick Revision

```
AWS Free Tier

↓

Learn AWS

↓

Stay within usage limits

↓

Cost = $0

↓

Exceed limits

↓

Additional charges apply
```

---

# Key Takeaways

- The AWS Free Tier is designed for learning and testing.
- It includes Free Trials, 12-Month Free Tier offers, and Always Free services.
- Staying within usage limits helps avoid charges.
- Billing tools such as AWS Cost Explorer and AWS Budgets help you monitor spending.
- Always clean up resources after completing your practice.
