---
title : "Creating EC2"
date : "`r Sys.Date()`"
weight : 1
chapter : false
pre : " <b> 2.1 </b> "
---

#### Create EC2

- **Amazon EC2 (Elastic Compute Cloud)**: If you are using Amazon EC2 to run your application, you can create an EC2 instance as the origin for CloudFront. An EC2 instance is a virtual machine running on Amazon's cloud platform. After creating an EC2 instance, you can install and configure your application on it, and then use this EC2 instance as the origin for CloudFront.

1. Access to EC2

   - Select **Instances**
   - Select **Launch instances**

![Create EC2](/images/1/0001.png?featherlight=false&width=90pc)

2. Enter the instance name

![Create EC2](/images/1/0002.png?featherlight=false&width=90pc)

3. Select **AMI** as **Amazon Linux**


![Create EC2](/images/1/0003.png?featherlight=false&width=90pc)

4. Select **t2.micro**


![Create EC2](/images/1/0004.png?featherlight=false&width=90pc)

5. Select **Create new key pair**

![Create EC2](/images/1/0005.png?featherlight=false&width=90pc)

6. Enter the key name and select **Create key pair**

![Create EC2](/images/1/0006.png?featherlight=false&width=90pc)

7. Configure networking

   - Select **VPC**
   - Create **security group**
   - Configure security according to the picture

![Create EC2](/images/1/0007.png?featherlight=false&width=90pc)

8. Scroll down to the **User data** section, enter the following script:

```
#!/bin/bash
#Update the system and install Node.js

yum update -y
curl -sL https://rpm.nodesource.com/setup_14.x | sudo bash -
yum install -y nodejs

#Install PM2 and Express
npm install pm2@latest -g
npm install express --save

#Create and configure the Express app
cat <<'EOF' >> app.js
let express = require('express');
let app = express();

app.get('/api', (req, res) => {
  console.log(JSON.stringify(req.headers));
  let message = {
    timestamp: new Date().toISOString(),
    headers: req.headers,
  };
  res.json(message);
});

app.listen(80, () => {
  console.log('api is up!');
});
EOF


#Start the app with PM2
sudo pm2 start ./app.js
sudo pm2 startup systemd
sudo pm2 save

#Enable PM2 to start on system boot
systemctl enable --now pm2-root.service
```

![Create EC2](/images/1/0008.png?featherlight=false&width=90pc)

9. Select **Launch instance**

![Create EC2](/images/1/0009.png?featherlight=false&width=90pc)

10. Successful EC2 Creation

![Create EC2](/images/1/00010.png?featherlight=false&width=90pc)

11. View the details of the newly created EC2.

![Create EC2](/images/1/00011.png?featherlight=false&width=90pc)

12. Copy **Public IPv4 DNS**

![Create EC2](/images/1/00012.png?featherlight=false&width=90pc)

13. Use **Public IPv4 DNS** included with **/api**

![Create EC2](/images/1/00013.png?featherlight=false&width=90pc)