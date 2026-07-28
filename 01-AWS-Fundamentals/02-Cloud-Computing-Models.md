# Cloud Computing Models

Cloud computing models describe **how cloud infrastructure is deployed and who owns it**.

There are four main cloud deployment models:

1. Public Cloud
2. Private Cloud
3. Hybrid Cloud
4. Multi-Cloud

---

# 1. Public Cloud

## Definition

A Public Cloud is owned and managed by a cloud provider. The infrastructure is shared among multiple customers, but each customer's data remains isolated and secure.

Examples of public cloud providers:

- Amazon Web Services (AWS)
- Microsoft Azure
- Google Cloud Platform (GCP)

---

## Diagram

```
                Internet
                     │
        +--------------------------+
        |      AWS Cloud           |
        |                          |
        | Customer A               |
        | Customer B               |
        | Customer C               |
        +--------------------------+
```

All customers use AWS's infrastructure.

---

## Characteristics

- No hardware to purchase
- Pay only for what you use
- Highly scalable
- Available worldwide
- Managed by the cloud provider

---

## Advantages

✅ Low cost

✅ Easy to start

✅ No maintenance

✅ High availability

✅ Automatic updates

---

## Disadvantages

❌ Less control over physical hardware

❌ Internet connection required

---

## Real Example

A startup launches its website on AWS.

They do not own any servers.

AWS owns and manages everything.

---

# 2. Private Cloud

## Definition

A Private Cloud is dedicated to a single organization.

Only one company uses the infrastructure.

It may be located:

- Inside the company (On-Premises)
- Hosted by a cloud provider

---

## Diagram

```
           Company

        +----------------+
        | Private Cloud  |
        |                |
        | Only Company   |
        | Uses It        |
        +----------------+
```

No other customers share the infrastructure.

---

## Characteristics

- Dedicated resources
- More control
- Better customization
- Higher security
- Higher cost

---

## Advantages

✅ Full control

✅ Better security

✅ Meets compliance requirements

---

## Disadvantages

❌ Expensive

❌ Hardware maintenance

❌ Requires IT staff

---

## Real Example

A bank stores customer financial data in its own private cloud because of strict security requirements.

---

# 3. Hybrid Cloud

## Definition

Hybrid Cloud combines:

- Private Cloud
- Public Cloud

Both environments work together.

---

## Diagram

```
          Company

      +----------------+
      | Private Cloud  |
      +----------------+
              │
      Secure Connection
              │
              ▼
      +----------------+
      | AWS Public     |
      | Cloud          |
      +----------------+
```

---

## Characteristics

- Sensitive data stays private
- Public cloud handles extra workload
- Flexible
- Cost-effective

---

## Advantages

✅ Best of both worlds

✅ Better disaster recovery

✅ Easy scaling

---

## Disadvantages

❌ More complex

❌ Network configuration required

---

## Real Example

A hospital stores patient records in a private cloud.

Its public website runs on AWS.

---

# 4. Multi-Cloud

## Definition

Multi-Cloud means using cloud services from **more than one cloud provider**.

Example:

- AWS
- Azure
- Google Cloud

All are used together.

---

## Diagram

```
          Company

        /     |      \

      AWS   Azure    GCP
```

---

## Why Use Multi-Cloud?

- Avoid vendor lock-in
- Better reliability
- Choose the best service from each provider

---

## Advantages

✅ High availability

✅ Flexibility

✅ Reduced dependency on one provider

---

## Disadvantages

❌ Complex management

❌ Requires multiple skills

---

## Real Example

A company uses:

- AWS for EC2
- Azure for Active Directory
- Google Cloud for Machine Learning

This is Multi-Cloud.

---

# Comparison Table

| Feature | Public | Private | Hybrid | Multi-Cloud |
|----------|---------|----------|---------|-------------|
| Owner | Cloud Provider | Company | Both | Multiple Providers |
| Cost | Low | High | Medium | Medium to High |
| Security | High | Very High | Very High | Depends |
| Scalability | Excellent | Limited | Excellent | Excellent |
| Maintenance | Provider | Company | Shared | Shared |
| Example | AWS | Company Data Center | AWS + Company DC | AWS + Azure |

---

# Easy Way to Remember

## Public Cloud

"My house is rented."

You use someone else's infrastructure.

Example:

AWS

---

## Private Cloud

"My own house."

Only your company uses it.

---

## Hybrid Cloud

"Home + Hotel"

Some work stays at home.

Some work goes to the hotel.

---

## Multi-Cloud

"Staying in multiple hotels."

Use AWS, Azure, and Google Cloud together.

---

# Interview Questions

## What is Public Cloud?

A cloud environment owned and managed by a cloud provider where multiple customers share infrastructure securely.

---

## What is Private Cloud?

A cloud environment dedicated to a single organization.

---

## What is Hybrid Cloud?

A combination of public cloud and private cloud working together.

---

## What is Multi-Cloud?

Using services from multiple cloud providers like AWS, Azure, and Google Cloud.

---

# Quick Revision

✅ Public Cloud → Everyone shares the provider's infrastructure.

✅ Private Cloud → Only one company uses the infrastructure.

✅ Hybrid Cloud → Public + Private.

✅ Multi-Cloud → AWS + Azure + Google Cloud.

---

# Key Takeaways

- Public Cloud = Best for startups and most businesses.
- Private Cloud = Best for highly sensitive data.
- Hybrid Cloud = Mix of public and private.
- Multi-Cloud = Multiple cloud providers.
- AWS is a Public Cloud provider.
