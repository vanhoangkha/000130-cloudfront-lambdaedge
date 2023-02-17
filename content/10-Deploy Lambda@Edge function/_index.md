---
title : "Deploy Lambda@Edge function to CloudFront"
date : "`r Sys.Date()`"
weight : 10
chapter : false
pre : " <b> 10. </b> "
---

#### Deploy Lambda@Edge function to CloudFront

In this section, we will add CloudFront as a trigger for your Lambda function.

![CloudFront Lab](/images/11/00014.png?featherlight=false&width=90pc)

1. In the same lambda console, you have implemented version 1 of the Lambda function. Click the Add trigger button and select CloudFront.

![CloudFront Lab](/images/11/0001.png?featherlight=false&width=90pc)

2. Click Deploy to Lambda@Edge.

![CloudFront Lab](/images/11/0002.png?featherlight=false&width=90pc)

3. Configure the trigger to use the previously created CloudFront Distribution and Cache Behavior with the following settings:

- Distribution: <select the distributionID generated from exercise 1>
- Cache behavior: "/serverless"
- CloudFront event: Origin request
- Select "I acknowledge that on deploy a new version of this function will be published with the above trigger and replicated across all available AWS regions."
- Click **Deploy**

![CloudFront Lab](/images/11/0003.png?featherlight=false&width=90pc)

4. Deployment will take approximately 5 minutes to complete for CloudFront distribution. In some cases, you can start testing in less than 5 minutes, depending on your location.

![CloudFront Lab](/images/11/0004.png?featherlight=false&width=90pc)

5. Return to **Lambda** interface and select **Replicas**.

![CloudFront Lab](/images/11/0005.png?featherlight=false&width=90pc)

6. Now search for your Lambda function in the Lambda functions list and you will find a Lambda function Replica in us-east-1 for the Lambda function you created.

![CloudFront Lab](/images/11/0006.png?featherlight=false&width=90pc)

7. When you move to other AWS regions, you will find that there is a Lambda function replica in all regions where CloudFront has a Regional Edge Cache. These are the Lambda functions that will be called when your CloudFront distribution executes Lambda@Edge. Once your CloudFront distribution has been deployed, test your CloudFront distribution by accessing Distribution in a browser with a serverless path.

![CloudFront Lab](/images/11/0007.png?featherlight=false&width=90pc)