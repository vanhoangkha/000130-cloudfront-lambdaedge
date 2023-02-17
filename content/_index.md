---
title : "AWS CloudFront Workshop"
date : "`r Sys.Date()`"
weight : 1
chapter : false
---

# AWS CloudFront Workshop

#### Overview
**Amazon CloudFront** is the static and dynamic content delivery service of Amazon Web Services (AWS). With the ability to increase the speed and stability of your web applications, **Amazon CloudFront** provides a temporary storage solution for your content on Amazon Edge servers.

![CloudFront Lab](/images/11/00012.png?featherlight=false&width=90pc)

**Amazon CloudFront** is customizable and flexible allowing you to configure features such as **EC2** and **S3 Origins**, **CloudFront Distribution**, **Custom Error Page**, Origin Group, Response Headers, create new cache behavior, create Lambda@Edge function and deploy Lambda@Edge function to CloudFront. This increases content availability and reduces response times.

In addition, **Amazon CloudFront** provides features that monitor and analyze the performance of content delivered through this service. By logging in to S3 and using tools like Amazon Athena and Amazon Redshift, you can easily monitor and analyze the performance of your assets.

To help you better understand **Amazon CloudFront**, let's look at some of its features and usage:

1. **EC2 and S3 Origins**: **Amazon CloudFront** allows you to connect content from EC2 or S3. This increases the speed and reduces the response time of your web application.

2. **CloudFront Distribution**: To use **Amazon CloudFront**, you need to create a distribution. Distribution is a collection of Amazon's Edge servers, on which your content is temporarily stored.

3. **Custom Error Page**: You can customize your error page to be compatible with your website.

4. **Origin Group**: If you have multiple Origin servers, you can configure them into a group. CloudFront will automatically switch to other servers in the pool if the origin server crashes.

5. **Response Headers**: You can configure HTTP response headers to customize client requests.

6. **Create a new cache behavior**: If you want to create a new cache behavior, you need to configure its features on the origin server or by using Lambda@Edge.

7. **Create Lambda@Edge function**: If you want to process a CloudFront request, you can use the Lambda@Edge function.

8. **Deploy Lambda@Edge to CloudFront**: You can deploy your Lambda@Edge function to CloudFront using the AWS CLI.

9. **Metrics and Logs**: **Amazon CloudFront** provides features to monitor and analyze the performance of content delivered through this service. By logging in to S3 and using tools like Amazon Athena and Amazon Redshift, you can easily monitor and analyze the performance of your assets.

As such, **Amazon CloudFront** is a great service to increase the speed and stability of your web application. With its features and strengths, **Amazon CloudFront** is a reliable and flexible content delivery solution.

#### Content:

1. [Introduction](1-introduction/)
2. [Preparation steps](2-preparation/)
3. [Create CloudFront Distribution](3-create-cloudfront-distribution/)
4. [Check Distribution Invalidations](4-distribution-invalidations/)
5. [Custom Configuration Error Page](5-custom-error-page/)
6. [Configure Origin Group](6-origin-group/)
7. [Response Headers](7-response-headers/)
8. [Create Cache Behavior](8-cache-behavior/)
9. [Create Lambda@Edge function](9-lambdaedge-function/)
10. [Deploy Lambda@Edge function to CloudFront](10-deploy-lambdaedge-function/)
11. [Metrics and Logs](11-metrics-and-logs/)
12. [Resource Cleanup](12-cleanup/)