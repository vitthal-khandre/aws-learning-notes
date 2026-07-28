# AWS Global Infrastructure

## What is AWS Global Infrastructure?

AWS Global Infrastructure is the worldwide network of data centers and networking that AWS uses to deliver cloud services.

It is designed to provide:

- High Availability
- Low Latency
- Fault Tolerance
- Scalability
- Disaster Recovery

AWS has data centers around the world so customers can run applications close to their users.

---

# Components of AWS Global Infrastructure

AWS Global Infrastructure consists of:

1. Regions
2. Availability Zones (AZs)
3. Local Zones
4. Edge Locations
5. Regional Edge Caches

```
                    AWS Global Infrastructure

                             AWS
                              │
        ┌─────────────────────┼─────────────────────┐
        │                     │                     │
    Region A              Region B             Region C
        │                     │                     │
   ┌────┴────┐           ┌────┴────┐          ┌────┴────┐
   │         │           │         │          │         │
  AZ-1     AZ-2        AZ-1      AZ-2       AZ-1     AZ-2
```

---

# What is a Region?

A Region is a **geographical area** where AWS has multiple data centers.

Examples:

- Mumbai
- Singapore
- Tokyo
- Frankfurt
- London
- Ohio

Each Region is completely independent.

---

## Why are Regions important?

- Lower latency
- Compliance requirements
- Disaster recovery
- Data residency

Example:

If your users are in India,

choose **Mumbai Region** instead of **London Region** for better performance.

---

# Example

```
India Users
      │
      ▼
AWS Mumbai Region

instead of

India Users
      │
      ▼
AWS London Region
```

Mumbai provides lower network latency.

---

# What is an Availability Zone (AZ)?

An Availability Zone is one or more data centers inside a Region.

Each Region contains multiple AZs.

Example:

Mumbai Region

```
ap-south-1

├── ap-south-1a
├── ap-south-1b
├── ap-south-1c
```

Each AZ has:

- Independent power
- Independent cooling
- Independent networking

---

# Why Multiple Availability Zones?

Suppose your application runs only in AZ-A.

```
EC2
 │
AZ-A
```

If AZ-A fails,

your application becomes unavailable.

Now imagine this:

```
EC2
 │
AZ-A

EC2
 │
AZ-B
```

If AZ-A fails,

AZ-B continues serving users.

This provides **High Availability**.

---

# What is a Local Zone?

A Local Zone extends AWS services closer to users in a metropolitan area.

Purpose:

- Lower latency
- Better performance for local applications

Examples:

- Video editing
- Gaming
- Real-time applications

---

# What is an Edge Location?

Edge Locations are used by AWS services such as:

- Amazon CloudFront
- AWS WAF
- AWS Shield
- Route 53

They cache content closer to users.

Example:

Without CloudFront

```
User (Delhi)
      │
      ▼
Mumbai Region
```

With CloudFront

```
User (Delhi)
      │
      ▼
Delhi Edge Location

      │
      ▼
Mumbai Region
```

The user gets faster access because content is served from the nearest Edge Location.

---

# Regional Edge Cache

A Regional Edge Cache sits between the Region and Edge Locations.

Purpose:

- Reduce requests to the Region
- Improve content delivery
- Increase cache efficiency

```
User
 │
 ▼
Edge Location
 │
 ▼
Regional Edge Cache
 │
 ▼
AWS Region
```

---

# Real-World Example

Suppose you create a website hosted on Amazon EC2 in the Mumbai Region.

Users:

- Mumbai
- Delhi
- Chennai
- Hyderabad

Without CloudFront:

All requests go directly to Mumbai.

With CloudFront:

Users receive cached content from the nearest Edge Location.

The website loads faster.

---

# Region vs Availability Zone

| Region | Availability Zone |
|---------|-------------------|
| Geographic location | Data center(s) inside a Region |
| Independent from other Regions | Connected with other AZs in the same Region |
| Example: Mumbai | Example: ap-south-1a |

---

# Why Doesn't AWS Use Only One Data Center?

If a single data center has:

- Power failure
- Fire
- Flood
- Network outage

Everything would stop.

Using multiple AZs prevents a single point of failure.

---

# Best Practices

✅ Deploy applications in multiple Availability Zones.

✅ Choose the Region closest to your users.

✅ Use CloudFront for global users.

✅ Keep backups in another Region for disaster recovery.

---

# Interview Questions

## What is an AWS Region?

A Region is a geographical area where AWS operates multiple Availability Zones.

---

## What is an Availability Zone?

An Availability Zone is one or more physically separate data centers within a Region.

---

## Why should applications use multiple Availability Zones?

To improve High Availability and Fault Tolerance.

---

## What is an Edge Location?

An Edge Location caches content closer to users to reduce latency.

---

## Which AWS service uses Edge Locations?

Amazon CloudFront.

---

# Quick Revision

✅ Region = Geographic area.

✅ Availability Zone = Data center(s) inside a Region.

✅ Multiple AZs = High Availability.

✅ Edge Location = Faster content delivery.

✅ Local Zone = AWS services closer to cities.

---

# Key Takeaways

- AWS has a global network of Regions and Availability Zones.
- Each Region contains multiple AZs.
- Applications should be deployed across multiple AZs for high availability.
- Edge Locations improve performance by serving cached content closer to users.
- Choosing the right Region helps reduce latency and meet compliance requirements.
