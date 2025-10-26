Personal Portfolio Website - Fully Automated Deployment on AWS

This project hosts my personal portfolio website on AWS using a fully automated, scalable, and secure cloud architecture.  
The infrastructure is defined using AWS CloudFormation, which allows the entire environment to be created and updated everything from the code.

---

🚀 Architecture Overview

The website is stored in an Amazon S3 bucket and delivered globally through Amazon CloudFront.  
A custom domain is configured using Amazon Route 53, and HTTPS encryption is provided through AWS Certificate Manager.

🧰 Technologies & AWS Services Used

Service / Technology | Purpose 
------------------------------
- Amazon S3 | Stores static website assets (HTML, CSS, JS, images) |
- Amazon CloudFront | CDN for caching and global low-latency delivery |
- Amazon Route 53 | DNS routing for custom domain and subdomain |
- AWS Certificate Manager | Provides SSL/TLS certificate for HTTPS |
- AWS CodeBuild | Automates deployment triggered by GitHub commits |
- IAM Roles & Policies | Secure permissions for deployment and CDN invalidation |
- CloudWatch Logs | Build logs |
- AWS CloudFormation | Infrastructure as Code |
- GitHub Webhooks | CI/CD integration to trigger code changes in repository |

🔄 CI/CD Workflow

1. Pushing new code to the main branch on GitHub.
2. A webhook triggers AWS CodeBuild.
3. CodeBuild pulls the repo and uploads the updated files to the S3 bucket.
4. CodeBuild automatically triggers a CloudFront cache invalidation so updates are visible immediately.
5. Website updates go live.

🌍 Domain & SSL Configuration

- The domain `jakub-grzelak.com` and subdomain `www.jakub-grzelak.com` are managed in Route 53.
- Both domain versions point to the same CloudFront distribution.
- An ACM certificate provides secure HTTPS encryption.

📦 CloudFormation Highlights

The stack includes:

- S3 bucket for main site
- Optional subdomain redirect bucket
- CloudFront distribution configured with:
  a) SSL certificate
  b) Custom domain aliases
  c) Cache policies for optimized performance
- DNS records in Route 53.
- CodeBuild project and IAM role for automated deployment
