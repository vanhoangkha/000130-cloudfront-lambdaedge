---
title : "Create CloudFront Distribution"
date : "`r Sys.Date()`"
weight : 3
chapter : false
pre : " <b> 3. </b> "
---

#### Create CloudFront Distribution

1. Go to CloudFront on the AWS console and click Create a CloudFront Distribution.

![Create CloudFront Distribution](/images/3/0001.png?featherlight=false&width=90pc)

2. Configure the default source for the previously created S3 bucket and grant CloudFront access to the bucket using the Origin Access Identity setup:

   - Origin domain > Select your S3 bucket
   - Access S3 bucket > Yes using OAI (bucket can limit access only to CloudFront)

![Create CloudFront Distribution](/images/3/0002.png?featherlight=false&width=90pc)

3. Origin access identity

   - Click Create new OAI


![Create CloudFront Distribution](/images/3/0003.png?featherlight=false&width=90pc)

4. - In the displayed dialog, click Create

![Create CloudFront Distribution](/images/3/0004.png?featherlight=false&width=90pc)

5. Policy bucket > Yes, update the bucket policy

![Create CloudFront Distribution](/images/3/0005.png?featherlight=false&width=90pc)

6. Configure the Default Cache Behavior as follows:

   - View protocol policy > Redirect HTTP to HTTPS.

![Create CloudFront Distribution](/images/3/0006.png?featherlight=false&width=90pc)

7. Cache key and origin requests

   - Cache policy and origin request policy (recommended)
   - Cache policy > CachingOptimized (Recommended for S3 source)
   CloudFront provides a set of managed cache policies that you can attach to any cache behavior of your distribution. With a managed cache policy, you don't need to write or maintain your own cache policy. Management policies use settings optimized for specific use cases.

![Create CloudFront Distribution](/images/3/0007.png?featherlight=false&width=90pc)

8. In the Settings section:

   - In this lab you will use a domain name provided by CloudFront, however, if you want to use your own domain name, you can configure it with Alternate Domain Names , you can add a new entry in the section Alternate domain name (CNAME) - optional.
   - Configure the Default root object - optionally index.html- And leave all remaining values ​​as default


![Create CloudFront Distribution](/images/3/0008.png?featherlight=false&width=90pc)

9. Click Create distribution

![Create CloudFront Distribution](/images/3/0009.png?featherlight=false&width=90pc)

10. Create a successful CloudFront distribution.

![Create CloudFront Distribution](/images/3/00010.png?featherlight=false&width=90pc)

11. CloudFront starts creating the distribution and it usually takes 5 to 10 minutes to fully deliver. The status of the delivery will be In Progress.

    - To check the status, you can click on the Distribution menu on the left sidebar.

![Create CloudFront Distribution](/images/3/00011.png?featherlight=false&width=90pc)