---
title : "Clean up resources"
date : "`r Sys.Date()`"
weight : 12
chapter : false
pre : " <b> 12. </b> "
---
#### Clean up resources

#### Delete S3 bucket

- Step 1: Log in to the AWS Management Console.

- Step 2: Select S3 service.

- Step 3: Select the bucket you want to delete.

- Step 4: Click the Delete bucket button at the top of the screen.

- Step 5: Enter the bucket name in the confirmation box and click Delete.

Note: If the bucket contains any objects, you will not be able to delete the bucket directly. You must delete all objects in the bucket before deleting the bucket. If you want to delete some specific objects, select the object and click the Delete button.

Use the AWS Command Line Interface (CLI) to delete a bucket

You can also use the AWS CLI to delete buckets. Here are the steps to delete a bucket using the AWS CLI:

- Step 1: Open Command Prompt or Terminal.

- Step 2: Sign in to the AWS CLI.

- Step 3: Use the following command to delete the bucket:

```
aws s3 rb s3://bucket-name --force
```
Where, bucket-name is the name of the bucket you want to delete. The --force option is used to confirm the deletion of the bucket.

Note: If the bucket contains any objects, you will not be able to delete the bucket directly. You must delete all objects in the bucket before deleting the bucket. If you want to delete some specific objects, use aws s3 rm command to delete them.

With the steps above, you can delete a bucket in AWS S3 using the user interface or the AWS CLI. Make sure you back up all your data before deleting the bucket, and do this carefully.

#### Terminate EC2

- Step 1: Login to AWS Management Console

  - To delete EC2, you first need to log in to the AWS Management Console. This can be done by going to https://aws.amazon.com and logging in with your AWS account.

- Step 2: Search for EC2 instance to delete

  - After logging in to the AWS Management Console, you need to find the EC2 instance that you want to delete. You can use the search engines or browse the EC2 instance lists to find the instances you want to delete.

- Step 3: Delete EC2 instance

- Once you find an EC2 instance to delete, you can delete it by performing the following steps:

  - Right click on the EC2 instance you want to delete.
  - Select "Instance State" from the menu that appears.
  - Select "Terminate" to delete EC2 instance.
  - You will receive a warning to confirm the deletion of the EC2 instance. If you are sure you want to delete the EC2 instance, select "Yes, Terminate".

#### Delete CloudFront Distribution

- Step 1: Access AWS Console

- First, you need to sign in to the AWS Console with your account at https://console.aws.amazon.com/.

- Step 2: Select CloudFront . service

- After logging in to the AWS Console, you need to select the CloudFront service by clicking the "Services" icon on the top bar and searching for CloudFront. You can enter the keyword "CloudFront" in the search box to find the service faster.

- Step 3: Select CloudFront Distribution to delete

- In the CloudFront screen, you will see a list of CloudFront Distributions. Find and select the CloudFront Distribution you want to remove by clicking on its name.

- Step 4: Delete CloudFront Distribution

- After selecting the CloudFront Distribution to delete, you need to click the "Distribution Settings" button. In the distribution settings page you will see a "Delete" button. Click this button and confirm deletion of CloudFront Distribution by entering "Yes" in the confirmation dialog.

Note: When deleting CloudFront Distribution, all data related to it will be deleted from the system and cannot be recovered. Therefore, make sure that you have backed up your important data before performing the delete operation.

#### Delete Lambda Function
- Step 1: Log in to your AWS account and go to the Lambda service management page.

- Step 2: Find and select the Lambda Function you want to delete.

- Step 3: Click the Actions button and select Delete Function.

- Step 4: Confirm deletion by pressing Delete.

Note: You cannot restore a deleted Lambda Function.

#### Remove Lambda Edge
- Step 1: Log in to your AWS account and go to the Lambda service management page.

- Step 2: Select the Functions tab and select the Lambda Function used by Lambda Edge.

- Step 3: Find and click the Triggers tab and select Edge Association.

- Step 4: Click the Delete button and confirm by pressing Yes.

Note: After removing Lambda Edge, you need to wait about 10 minutes for the changes to take effect across the CDN network.