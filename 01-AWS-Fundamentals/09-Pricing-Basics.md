# AWS Pricing Basics

## Learning Objectives

After completing this lesson, you will be able to:

- Understand how AWS pricing works.
- Learn the AWS Pay-as-You-Go model.
- Understand common pricing models.
- Learn how to reduce AWS costs.
- Understand the AWS pricing tools.

---

# What is AWS Pricing?

AWS follows a **Pay-as-You-Go** pricing model.

This means:

> You pay **only for the AWS resources you actually use.**

Unlike buying your own servers, you don't pay a large upfront cost.

---

# Traditional IT vs AWS

## Traditional IT

```
Buy Server

↓

Pay Full Cost

↓

Maintain Hardware

↓

Upgrade Hardware

↓

Replace Hardware
```

You invest money before you even start.

---

## AWS Cloud

```
Launch EC2

↓

Use It

↓

Pay Only for Usage

↓

Stop Using

↓

Stop Paying
```

No large upfront investment.

---

# Pay-as-You-Go

Imagine taking a taxi.

You pay based on:

- Distance
- Time

Not for buying the taxi.

AWS works the same way.

Example:

You run an EC2 instance for **10 hours**.

You pay only for those **10 hours** (or according to the service's current billing model).

---

# Main AWS Pricing Principles

AWS pricing is based on three ideas.

## 1. Pay for What You Use

Only pay while the resource is being used.

Example:

```
EC2 Running

↓

Charges Apply

EC2 Terminated

↓

No EC2 Compute Charges
```

---

## 2. Save When Usage Increases

Some AWS services offer lower costs when you commit to longer-term or higher-volume usage.

Examples:

- Savings Plans
- Reserved Instances
- Volume discounts for some services

---

## 3. Stop Paying When You Stop Using

Delete unused resources.

Example:

Unused:

- EC2
- EBS Volumes
- Elastic IPs
- Load Balancers

may continue to generate charges if they are still allocated or stored.

---

# Common AWS Pricing Models

## 1. On-Demand Pricing

Best for:

- Beginners
- Testing
- Short-term projects

Characteristics:

- No long-term commitment
- Pay only for actual usage
- Flexible

Example:

Create an EC2 instance today.

Delete it tomorrow.

Only pay for the time it was running (based on the applicable pricing model).

---

## 2. Reserved Instances (RI)

Best for:

- Predictable workloads
- Long-running applications

Characteristics:

- Commit for 1 or 3 years
- Lower cost than On-Demand
- Less flexible

Example:

A company runs the same database server every day for several years.

---

## 3. Savings Plans

Best for:

- Regular AWS usage

Characteristics:

- Commit to a consistent amount of usage over time
- Can provide savings compared to On-Demand pricing
- More flexible than Reserved Instances for many workloads

---

## 4. Spot Instances

Best for:

- Batch jobs
- Testing
- Data processing
- Fault-tolerant workloads

Characteristics:

- Can be significantly cheaper than On-Demand
- AWS can interrupt the instance if capacity is needed elsewhere

Example:

Video rendering or scientific processing that can restart if interrupted.

---

# Pricing Example

Imagine an EC2 server.

```
Start Server

↓

Use for Project

↓

Stop or Terminate

↓

Charges stop for compute
```

If you leave attached storage or other resources allocated, those may still incur charges.

---

# AWS Cost Management Tools

## AWS Pricing Calculator

Estimate costs before creating resources.

Useful for:

- Planning projects
- Budget estimation

---

## AWS Cost Explorer

Analyze:

- Current costs
- Historical usage
- Spending trends

---

## AWS Budgets

Create monthly budgets.

Example:

Budget:

```
$20 per month
```

If your spending reaches your chosen threshold,

AWS can notify you.

---

## AWS Billing Dashboard

Shows:

- Current charges
- Bills
- Usage
- Payment history

---

# Tips to Save Money

✅ Stop unused EC2 instances.

✅ Delete unused EBS volumes.

✅ Remove unused snapshots.

✅ Delete unused Elastic IPs.

✅ Use the Free Tier when eligible.

✅ Use AWS Budgets.

✅ Choose the correct EC2 instance size.

---

# Real-World Example

A startup hosts its website.

Resources:

- 1 EC2
- 1 RDS
- 1 S3 Bucket

Instead of buying servers,

they pay only for what they use each month.

As traffic grows,

they can increase resources.

---

# Interview Questions

## What pricing model does AWS use?

AWS uses a Pay-as-You-Go pricing model.

---

## What is an On-Demand Instance?

An EC2 instance with no long-term commitment.

You pay based on usage.

---

## What are Spot Instances?

Instances that use spare AWS capacity at a lower price but can be interrupted.

---

## What is AWS Cost Explorer?

A tool for analyzing AWS costs and usage.

---

## What is AWS Budgets?

A service that helps monitor spending and alerts you when you approach or exceed your budget.

---

# Quick Revision

```
AWS Pricing

↓

Pay-as-You-Go

↓

Only Pay for What You Use

↓

Delete Unused Resources

↓

Save Money
```

---

# Comparison Table

| Pricing Model | Best For | Cost | Flexibility |
|---------------|----------|------|-------------|
| On-Demand | Testing, Short Projects | Highest | High |
| Reserved Instances | Long-Term Workloads | Lower | Medium |
| Savings Plans | Predictable Usage | Lower | High |
| Spot Instances | Batch Jobs | Lowest | Low |

---

# Key Takeaways

- AWS uses a Pay-as-You-Go pricing model.
- You pay only for the resources you use.
- Different pricing models suit different workloads.
- AWS provides tools to estimate and monitor costs.
- Regularly clean up unused resources to avoid unnecessary charges.
