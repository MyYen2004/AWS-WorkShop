---
title : "Frontend Hosting & Content Delivery"
date : 2024-01-01
weight : 1
chapter : false
pre : " <b> 5.2.1 </b> "
---

## 5.2.1 Frontend Hosting & Content Delivery

CloudMenu uses Amazon S3 to store frontend files built with HTML, CSS, and JavaScript. The frontend includes interfaces for Customer, Kitchen, and Manager.

Amazon CloudFront is used to distribute frontend files from Amazon S3 to users through a CDN, allowing the CloudMenu interfaces to be accessed over the Internet through CloudFront.

- Amazon S3

Amazon S3 serves as the storage layer for the CloudMenu frontend and its static resources. The frontend files are uploaded to S3 for deployment.

- Amazon CloudFront

Amazon CloudFront serves as the content delivery layer in front of Amazon S3. Users access CloudMenu through CloudFront rather than directly accessing S3.

- Frontend Deployment Flow

The frontend source code is managed on GitHub and is currently uploaded manually to Amazon S3. Amazon CloudFront then uses S3 as the content origin to distribute the frontend to users.

- Deployment Flow

Developer → GitHub → Deploy/Upload → Amazon S3 → Amazon CloudFront → Browser/Phone

- User Access Flow

Customer / Kitchen / Manager → Amazon CloudFront → Amazon S3

