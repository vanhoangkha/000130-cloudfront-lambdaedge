---
title : "Preparation steps"
date : "`r Sys.Date()`"
weight : 2
chapter : false
pre : " <b> 2. </b> "
---

#### Preparation steps

To get the most out of Amazon CloudFront, you need to create origins for your content. These origins will contain data and are used by CloudFront to deliver content to end users. The two primary origins for use with Amazon CloudFront are Amazon S3 (Simple Storage Service) and Amazon EC2 (Elastic Compute Cloud).

- **Amazon S3 (Simple Storage Service)**: If you are using Amazon S3 to store content, you can create an S3 bucket as the origin for CloudFront. An S3 bucket is a simple storage space for storing objects such as images, videos, or documents. After creating an S3 bucket, you can inject objects into it and use this S3 bucket as the origin for CloudFront.

- **Amazon EC2 (Elastic Compute Cloud)**: If you are using Amazon EC2 to run your application, you can create an EC2 instance as the origin for CloudFront. An EC2 instance is a virtual machine running on Amazon's cloud platform. After creating an EC2 instance, you can install and configure your application on it, and then use this EC2 instance as the origin for CloudFront.

Originating your content is essential to using Amazon CloudFront effectively. If you are using Amazon S3 or Amazon EC2, it is very simple to create an origin for CloudFront. Using these sources makes it possible to quickly and securely distribute your content.

#### Content

1. [Create EC2](2.1-createec2/)
2. [Create S3](2.2-creates3/)