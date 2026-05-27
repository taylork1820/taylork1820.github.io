# Project 2 — Static Website with CI/CD Pipeline

**Status:** ⏳ Coming soon  
**Estimated AWS cost:** $0 (free tier)  
**Time to build:** ~2 hours  

---

## Business Problem

Every business needs a fast, reliable website. Manually uploading files to a web server every time something changes is slow, error-prone, and unscalable. A CI/CD pipeline automates this — every time a change is pushed to GitHub, the website updates automatically within seconds.

For a Solutions Architect, this demonstrates knowledge of content delivery, HTTPS, and automation patterns. For a Technical Account Manager, it covers the services most commonly used by customers hosting static websites, marketing pages, and documentation sites.

---

## Architecture

![Architecture Diagram](architecture-diagram.png)
*(diagram to be added)*

### Services used and why

| Service | Role | Why this service |
|---------|------|-----------------|
| S3 | Stores the website files | Durable, cheap, designed for static file hosting |
| CloudFront | Delivers the site globally with low latency | CDN — serves files from the nearest edge location to the visitor |
| ACM | Provides free HTTPS certificate | Free, auto-renews, integrates directly with CloudFront |
| Route 53 | Custom domain DNS | AWS-native DNS, easy to connect to CloudFront |
| GitHub Actions | CI/CD pipeline — auto-deploys on push | Free, widely used, no extra AWS service needed |

---

## How It Works

1. A change is pushed to GitHub
2. GitHub Actions detects the push and runs the pipeline
3. Pipeline syncs the updated files to the S3 bucket
4. Pipeline invalidates the CloudFront cache so visitors see the new version immediately
5. Visitors worldwide get the site served from their nearest CloudFront edge location over HTTPS

---

## Screenshots

*(to be added during build)*

---

## SAA-C03 Exam Topics This Covers

- S3 static website hosting and bucket policies
- CloudFront distributions, origins, and cache behaviors
- ACM certificate provisioning and DNS validation
- Route 53 alias records
- CI/CD concepts and automation

---

## What I Learned

*(to be filled in after completing the project)*

---

## What I Would Improve

*(to be filled in after completing the project)*

---

## Tear-Down Checklist

- [ ] CloudFront distribution disabled and deleted
- [ ] S3 bucket emptied and deleted
- [ ] ACM certificate deleted
- [ ] Route 53 records deleted (if custom domain used)
- [ ] Confirmed $0 bill in Cost Explorer
