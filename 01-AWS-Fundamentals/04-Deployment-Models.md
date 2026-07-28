# Deployment Models

## What are Deployment Models?

A deployment model describes **where your applications and data are hosted**.

It helps organizations decide where to run their workloads based on cost, security, compliance, and business requirements.

The four common deployment models are:

1. On-Premises
2. Cloud
3. Hybrid
4. Multi-Cloud

---

# Overview

```
Your Application

        │
        ▼

+--------------------+
| Deployment Model   |
+--------------------+
| On-Premises        |
| Cloud              |
| Hybrid             |
| Multi-Cloud        |
+--------------------+
```

---

# 1. On-Premises

## Definition

On-Premises means all IT infrastructure is located inside your own organization.

The company purchases, owns, and manages:

- Servers
- Storage
- Networking
- Power
- Cooling
- Security

---

## Diagram

```
        Company Office

+----------------------------+
| Server Room                |
|                            |
|  Server                    |
|  Storage                   |
|  Firewall                  |
|  Network Switch            |
|                            |
+----------------------------+
```

Everything belongs to the company.

---

## Characteristics

- Complete control
- High security
- Company manages everything
- Large upfront investment

---

## Advantages

✅ Full control

✅ Data stays within the company

✅ Can work without Internet for internal systems

---

## Disadvantages

❌ Expensive

❌ Hardware maintenance

❌ Limited scalability

❌ Disaster recovery is more difficult

---

## Real Example

A manufacturing company hosts its ERP system in its own data center.

---

# 2. Cloud Deployment

## Definition

Cloud Deployment means applications run on infrastructure provided by a cloud provider like AWS.

The cloud provider owns and manages the physical infrastructure.

---

## Diagram

```
      Internet
          │
          ▼
+-----------------------+
| AWS Cloud             |
|                       |
| EC2                   |
| S3                    |
| RDS                   |
+-----------------------+
```

---

## Characteristics

- No physical servers to buy
- Pay-as-you-go pricing
- Highly scalable
- Global availability

---

## Advantages

✅ Lower upfront cost

✅ Fast deployment

✅ Easy scaling

✅ High availability

---

## Disadvantages

❌ Internet dependency

❌ Less control over physical hardware

---

## Real Example

A startup hosts its website on Amazon EC2.

---

# 3. Hybrid Deployment

## Definition

Hybrid Deployment combines On-Premises infrastructure with Cloud infrastructure.

Some workloads stay in the company while others run in the cloud.

---

## Diagram

```
     Company Office

+-------------------+
| Local Servers     |
+-------------------+
         │
 Secure Connection
         │
         ▼
+-------------------+
| AWS Cloud         |
| EC2               |
| S3                |
+-------------------+
```

---

## Characteristics

- Mix of local and cloud resources
- Flexible
- Good for gradual cloud migration

---

## Advantages

✅ Better flexibility

✅ Easier migration

✅ Sensitive data stays on-premises

✅ Cloud handles extra workloads

---

## Disadvantages

❌ More complex networking

❌ Requires management of two environments

---

## Real Example

A hospital keeps patient records on-premises but stores backups in Amazon S3.

---

# 4. Multi-Cloud Deployment

## Definition

Multi-Cloud means using services from multiple cloud providers.

Example:

- AWS
- Microsoft Azure
- Google Cloud Platform

---

## Diagram

```
          Company

        /    |    \

      AWS  Azure  GCP
```

---

## Characteristics

- Uses multiple cloud vendors
- Avoids dependence on one provider
- Allows choosing the best service from each provider

---

## Advantages

✅ High availability

✅ Flexibility

✅ Reduced vendor lock-in

---

## Disadvantages

❌ More complex management

❌ Different tools and billing systems

---

## Real Example

A company uses:

- AWS for virtual servers
- Azure for identity management
- Google Cloud for AI services

---

# Comparison Table

| Feature | On-Premises | Cloud | Hybrid | Multi-Cloud |
|----------|-------------|--------|---------|-------------|
| Infrastructure Owner | Company | Cloud Provider | Both | Multiple Providers |
| Initial Cost | High | Low | Medium | Medium |
| Maintenance | Company | Provider | Shared | Shared |
| Scalability | Limited | Excellent | Excellent | Excellent |
| Internet Required | Not always | Yes | Usually | Yes |
| Flexibility | Low | High | Very High | Very High |

---

# Deployment Model vs Cloud Model

Many beginners confuse these terms.

| Cloud Model | Deployment Model |
|-------------|------------------|
| Describes who owns the cloud infrastructure (Public, Private, Hybrid, Multi-Cloud) | Describes where your application runs (On-Premises, Cloud, Hybrid, Multi-Cloud) |

Example:

- AWS is a **Public Cloud**.
- Your website running on AWS is a **Cloud Deployment**.

---

# Real-World Example

Imagine your company has:

- Employee Management System
- Company Website
- Database
- Backup Server

### Option 1: On-Premises

Everything runs inside the office.

### Option 2: Cloud

Everything runs on AWS.

### Option 3: Hybrid

Employee database stays on-premises.

Website runs on AWS.

### Option 4: Multi-Cloud

Website runs on AWS.

Authentication uses Azure.

AI features use Google Cloud.

---

# Easy Way to Remember

## On-Premises

"My own house."

Everything belongs to me.

---

## Cloud

"Rent a furnished apartment."

The provider owns the building.

---

## Hybrid

"I live in my house but also rent an apartment."

Use both together.

---

## Multi-Cloud

"I rent apartments from different companies."

Use AWS, Azure, and Google Cloud.

---

# Interview Questions

## What is On-Premises Deployment?

Running applications on infrastructure owned and managed by the organization.

---

## What is Cloud Deployment?

Running applications on cloud infrastructure managed by a cloud provider like AWS.

---

## What is Hybrid Deployment?

A combination of on-premises infrastructure and cloud infrastructure.

---

## What is Multi-Cloud Deployment?

Using multiple cloud providers for different workloads or services.

---

## Why do companies choose Hybrid Deployment?

- Keep sensitive data on-premises
- Use cloud for scalability
- Support gradual migration to the cloud

---

# Quick Revision

✅ On-Premises → Everything in your own data center.

✅ Cloud → Everything runs on AWS or another cloud provider.

✅ Hybrid → Mix of on-premises and cloud.

✅ Multi-Cloud → Multiple cloud providers.

---

# Key Takeaways

- Deployment models define **where applications are deployed**.
- On-Premises offers maximum control but higher costs.
- Cloud provides scalability and lower upfront costs.
- Hybrid is ideal for gradual migration and sensitive workloads.
- Multi-Cloud improves flexibility and reduces dependence on a single provider.
