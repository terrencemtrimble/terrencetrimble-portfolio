terrencetrimble.com — Portfolio Website
Live at terrencetrimble.com
A serverless, globally distributed portfolio website built on AWS. Automatically deploys on every push via GitHub Actions CI/CD pipeline.

Architecture
GitHub → GitHub Actions → S3 (Origin) → CloudFront (CDN) → Route 53 (DNS)
ServiceRoleAmazon S3Private object storage for static site filesAmazon CloudFrontGlobal CDN with HTTPS, edge caching, and Origin Access ControlAWS Certificate ManagerFree SSL/TLS certificate for HTTPSAmazon Route 53DNS routing from custom domain to CloudFrontGitHub ActionsCI/CD pipeline — auto-deploys on push to master

Features

Serverless — no web servers to manage or patch
Global edge delivery — CloudFront serves content from 400+ edge locations worldwide
HTTPS enforced — HTTP requests automatically redirected to HTTPS
Private S3 bucket — Origin Access Control (OAC) ensures S3 is never publicly accessible
Automated deployments — push to GitHub, site updates within seconds
~$2/month — cost-optimized for static hosting


CI/CD Pipeline
Every push to the master branch triggers a GitHub Actions workflow that:

Checks out the latest code
Authenticates with AWS using IAM credentials stored as GitHub Secrets
Syncs index.html to the S3 bucket
Creates a CloudFront cache invalidation so changes go live immediately

yamlon:
  push:
    branches:
      - master

Security

S3 bucket is fully private — no public access
CloudFront accesses S3 via Origin Access Control (OAC) — the modern replacement for OAI
HTTPS enforced via TLS 1.2 minimum security policy
AWS credentials stored as GitHub Secrets — never exposed in code
IAM user follows least privilege principle — scoped to S3 and CloudFront only


Project Structure
terrencetrimble-portfolio/
├── index.html              # Portfolio site (HTML/CSS/JS)
└── .github/
    └── workflows/
        └── deploy.yml      # GitHub Actions CI/CD pipeline

Skills Demonstrated
AWS S3 CloudFront Route 53 ACM IAM GitHub Actions CI/CD DNS HTTPS OAC Serverless
