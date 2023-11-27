---
title : "Add EC2 Origin"
date : "`r Sys.Date()`"
weight : 1
chapter : false
pre : " <b> 3.1 </b> "
---

#### Add EC2 Origin



1. Access the CloudFront distribution management page.

- Select the distribution ID corresponding to the site you want to configure.

- Select the Origins tab.
- Check existing origins. If you already have an origin, press the Create Origin button to add a new origin.
- At the Origins page, click the Create Origin button to create a new origin for the API.

![Create CloudFront Distribution](/images/4/0001.png?featherlight=false&width=90pc)

2. Enter the DNS name of the EC2 instance in the Origin Domain Name field. Configure by setting Origin Protocol Policy to HTTP only.

![Create CloudFront Distribution](/images/4/0002.png?featherlight=false&width=90pc)

3. Keep defaults and select **Additional settings**

![Create CloudFront Distribution](/images/4/0003.png?featherlight=false&width=90pc)

4. Increase keep alive timeout to 60 seconds.

Note that although we want to serve content over HTTPS to users, we want to keep the HTTP connection to origin to minimize the overhead of TLS.
- Select **Create origin**

![Create CloudFront Distribution](/images/4/0004.png?featherlight=false&width=90pc)

5. Create origin successfully

![Create CloudFront Distribution](/images/4/0005.png?featherlight=false&width=90pc)

6. Configure a second Behavior cache to use EC2's origin with the following parameters to use CloudFront as a proxy and ignore any cache classes.

![Create CloudFront Distribution](/images/4/0006.png?featherlight=false&width=90pc)

7. Path pattern > /api

- Origin and origin groups > Select previously created EC2 Origin

![Create CloudFront Distribution](/images/4/0007.png?featherlight=false&width=90pc)

8. Viewer protocol policy > Redirect HTTP to HTTPS


![Create CloudFront Distribution](/images/4/0008.png?featherlight=false&width=90pc)

9. Cache key and origin requests

- Cache policy and origin request policy (recommended)
- Cache policy > CachingDisabled
- Origin request policy - options -> AllViewer
- In the above configuration, we use two types of management policy, CachingDisabled is a managed cache policy -- this policy disables cache, it is useful for dynamic content and for requests that cannot be handled cached -- and AllViewer is an origin-managed request policy -- this policy includes all values ​​(header, cookie and query string) in the viewer's request.

![Create CloudFront Distribution](/images/4/0009.png?featherlight=false&width=90pc)

10. Select **Create behavior**

![Create CloudFront Distribution](/images/4/00010.png?featherlight=false&width=90pc)

11. Create successful behavior.

![Create CloudFront Distribution](/images/4/00011.png?featherlight=false&width=90pc)