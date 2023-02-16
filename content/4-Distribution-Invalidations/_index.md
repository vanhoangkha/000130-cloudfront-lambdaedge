---
title : "Test Distribution Invalidations"
date : "`r Sys.Date()`"
weight : 4
chapter : false
pre : " <b> 4. </b> "
---

#### Test Distribution Invalidations

When using Amazon CloudFront to distribute resources to the website, some resources will be stored in CloudFront's cache to speed up access for users. However, when you make changes to a cached resource but cannot change the URL to point to the new version, you need to perform Invalidations to discard the old version and reload the session. new version from the original server.

1. Access the Invalidations tab on the CloudFront Console interface.

- Create an Invalidation for the index.html resource.

![CloudFront Lab](/images/6/0001.png?featherlight=false&width=90pc)

2. You can specify / in Object paths because we have set index.html as default root object.


![CloudFront Lab](/images/6/0002.png?featherlight=false&width=90pc)

3. Invalidations in progress

![CloudFront Lab](/images/6/0003.png?featherlight=false&width=90pc)

4. Create successful Invalidations

![CloudFront Lab](/images/6/0004.png?featherlight=false&width=90pc)

5. After a few seconds, retry the site using the browser developer tool, you will see that it is no longer cached by CloudFront and reload a new version from the origin server.

![CloudFront Lab](/images/6/0005.png?featherlight=false&width=90pc)

Note: Invalidations may take a few minutes to complete, and during that time, users may be able to access an older version of the resource. Therefore, you need to consider and perform Invalidations at the right time to ensure the latest resources are delivered to users.

The data shows that when you perform Invalidations, if a resource is already cached in CloudFront, it will be removed from the cache and a new version will be downloaded from the origin server when the user requests access. access that resource. This helps ensure that users receive the latest version of the resource without having to clear the browser cache or wait for the CloudFront cache to expire.

Using Invalidations in Amazon CloudFront also saves costs and increases the performance of your website. When a resource is stored in CloudFront's cache, downloading it from the origin server consumes a lot of your time and system resources. When you use Invalidations to remove old versions, CloudFront will no longer have to reload these old versions, saving resources and reducing your website's operating costs.

In short, Invalidations is an important tool that helps ensure that users receive the latest version of the resource and helps speed up the website. It also saves resources and lowers your website's operating costs.