# Project 1 — Serverless URL Shortener

**Status:** 🔄 In progress  
**Estimated AWS cost:** $0 (free tier)  
**Time to build:** ~2 hours  

---

## Business Problem

Long URLs are difficult to share, track, and manage. A URL shortener solves this by mapping a short, memorable code to any long URL — and redirecting visitors automatically. This is the same problem solved by services like Bitly and TinyURL.

For a Solutions Architect, this project demonstrates the ability to design a serverless, scalable, low-cost solution to a real business need. For a Technical Account Manager, it demonstrates hands-on familiarity with the core serverless services most commonly used by AWS customers.

---

## Architecture

![Architecture Diagram](architecture-diagram.png)
*(diagram to be added)*

### Services used and why

| Service | Role | Why this service |
|---------|------|-----------------|
| API Gateway | Receives incoming HTTP requests from the internet | Managed, serverless, scales automatically — no web server to maintain |
| Lambda | Runs the redirect logic | No server to manage, pay only per request, integrates natively with API Gateway |
| DynamoDB | Stores short code → long URL mappings | Serverless NoSQL, single-digit millisecond reads, no capacity to manage on free tier |
| IAM | Controls what Lambda is allowed to access | Least-privilege security — Lambda can only read/write its own DynamoDB table |
| CloudWatch | Logs, metrics, and alarms | Visibility into errors, latency, and invocation count without any extra tooling |

---

## How It Works

1. A user visits a short URL (e.g. `https://[api-id].execute-api.us-east-1.amazonaws.com/prod/abc123`)
2. API Gateway receives the request and triggers the Lambda function
3. Lambda looks up `abc123` in the DynamoDB table
4. If found, Lambda returns an HTTP 301 redirect to the original long URL
5. If not found, Lambda returns a 404 response
6. CloudWatch logs every invocation automatically

---

## Screenshots

### DynamoDB table
*(screenshot to be added)*

### Lambda function configuration
*(screenshot to be added)*

### API Gateway endpoint
*(screenshot to be added)*

### Successful redirect in browser
*(screenshot to be added)*

### CloudWatch logs showing invocation
*(screenshot to be added)*

### CloudWatch alarm configured on errors
*(screenshot to be added)*

### IAM role with least-privilege policy
*(screenshot to be added)*

---

## SAA-C03 Exam Topics This Covers

- Serverless architecture patterns (Lambda + API Gateway)
- NoSQL database design (DynamoDB partition keys)
- Least-privilege IAM roles and policies
- CloudWatch Logs, Metrics, and Alarms
- Event-driven compute

---

## What I Learned

*(to be filled in after completing the project)*

---

## What I Would Improve

*(to be filled in after completing the project — this section matters to interviewers)*

Examples to consider:
- Add a custom domain with Route 53 and ACM
- Add a front-end form so users can create short URLs without touching the console
- Add click tracking (store a count in DynamoDB each time a short URL is used)
- Add TTL (time-to-live) to DynamoDB items so short URLs expire automatically

---

## Tear-Down Checklist

Services deleted after documentation to avoid charges:

- [ ] Lambda function deleted
- [ ] API Gateway deleted
- [ ] DynamoDB table deleted
- [ ] CloudWatch alarms deleted
- [ ] IAM role deleted
- [ ] Confirmed $0 bill in Cost Explorer
