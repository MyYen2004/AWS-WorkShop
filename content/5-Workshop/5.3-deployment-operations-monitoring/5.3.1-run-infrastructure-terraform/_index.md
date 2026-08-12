---
title: "Frontend Deployment with Amazon S3 and Amazon CloudFront"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 5.3.1 </b> "
aliases:
  - /5-workshop/5.3-deployment-operations-monitoring/5.3.1-vpc-network/
---

## 5.3.1 Frontend Deployment with Amazon S3 and Amazon CloudFront

### 1. Frontend Preparation

CloudMenu uses a frontend built with HTML, CSS, and JavaScript, including the following interfaces:

- Customer
- Order Status
- Kitchen
- Manager Dashboard

The frontend source code is managed on GitHub. Before deployment, the file structure and the API endpoints used by the frontend are checked.

### 2. Upload Frontend to Amazon S3

An Amazon S3 bucket is created to store the CloudMenu frontend files.

The HTML, CSS, JavaScript files, and static resources are manually uploaded to S3.

The deployment flow can be described as:

Developer → GitHub → Deploy/Upload → Amazon S3

![CloudMenu AWS architecture](/images/2.jpg)

Note: CloudMenu currently does not use an automated CI/CD process from GitHub to S3. The frontend is manually uploaded to Amazon S3.

### 3. Configure Amazon CloudFront

After the frontend is stored in S3, a CloudFront Distribution is created with Amazon S3 configured as the origin.

CloudFront is responsible for distributing the frontend files to users through the CDN.

Distribution flow:

Amazon S3 → Amazon CloudFront → Browser/Phone

### 4. Access CloudMenu

After the CloudFront Distribution is deployed, users can access CloudMenu through the CloudFront URL.

The different user groups can access their corresponding interfaces through:

Customer / Kitchen / Manager → Amazon CloudFront → Amazon S3

Customers can open the ordering interface on their phones after scanning the QR code assigned to their table.

### 5. Post-Deployment Testing

After deployment, the following items are checked:

- Verify that the CloudFront URL is accessible.
- Verify that the HTML, CSS, and JavaScript files load correctly.
- Verify that the Customer, Kitchen, and Manager interfaces work properly.
- Verify that the frontend can send requests to Amazon API Gateway.
- Check for CORS errors if the frontend cannot send requests to the API.