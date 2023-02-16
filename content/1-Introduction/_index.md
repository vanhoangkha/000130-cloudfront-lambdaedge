---
title : "Introduction"
date : "`r Sys.Date()`"
weight : 1
chapter : false
pre : " <b> 1. </b> "
---

#### Introduce

#### Overview
Amazon CloudFront is the static and dynamic content delivery service of Amazon Web Services (AWS). With the ability to increase the speed and stability of your web applications, Amazon CloudFront provides a temporary storage solution for your content on Amazon Edge servers.

Amazon CloudFront is customizable and flexible allowing you to configure features such as **EC2** and **S3 Origins**, **CloudFront Distribution**, **Custom Error Page**, Origin Group, Response Headers, create new cache behavior, create Lambda@Edge function and deploy Lambda@Edge function to CloudFront. This increases content availability and reduces response times.

In addition, Amazon CloudFront provides features that monitor and analyze the performance of content delivered through this service. By logging in to S3 and using tools like Amazon Athena and Amazon Redshift, you can easily monitor and analyze the performance of your assets.

To help you better understand Amazon CloudFront, let's look at some of its features and usage:

1. **EC2 and S3 Origins**: Amazon CloudFront allows you to connect content from EC2 or S3. This increases the speed and reduces the response time of your web application.

2. **CloudFront Distribution**: To use Amazon CloudFront, you need to create a distribution. Distribution is a collection of Amazon's Edge servers, on which your content is temporarily stored.

3. **Custom Error Page**: You can customize your error page to be compatible with your website.

4. **Origin Group**: If you have multiple Origin servers, you can configure them into a group. CloudFront will automatically switch to other servers in the pool if the origin server crashes.

5. **Response Headers**: You can configure HTTP response headers to customize client requests.

6. **Create a new cache behavior**: If you want to create a new cache behavior, you need to configure its features on the origin server or by using Lambda@Edge.

7. **Create Lambda@Edge function**: If you want to process a CloudFront request, you can use the Lambda@Edge function.

8. **Deploy Lambda@Edge to CloudFront**: You can deploy your Lambda@Edge function to CloudFront using the AWS CLI.

9. **Metrics and Logs**: Amazon CloudFront provides features to monitor and analyze the performance of content delivered through this service. By logging in to S3 and using tools like Amazon Athena and Amazon Redshift, you can easily monitor and analyze the performance of your assets.

As such, Amazon CloudFront is a great service to increase the speed and stability of your web application. With its features and strengths, Amazon CloudFront is a reliable and flexible content delivery solution.

#### Best practice

To get the most out of Amazon CloudFront's potential, there are a few best practices that you should follow:

- Use S3 Bucket or EC2 Instance as Origin: Using S3 Bucket or EC2 Instance as Origin for your CloudFront Distribution will increase response speed and reduce bandwidth costs.

- Use SSL/TLS Encryption: Use SSL/TLS Encryption to protect data in transit between Origin and Edge Locations. You can use a free or paid SSL certificate to ensure the security of your data.

- Use Compression: Use compression in CloudFront Distribution to reduce file size and speed up page loading.

- Use CloudFront Behaviors: Create CloudFront Behaviors to customize how CloudFront handles requests. For example, you can create a cache behavior to optimize performance for GET or HEAD requests.

- Use Caching: Use the caching feature in CloudFront to reduce page load times and reduce bandwidth costs. You can configure the cache to cache resources temporarily and reduce the number of requests to the origin.

- Use Lambda@Edge: Use Lambda@Edge to customize and process customer requests on CloudFront. Lambda@Edge provides the ability to add, modify, or remove HTTP headers or resources on your site.

- Use AWS WAF: Use AWS WAF to protect your applications on CloudFront. AWS WAF provides security policies, filters, and access management for your applications.

- Use CloudFront Logs: Use the logging feature in CloudFront to monitor and analyze the performance of your delivered assets. You can use data analytics tools, like Amazon Athena or Amazon Redshift, to analyze logs and make smart business decisions.