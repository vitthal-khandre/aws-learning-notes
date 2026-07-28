# Service Models (IaaS, PaaS, SaaS)

## What are Service Models?

Cloud Service Models define **who manages what** between the cloud provider (such as AWS) and the customer.

There are three main service models:

1. IaaS (Infrastructure as a Service)
2. PaaS (Platform as a Service)
3. SaaS (Software as a Service)

---

# Overview

```
More Control  <------------------------------------------->  Less Control

IaaS                  PaaS                      SaaS
│                     │                         │
You manage            AWS manages more         Everything is managed
most things           You focus on code        Just use the software
```

---

# 1. Infrastructure as a Service (IaaS)

## Definition

IaaS provides virtual infrastructure over the Internet.

The cloud provider supplies:

- Virtual Machines
- Storage
- Networking
- Physical Servers

You are responsible for:

- Installing the Operating System
- Installing Applications
- Security Configuration
- Software Updates (inside the VM)

---

## Diagram

```
+----------------------+
| Applications         | ← You Manage
+----------------------+
| Operating System     | ← You Manage
+----------------------+
| Virtual Machine      | ← AWS
+----------------------+
| Storage              | ← AWS
+----------------------+
| Network              | ← AWS
+----------------------+
| Physical Hardware    | ← AWS
+----------------------+
```

---

## AWS Examples

- Amazon EC2
- Amazon EBS
- Amazon VPC

---

## Real-Life Example

Imagine renting an empty apartment.

The owner provides:

- Building
- Electricity
- Water

You bring:

- Furniture
- TV
- Bed
- Decorations

AWS provides the infrastructure.

You configure everything inside.

---

## Advantages

✅ Full control

✅ Flexible

✅ Easy to scale

---

## Disadvantages

❌ More administration

❌ Responsible for OS updates

❌ Requires technical knowledge

---

# 2. Platform as a Service (PaaS)

## Definition

PaaS provides a platform where developers can build, test, and deploy applications without managing servers.

AWS manages:

- Servers
- Operating System
- Runtime
- Networking

You manage:

- Application Code
- Data

---

## Diagram

```
+----------------------+
| Application Code     | ← You
+----------------------+
| Runtime              | ← AWS
+----------------------+
| Operating System     | ← AWS
+----------------------+
| Virtual Machine      | ← AWS
+----------------------+
| Storage              | ← AWS
+----------------------+
| Network              | ← AWS
+----------------------+
```

---

## AWS Examples

- AWS Elastic Beanstalk
- AWS App Runner

---

## Real-Life Example

Think of a fully equipped kitchen.

The kitchen already has:

- Stove
- Oven
- Gas
- Utensils

You only cook the food.

Similarly, PaaS lets developers focus only on writing code.

---

## Advantages

✅ Faster development

✅ No server management

✅ Automatic scaling

---

## Disadvantages

❌ Less control

❌ Platform limitations

---

# 3. Software as a Service (SaaS)

## Definition

SaaS delivers ready-to-use software over the Internet.

You simply sign in and use the application.

The provider manages everything.

---

## Diagram

```
+----------------------+
| Software             | ← Provider
+----------------------+
| Application          | ← Provider
+----------------------+
| Operating System     | ← Provider
+----------------------+
| Servers              | ← Provider
+----------------------+
| Network              | ← Provider
+----------------------+
```

You only use the software.

---

## Examples

- Gmail
- Microsoft 365
- Dropbox
- Zoom
- Salesforce

---

## Real-Life Example

Think of watching movies on Netflix.

You don't install or manage the servers.

You simply log in and watch.

---

## Advantages

✅ Easy to use

✅ No installation

✅ Automatic updates

✅ Accessible anywhere

---

## Disadvantages

❌ Limited customization

❌ Internet required

---

# Responsibility Comparison

| Component | IaaS | PaaS | SaaS |
|-----------|------|------|------|
| Applications | You | You | Provider |
| Data | You | You | Provider* |
| Runtime | You | Provider | Provider |
| Operating System | You | Provider | Provider |
| Virtual Machines | Provider | Provider | Provider |
| Storage | Provider | Provider | Provider |
| Networking | Provider | Provider | Provider |
| Physical Hardware | Provider | Provider | Provider |

> **Note:** In SaaS, while the provider operates the application and infrastructure, you are still responsible for the data you create and how you use the service (for example, managing user access and protecting your account).

---

# AWS Examples

| AWS Service | Model |
|-------------|-------|
| Amazon EC2 | IaaS |
| Amazon EBS | IaaS |
| Amazon VPC | IaaS |
| AWS Elastic Beanstalk | PaaS |
| AWS App Runner | PaaS |

---

# Everyday Examples

| Service | Model |
|----------|-------|
| Gmail | SaaS |
| Microsoft 365 | SaaS |
| Dropbox | SaaS |
| Zoom | SaaS |

---

# Easy Way to Remember

## IaaS

Rent an empty house.

You arrange everything inside.

---

## PaaS

Rent a fully equipped kitchen.

You only cook.

---

## SaaS

Eat in a restaurant.

Everything is prepared.

You simply enjoy the meal.

---

# Interview Questions

## What is IaaS?

Infrastructure as a Service provides virtual infrastructure such as servers, storage, and networking. The customer manages the operating system and applications.

---

## What is PaaS?

Platform as a Service provides a managed platform where developers can build and deploy applications without managing servers.

---

## What is SaaS?

Software as a Service provides ready-to-use software over the Internet without requiring installation or infrastructure management.

---

## Which AWS service is an example of IaaS?

Amazon EC2.

---

## Which AWS service is an example of PaaS?

AWS Elastic Beanstalk.

---

## Is Gmail IaaS, PaaS, or SaaS?

Gmail is SaaS.

---

# Quick Revision

✅ IaaS → Infrastructure (Virtual Machines)

✅ PaaS → Platform (Develop Applications)

✅ SaaS → Ready-to-use Software

---

# Key Takeaways

- IaaS gives you the most control and responsibility.
- PaaS lets developers focus on code instead of infrastructure.
- SaaS is the easiest to use because everything is managed by the provider.
- AWS offers services in different models depending on your needs.
