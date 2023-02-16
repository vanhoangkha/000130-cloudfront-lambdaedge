---
title : "Response Headers"
date : "`r Sys.Date()`"
weight : 7
chapter : false
pre : " <b> 7. </b> "
---

#### Response Headers

In this section, you will configure the security headers in the S3 response returned by your Distribution CloudFront. You don't need to configure your origin or use Lambda@Edge or CloudFront custom functions to insert these headers. Amazon CloudFront now supports configurable response headers.

1. Go to the AWS Management Console and select the CloudFront service.

- Select the Distributions tab and select your Distributions ID.
- In the Behaviors tab, select Default(*) behavior and click the Edit button.

![CloudFront Lab](/images/8/00014.png?featherlight=false&width=90pc)

2. In the "Cache key and origin requests" section, under "Response headers policy - optional", open the drop-down list to see a list of options. Select "Security headers" and click the "Save changes" button.
- This step will set up a response policy that matches the security header you added in the previous step. When requests come to CloudFront, security headers are inserted into the S3 response from your Distribution. This helps to protect your website from various attacks.

![CloudFront Lab](/images/8/00015.png?featherlight=false&width=90pc)

3. Update the Inbound rule of the security group, change **MyIP** to **Anywhere**

![CloudFront Lab](/images/8/00016.png?featherlight=false&width=90pc)

4. This Management Response Policy will add a set of security headers to all responses that CloudFront sends to viewers. For more information about these security headers, see Mozilla's web security guide.

- With this response policy, CloudFront will add X-Content-Type-Options: nosniff to all responses, regardless of whether the response CloudFront receives from Origin contains this header. For all other headers in this policy, if the response CloudFront receives from Origin contains that header, CloudFront uses the header received (and its value) in its response to its viewers. , instead of using the header in this policy.

![CloudFront Lab](/images/8/00018.png?featherlight=false&width=90pc)

5. Return to your site with your CloudFront URL (eg http://dxxxx.cloudfront.net), open your browser's developer tools and check the response headers sent by CloudFront. Security headers added using the response policy that you have configured will be listed in the "Response Headers" section of the response.

![CloudFront Lab](/images/8/00017.png?featherlight=false&width=90pc)

- You learned how to create a Distribution with multiple origins and multiple behaviors to serve static content and forward dynamic content API to your origin.

- You learned how to set up an origin group to provide rerouting in the event of a problem.

- You also learned how to set up a custom error page and disable content on the fly.

- Finally, you learned about some important CloudFront headers for debugging and how to add a response policy to the response.