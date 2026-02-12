# Cloud Resume Project – AWS Deployment

## Overview

This project is a fully deployed static resume website hosted on AWS using production-level cloud architecture.  
It demonstrates cloud infrastructure deployment, DNS configuration, SSL implementation, CDN integration, and IAM security best practices.

Live Site: https://usmanaws.com

---

## Technologies Used

- HTML
- CSS
- JavaScript
- Amazon S3 (Static Website Hosting)
- Amazon Route 53 (DNS Management)
- AWS Certificate Manager (SSL/TLS)
- Amazon CloudFront (CDN + HTTPS)
- AWS IAM (Security Best Practices)

---

## Architecture

User → Route 53 → CloudFront (HTTPS + CDN) → S3 (Static Website Hosting)

---

## Implementation Steps

### 1. Designed and Developed Resume Website (Frontend)

- Built a responsive single-page resume website using HTML, CSS, and JavaScript.
- Implemented an interactive employment timeline using JavaScript.
- Structured project files into:
  - `index.html`
  - `styles.css`
  - `script.js`
  - image assets
- Tested locally in the browser before deployment.

---

### 2. Implemented Secure AWS Access Controls

- Created and used an IAM user instead of the root account.
- Applied appropriate permissions for S3, Route 53, ACM, and CloudFront.
- Followed AWS security best practices for least privilege access.

---

### 3. Deployed Website to Amazon S3

- Created an S3 bucket named `usmanaws.com`.
- Enabled Static Website Hosting.
- Set `index.html` as the default document.
- Uploaded all website files.
- Configured bucket policy to allow public read access.

Result: Website accessible via S3 website endpoint.

---

### 4. Registered Custom Domain Using Route 53

- Registered domain `usmanaws.com`.
- Created a Public Hosted Zone.
- Created an A Record with Alias.
- Initially routed traffic to the S3 website endpoint.

Result: Domain resolved to hosted website.

---

### 5. Secured Website with SSL Using AWS Certificate Manager (ACM)

- Requested public SSL certificate for:
  - `usmanaws.com`
  - `www.usmanaws.com`
- Used DNS validation method.
- Validated certificate through Route 53.
- Ensured certificate was created in `us-east-1` (required for CloudFront).
- Waited until certificate status was **Issued**.

---

### 6. Configured CloudFront Distribution

- Created a CloudFront distribution.
- Set S3 website endpoint as origin.
- Added Alternate Domain Name (CNAME): `usmanaws.com`.
- Attached ACM SSL certificate.
- Enabled "Redirect HTTP to HTTPS."
- Allowed CloudFront to update S3 bucket policy for secure origin access.

Result: Website secured with HTTPS and optimized with CDN performance.

---

### 7. Updated Route 53 to Route Traffic Through CloudFront

- Modified Route 53 A Record.
- Updated Alias target from S3 endpoint to CloudFront distribution.
- Confirmed DNS propagation.
- Verified secure HTTPS access.

---

## Final Outcome

- Custom domain configuration
- HTTPS secured via SSL certificate
- CDN-enabled performance using CloudFront
- Static hosting via S3
- DNS routing via Route 53
- IAM security best practices
- Production-style cloud architecture

---

## Why This Project Matters

This project demonstrates:

- Cloud infrastructure deployment
- DNS and domain management
- SSL certificate integration
- CDN configuration
- Secure AWS account management
- End-to-end cloud architecture design

