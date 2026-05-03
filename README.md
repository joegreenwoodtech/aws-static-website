# Static Website on AWS S3 + CloudFront

A personal portfolio website deployed to AWS using S3 for storage and CloudFront as a CDN for fast, secure global HTTPS delivery.

## Live Demo

[View Live Website](https://d3uwqyk78lbrx7.cloudfront.net)

## Architecture

User → CloudFront (CDN) → S3 Bucket (Static Files)

## AWS Services Used

- **Amazon S3** — Stores and serves the static website files. Configured as the origin for CloudFront.
- **Amazon CloudFront** — CDN that delivers content globally with low latency and HTTPS.
- **AWS IAM** — Manages permissions and access control. Origin Access Control restricts S3 bucket access to CloudFront only; direct S3 URLs are not publicly accessible.
- **Bucket Policies** — Configured to deny public access and only permit reads from the CloudFront distribution.

## Features

- Served over HTTPS via CloudFront
- Global content delivery via AWS edge locations
- Custom error page (404)
- Bucket policy restricting direct S3 access

## Project Structure

- `index.html` — Main portfolio page
- `style.css` — Stylesheet
- `error.html` — Custom 404 error page
- `README.md` — Project documentation

## Deployment Steps

1. Created S3 bucket with static website hosting enabled
2. Applied bucket policy for public read access
3. Uploaded website files to S3
4. Created CloudFront distribution pointing to S3 origin
5. Configured HTTPS and HTTP to HTTPS redirect

### CI/CD Automation

Deployment was later automated via GitHub Actions in a companion project: **[aws-cicd-pipeline](https://github.com/joegreenwoodtech/aws-cicd-pipeline)**. The CI/CD pipeline syncs site updates to S3 and invalidates the CloudFront cache on every push to main, completing full deployment in under 15 seconds.

## Related Projects

Part of a four-project AWS portfolio:

- 📦 **[aws-static-website](https://github.com/joegreenwoodtech/aws-static-website)** *(this repo)* — S3 + CloudFront static hosting
- 🚀 **[aws-cicd-pipeline](https://github.com/joegreenwoodtech/aws-cicd-pipeline)** — GitHub Actions automation for this site
- 🌐 **[aws-ec2-rds-webapp](https://github.com/joegreenwoodtech/aws-ec2-rds-webapp)** — 3-tier web application on EC2 + RDS
- 🏗️ **[terraform-vpc-ec2](https://github.com/joegreenwoodtech/terraform-vpc-ec2)** — Reusable VPC + EC2 module in Terraform

## Author

**Joe Greenwood**
AWS Cloud Practitioner
[GitHub](https://github.com/joegreenwoodtech)
