---
title: cloud resources
publishDate: "2025-04-23T13:00:00Z"
updateDate: "2025-04-23T14:32:00Z"
---

## Why Use Cloud?
- Cloud services (AWS, GCP, Azure) let companies manage their systems from anywhere.
- They provide a centralized environment for operations.

## Vulnerabilities in the Cloud
- Even though providers secure the infrastructure, **misconfigurations** by admins can expose resources.
- **Common risk areas**:
  - **AWS**: S3 buckets
  - **Azure**: blobs
  - **GCP**: cloud storage
- If not set up properly, these can be accessed **without authentication**.

## Company Hosted Servers
- DNS records often include internal tools and cloud storage for easy access.
- Example: S3 bucket linked to domain: `s3-website-us-west-2.amazonaws.com`.

## Finding Cloud Resources
- Use **Google Dorks** like `inurl:` and `intext:` to find exposed documents or files.
- Example file types: PDFs, presentations, code, etc.

## Tools & Platforms
- **Domain.glass**: Reveals infrastructure details, DNS info.
- **GrayHatWarfare**: Search public cloud storage files by name, format, or company.

## Security Risks
- Leaked **SSH private keys** can give attackers direct server access.
- Always handle credentials carefully.

---

We should always validate cloud configurations and monitor public exposure regularly. 
