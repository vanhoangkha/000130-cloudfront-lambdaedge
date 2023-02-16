---
title : "Creating Cache Behavior"
date : "`r Sys.Date()`"
weight : 8
chapter : false
pre : " <b> 8. </b> "
---



#### Dynamic content generation with Lambda@Edge

In this lab, you will use Lambda@Edge to dynamically generate the generated web page. Instead of simply outputting the request headers, we'll output the values ​​in an HTML table. You will learn how to authorize Lambda@Edge, implement the Lambda@Edge function code, and test it. Finally, you'll be able to view your function logs, stats, and troubleshoot your code.

#### Cache Behavior


In this section, you will create a new Cache Behavior in the CloudFront distribution you created. You will use this Cache Behavior to connect the Lambda@Edge function that you will write.

1 - Go to the CloudFront dashboard and select the distribution you created in Lab 1.

2 - Go to "Cache Behaviors" tab and click "Create Behavior"

![CloudFront Lab](/images/9/0001.png?featherlight=false&width=90pc)

3. Make the following configuration:

   - Path : "/serverless"

   - Origin: <Select the EC2 origin created in Lab 1>

![CloudFront Lab](/images/9/0002.png?featherlight=false&width=90pc)

4. Cache Policy: “Managed-CachingDisabled”

   - Origin Request Policy: “Managed-AllViewer”

   - Leave all other settings at default values.

![CloudFront Lab](/images/9/0003.png?featherlight=false&width=90pc)

5. Click “Create”

![CloudFront Lab](/images/9/0004.png?featherlight=false&width=90pc)

6. Finish creating the new Cache Behavior.

![CloudFront Lab](/images/9/0005.png?featherlight=false&width=90pc)