# Amazon S3 Static Website Hosting

## Learning Objectives

After completing this lesson, you will be able to:

- Understand Static Website Hosting.
- Host a website using Amazon S3.
- Configure Index and Error documents.
- Understand Website Endpoint vs REST API Endpoint.
- Configure Bucket Policy for public access.
- Understand security best practices.
- Answer common interview questions.

---

# What is Static Website Hosting?

Amazon S3 can host static websites.

A static website contains files like:

- HTML
- CSS
- JavaScript
- Images
- Fonts

No server-side code runs on S3.

Examples:

✅ Portfolio Website

✅ Company Website

✅ Landing Page

✅ Documentation Site

---

# Static Website vs Dynamic Website

## Static Website

Files are delivered exactly as stored.

```
Browser

↓

index.html

↓

Amazon S3
```

Examples:

- Portfolio
- Company profile
- Resume website

---

## Dynamic Website

A web server processes requests before sending a response.

```
Browser

↓

Web Server

↓

Application

↓

Database
```

Examples:

- Facebook
- Amazon Shopping
- Gmail

---

# Website Architecture

```
User

↓

Internet

↓

Amazon S3 Bucket

↓

index.html

style.css

logo.png

script.js
```

---

# Required Files

Example website:

```
website/

├── index.html
├── error.html
├── style.css
├── script.js
└── logo.png
```

---

# Enabling Static Website Hosting

Steps:

```
Amazon S3

↓

Bucket

↓

Properties

↓

Static Website Hosting

↓

Enable
```

Provide:

```
Index Document

index.html

Error Document

error.html
```

---

# Index Document

The default page shown when someone opens the website.

Example:

```
https://example-bucket.s3-website-region.amazonaws.com

↓

Loads

↓

index.html
```

---

# Error Document

Displayed when a requested page is not found.

Example:

```
User Requests

about.html

↓

Not Found

↓

error.html
```

---

# Website Endpoint

After enabling hosting, AWS provides a website endpoint.

Example:

```
http://my-website.s3-website-ap-south-1.amazonaws.com
```

Use this endpoint to access the website in a browser.

---

# Website Endpoint vs REST API Endpoint

Website Endpoint:

```
http://mybucket.s3-website-ap-south-1.amazonaws.com
```

Purpose:

- Static website hosting
- Supports index and error documents

---

REST API Endpoint:

```
https://mybucket.s3.ap-south-1.amazonaws.com
```

Purpose:

- Object access
- Applications
- SDKs
- APIs

---

# Public Access Requirements

A website must be publicly accessible.

To host a public website:

1. Disable Block Public Access (only for this bucket if appropriate).
2. Add a Bucket Policy allowing read access.
3. Upload website files.

Never use public access for sensitive data.

---

# Example Bucket Policy

Allow everyone to read website files.

```json
{
  "Version":"2012-10-17",
  "Statement":[
    {
      "Effect":"Allow",
      "Principal":"*",
      "Action":"s3:GetObject",
      "Resource":"arn:aws:s3:::my-static-site/*"
    }
  ]
}
```

---

# Upload Website Files

Example:

```
Bucket

my-static-site

│
├── index.html
├── style.css
├── app.js
├── images/
│      logo.png
└── error.html
```

---

# How Requests Work

```
User Opens Website

↓

Website Endpoint

↓

S3 Bucket

↓

index.html

↓

Displayed in Browser
```

---

# Real-World Example

Company:

ABC Technologies

Website:

```
abc-company-site

↓

index.html

↓

CSS

↓

JavaScript

↓

Images
```

Hosted entirely in Amazon S3.

---

# Advantages

✅ Very low cost

✅ Highly available

✅ Highly durable

✅ Easy to deploy

✅ No server management

✅ Automatically scalable

---

# Limitations

❌ Cannot run PHP

❌ Cannot run Java

❌ Cannot run Node.js

❌ Cannot connect directly to databases

❌ No server-side processing

For dynamic websites, use services like EC2, Elastic Beanstalk, ECS, or Lambda/API Gateway.

---

# Best Practices

✅ Enable Versioning.

✅ Enable Default Encryption.

✅ Keep backups.

✅ Use CloudFront for faster global delivery.

✅ Use HTTPS with CloudFront.

✅ Use a custom domain with Route 53.

---

# Common Mistakes

❌ Forgetting to upload index.html.

✔ Always specify the correct index document.

---

❌ Keeping Block Public Access enabled while expecting a public website.

✔ Configure public access only for the website bucket.

---

❌ Making unrelated buckets public.

✔ Only the website bucket should allow public read access.

---

# Interview Questions

## What is S3 Static Website Hosting?

A feature that allows Amazon S3 to host static websites containing HTML, CSS, JavaScript, and other static assets.

---

## Can S3 host dynamic websites?

No.

S3 only hosts static content.

---

## Which file is loaded first?

index.html

---

## Which file is shown when a page is missing?

error.html

---

## Which endpoint supports index and error documents?

The Website Endpoint.

---

## Is a Bucket Policy required?

Yes, for a public website you typically need a Bucket Policy that allows public read access, along with appropriate public access settings.

---

# Quick Revision

```
Upload Website

↓

Enable Website Hosting

↓

Set index.html

↓

Set error.html

↓

Public Read

↓

Website Endpoint

↓

Live Website
```

---

# Key Takeaways

- Amazon S3 can host static websites.
- Static websites contain HTML, CSS, JavaScript, images, and other static files.
- Configure index.html and error.html.
- Use the Website Endpoint for browser access.
- Configure Bucket Policies carefully.
- Use CloudFront and Route 53 for production deployments.
