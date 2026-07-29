# Multi-Factor Authentication (MFA)

## Learning Objectives

After completing this lesson, you will be able to:

- Understand what Multi-Factor Authentication (MFA) is.
- Learn why MFA is important.
- Understand the different MFA methods supported by AWS.
- Enable MFA for the Root User and IAM Users.
- Follow AWS MFA best practices.

---

# What is Multi-Factor Authentication (MFA)?

Multi-Factor Authentication (MFA) is a security feature that requires **two or more forms of verification** before access is granted.

Instead of logging in with only a password, AWS requires an additional verification factor.

It answers the question:

> "Can you prove it's really you?"

---

# Why Do We Need MFA?

A password alone is not always secure.

If someone steals your password, they could sign in to your AWS account.

With MFA enabled:

- The attacker knows your password.
- But they **do not have** your MFA device.

Result:

❌ Login is denied.

---

# Authentication Factors

Authentication can use one or more of these factors.

### 1. Something You Know

Examples:

- Password
- PIN

---

### 2. Something You Have

Examples:

- Mobile phone
- Hardware security key
- Authenticator app

---

### 3. Something You Are

Examples:

- Fingerprint
- Face recognition
- Iris scan

AWS IAM primarily uses:

- Password (Something you know)
- Authenticator app or hardware security key (Something you have)

---

# How MFA Works

```
User

↓

Enter Username

↓

Enter Password

↓

Enter MFA Code

↓

AWS Verifies

↓

Access Granted
```

Without the correct MFA code, access is denied.

---

# Types of MFA Supported by AWS

AWS supports several MFA methods.

## 1. Virtual MFA Device (Most Common)

Examples:

- Google Authenticator
- Microsoft Authenticator
- Authy

Advantages:

- Free
- Easy to configure
- Recommended for most users

---

## 2. Hardware Security Key

Examples:

- YubiKey
- FIDO2 Security Keys

Advantages:

- Strong security
- Resistant to phishing
- Commonly used in enterprises

---

## 3. Hardware OTP Token

A physical device that generates one-time passwords.

Used mainly in organizations with specific compliance requirements.

---

# MFA Login Flow

```
Username

↓

Password

↓

MFA Code

↓

AWS

↓

Access
```

---

# Enable MFA for the Root User

AWS strongly recommends enabling MFA immediately after creating an AWS account.

Steps:

1. Sign in as the Root User.
2. Open **IAM**.
3. Choose **Dashboard**.
4. Under **Security recommendations**, select **Add MFA**.
5. Choose a Virtual MFA Device or Hardware Security Key.
6. Scan the QR code using your authenticator app.
7. Enter two consecutive MFA codes.
8. Complete the setup.

---

# Enable MFA for an IAM User

Steps:

1. Sign in as an IAM Administrator User.
2. Open **IAM → Users**.
3. Select the user.
4. Open the **Security credentials** tab.
5. Click **Assign MFA device**.
6. Choose the MFA device type.
7. Complete the setup.

---

# Real-World Example

Imagine an ATM.

To withdraw money, you need:

- ATM Card
- PIN

If someone steals your PIN but doesn't have your card, they cannot withdraw money.

AWS MFA works the same way.

```
Password

+

MFA Device

=

Secure Login
```

---

# Benefits of MFA

✅ Protects against stolen passwords.

✅ Reduces the risk of unauthorized access.

✅ Improves account security.

✅ Recommended by AWS for all users.

---

# Best Practices

✅ Enable MFA for the Root User immediately.

✅ Enable MFA for IAM Users, especially administrators.

✅ Use a trusted authenticator app or hardware security key.

✅ Store recovery information securely.

✅ Remove MFA devices from inactive users.

---

# Common Mistakes

❌ Using only a password.

✔ Enable MFA.

---

❌ Enabling MFA only for IAM Users.

✔ Protect the Root User too.

---

❌ Sharing MFA devices.

✔ Each user should have their own MFA device.

---

❌ Ignoring lost device recovery.

✔ Keep backup and recovery options updated.

---

# Real AWS Example

```
AWS Account

↓

IAM User

↓

Username

↓

Password

↓

Authenticator App

↓

6-Digit Code

↓

AWS

↓

Access Granted
```

---

# Interview Questions

## What is MFA?

MFA (Multi-Factor Authentication) is a security mechanism that requires more than one authentication factor before granting access.

---

## Why should MFA be enabled?

To protect AWS accounts even if a password is compromised.

---

## Which AWS users should have MFA enabled?

- Root User
- IAM Administrator Users
- Ideally, all IAM Users

---

## Name two Virtual MFA applications.

- Google Authenticator
- Microsoft Authenticator
- Authy

---

## Is MFA part of Authentication or Authorization?

Authentication.

It verifies the user's identity.

---

# Quick Revision

```
Username

↓

Password

↓

MFA Code

↓

Access
```

---

# Key Takeaways

- MFA adds an extra layer of security.
- AWS recommends enabling MFA for the Root User immediately.
- MFA protects against stolen passwords.
- Virtual MFA devices are the most common option.
- MFA is part of Authentication, not Authorization.
