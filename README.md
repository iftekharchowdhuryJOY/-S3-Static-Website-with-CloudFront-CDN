# S3-Static-Website-with-CloudFront-CDN
# 🌍 AWS Project – S3 Static Website with CloudFront CDN

## 🧠 Overview
This project hosts a **static website** on **Amazon S3** and distributes it globally using **Amazon CloudFront**.  
It’s part of my **“30 Days of AWS Projects”** challenge — one project every day to master AWS.

---

## 🎯 Goal
- Deploy a website using **S3 Static Website Hosting**
- Speed it up using **CloudFront CDN**
- Serve the site securely over **HTTPS**
- Understand **costs** and **optimizations**

---

## 🧱 AWS Services Used
| Service | Purpose |
|----------|----------|
| **Amazon S3** | Stores website files (HTML, CSS, JS) |
| **Amazon CloudFront** | CDN to cache and serve content globally |
| **IAM** | Controls permissions and bucket access |

---

## 🪄 Steps to Deploy

### 1️⃣ Create an S3 Bucket
1. Go to **S3 Console → Create bucket**
2. Name: `joy-static-site-demo` *(must be globally unique)*
3. Uncheck **Block all public access**
4. Create bucket

### 2️⃣ Upload Website Files
Upload files such as:
```plaintext
index.html
style.css

Example index.html:
<html>
  <head><title>AWS S3 + CloudFront Demo</title></head>
  <body style="text-align:center;font-family:sans-serif;">
    <h1>🚀 Hosted on AWS S3 + CloudFront</h1>
    <p>Part of my 30 Days AWS Projects Challenge</p>
  </body>
</html>
3️⃣ Enable Static Website Hosting

Go to Properties → Static website hosting

Enable hosting

Set Index document to index.html

Copy your S3 website endpoint, e.g.

http://joy-static-site-demo.s3-website.ca-central-1.amazonaws.com/

4️⃣ Add Bucket Policy for Public Read

Go to Permissions → Bucket policy, paste:

{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicReadGetObject",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::joy-static-site-demo/*"
    }
  ]
}

5️⃣ Create CloudFront Distribution

Go to CloudFront → Create distribution

Origin domain: your S3 website endpoint
Example: joy-static-site-demo.s3-website.ca-central-1.amazonaws.com

Origin protocol policy: HTTP only

Distribution type: Single website or app

Create distribution

Wait for status = ✅ Deployed

Open CloudFront URL:

https://dxxxxx.cloudfront.net

6️⃣ (Optional) Invalidate Cache

To refresh updates:

CloudFront → Invalidations → Create invalidation → /*

🧩 Architecture

User → CloudFront (CDN) → S3 Bucket (Static Website)

💰 Cost & Optimization
Service	Free Tier	Est. Monthly Cost	Notes
S3	✅ 5 GB free + 20k GET requests	$0 – $0.50	Use small files
CloudFront	✅ 1 TB data transfer out (12 months)	$0 – $1	Delete after testing
IAM	✅ Always free	-	-
Total (approx)		$0 – $1/month	
Cost Tips			- Delete CloudFront after testing
- Don’t store large files
- Use .jpg for images
✅ Learning Outcomes

How S3 static hosting works

How to integrate CloudFront for HTTPS + CDN caching

How to configure permissions and bucket policies

How to manage cost-efficient hosting on AWS

🧹 Cleanup

To avoid charges:

Delete CloudFront distribution

Delete S3 bucket and objects

💼 Author

👨‍💻 Iftekhar Joy
AWS + DevOps + AI Engineer
Project 1 of 30 in my “30 Days of AWS Projects” Challenge













