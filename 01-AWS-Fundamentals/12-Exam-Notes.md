# AWS Fundamentals - Exam Notes

> 📌 Last Updated:
>
> AWS Fundamentals Revision Notes

---

# 1. What is Cloud Computing?

Cloud Computing is the delivery of IT resources over the Internet instead of owning physical infrastructure.

Examples:

- Servers
- Storage
- Databases
- Networking
- Software

### Benefits

- Pay-as-You-Go
- Scalability
- High Availability
- Global Access
- Security

---

# 2. Cloud Deployment Models

## Public Cloud

Infrastructure owned by AWS.

Example:

- AWS
- Azure
- Google Cloud

---

## Private Cloud

Infrastructure dedicated to one organization.

Example:

Company Data Center

---

## Hybrid Cloud

Combination of:

- Public Cloud
- Private Cloud

---

## Multi-Cloud

Using multiple cloud providers.

Example:

AWS + Azure + Google Cloud

---

# 3. Service Models

## IaaS

Infrastructure as a Service

Examples:

- Amazon EC2
- Amazon EBS
- Amazon VPC

Customer manages:

- OS
- Applications
- Data

---

## PaaS

Platform as a Service

Examples:

- AWS Elastic Beanstalk
- AWS App Runner

Customer manages:

- Application
- Data

---

## SaaS

Software as a Service

Examples:

- Gmail
- Microsoft 365
- Zoom

Customer only uses the software.

---

# 4. AWS Global Infrastructure

AWS consists of:

- Regions
- Availability Zones
- Local Zones
- Edge Locations
- Regional Edge Caches

---

# 5. Region

A Region is a geographic location.

Example:

Mumbai

```
ap-south-1
```

---

# 6. Availability Zone (AZ)

One or more physically separate data centers inside a Region.

Example:

```
ap-south-1a

ap-south-1b

ap-south-1c
```

Purpose:

High Availability

---

# 7. Edge Location

Used for caching content closer to users.

Main Service:

Amazon CloudFront

Purpose:

Lower Latency

---

# 8. Shared Responsibility Model

AWS

↓

Security **OF** the Cloud

Customer

↓

Security **IN** the Cloud

AWS manages:

- Hardware
- Networking
- Data Centers

Customer manages:

- IAM
- Passwords
- Applications
- Data
- Operating System (EC2)

---

# 9. Well-Architected Framework

Six Pillars

1. Operational Excellence
2. Security
3. Reliability
4. Performance Efficiency
5. Cost Optimization
6. Sustainability

Memory Trick:

```
OSRPCS
```

---

# 10. AWS Free Tier

Types:

- Free Trial
- 12-Month Free Tier
- Always Free

Remember:

Free ≠ Unlimited

---

# 11. AWS Pricing

Pricing Models

- On-Demand
- Reserved Instances
- Savings Plans
- Spot Instances

Memory Trick

```
On-Demand

↓

Reserved

↓

Savings

↓

Spot
```

---

# Important AWS Services Learned

| Service | Purpose |
|----------|----------|
| EC2 | Virtual Server |
| S3 | Object Storage |
| EBS | Block Storage |
| VPC | Private Network |
| CloudFront | CDN |
| IAM | Identity & Access |
| RDS | Managed Database |
| CloudWatch | Monitoring |
| Route 53 | DNS |
| AWS Budgets | Cost Alerts |

---

# Frequently Asked Interview Questions

### What is Cloud Computing?

Delivery of IT resources over the Internet.

---

### What is AWS?

Amazon Web Services is Amazon's cloud computing platform.

---

### Difference between Region and AZ?

Region

↓

Geographic Location

AZ

↓

Data Center(s)

---

### Which AWS service delivers content faster?

Amazon CloudFront

---

### Which AWS service launches virtual servers?

Amazon EC2

---

### Which AWS service stores files?

Amazon S3

---

### What does IAM do?

Manages users, groups, roles, and permissions.

---

### What is the Shared Responsibility Model?

AWS secures the cloud.

Customer secures resources inside the cloud.

---

### Which pricing model is cheapest?

Spot Instances

(Only for workloads that can tolerate interruptions.)

---

# Common Exam Questions

| Question | Answer |
|-----------|--------|
| What is a Region? | Geographic location |
| What is an AZ? | One or more data centers inside a Region |
| Which service uses Edge Locations? | CloudFront |
| Which service creates virtual machines? | EC2 |
| Which service stores objects? | S3 |
| Which service manages users? | IAM |
| What is CDN? | Content Delivery Network |
| What is High Availability? | Multiple AZ deployment |
| What is Pay-as-You-Go? | Pay only for what you use |
| What is IaaS? | Infrastructure as a Service |

---

# Memory Tricks

### Cloud Models

```
Public

Private

Hybrid

Multi
```

---

### Service Models

```
IaaS

PaaS

SaaS
```

---

### Six Pillars

```
OSRPCS

Operational Excellence

Security

Reliability

Performance

Cost

Sustainability
```

---

### Pricing Models

```
On-Demand

Reserved

Savings

Spot
```

---

### Shared Responsibility

```
AWS

↓

Security OF the Cloud

Customer

↓

Security IN the Cloud
```

---

# Final Revision Checklist

✅ I know what Cloud Computing is.

✅ I understand Public, Private, Hybrid, and Multi-Cloud.

✅ I know IaaS, PaaS, and SaaS.

✅ I understand AWS Regions and Availability Zones.

✅ I know what Edge Locations are.

✅ I understand the Shared Responsibility Model.

✅ I know all six Well-Architected Framework pillars.

✅ I understand AWS Free Tier.

✅ I know the four AWS pricing models.

✅ I can explain EC2, S3, IAM, VPC, CloudFront, Route 53, CloudWatch, and RDS.

---

# Congratulations!

🎉 You have completed the **AWS Fundamentals** section.

You are now ready to start learning AWS services in depth.

## Next Learning Path

```
01-AWS-Fundamentals ✅
        │
        ▼
02-IAM (Identity and Access Management)
        │
        ▼
03-EC2 (Elastic Compute Cloud)
        │
        ▼
04-S3 (Simple Storage Service)
        │
        ▼
05-VPC (Virtual Private Cloud)
        │
        ▼
06-EBS & EFS
        │
        ▼
07-RDS
        │
        ▼
08-Load Balancer & Auto Scaling
        │
        ▼
09-CloudWatch & CloudTrail
        │
        ▼
10-Route 53
        │
        ▼
11-Elastic Beanstalk
        │
        ▼
12-Lambda
```

> 🎯 **Recommended:** Before moving to IAM, create a **Free Tier AWS account** and practice each service as you learn it. Reading + hands-on practice is the fastest way to build real AWS skills.
