---
title : "Tạo EC2"
date :  "`r Sys.Date()`" 
weight : 1
chapter : false
pre : " <b> 2.1 </b> "
---

#### Tạo EC2

- **Amazon EC2 (Elastic Compute Cloud)**: Nếu bạn đang sử dụng Amazon EC2 để chạy ứng dụng của mình, bạn có thể tạo một EC2 instance làm nguồn gốc cho CloudFront. Một EC2 instance là một máy ảo đang chạy trên nền tảng đám mây của Amazon. Sau khi tạo một EC2 instance, bạn có thể cài đặt và cấu hình ứng dụng của mình trên đó, sau đó sử dụng EC2 instance này làm nguồn gốc cho CloudFront.

1. Truy cập vào EC2 

   - Chọn **Instances**
   - Chọn **Launch instances**

![Create EC2](/images/1/0001.png?featherlight=false&width=90pc)

2. Nhập tên instance

![Create EC2](/images/1/0002.png?featherlight=false&width=90pc)

3. Chọn **AMI** là **Amazon Linux**


![Create EC2](/images/1/0003.png?featherlight=false&width=90pc)

4. CHọn **t2.micro**


![Create EC2](/images/1/0004.png?featherlight=false&width=90pc)

5. Chọn **Create new key pair**

![Create EC2](/images/1/0005.png?featherlight=false&width=90pc)

6. Nhập tên key và chọn **Create key pair**

![Create EC2](/images/1/0006.png?featherlight=false&width=90pc)

7. Cấu hình networking

   - Chọn **VPC**
   - Tạo **security group**
   - Cấu hình security theo hình

![Create EC2](/images/1/0007.png?featherlight=false&width=90pc)

8. Kéo xuống phần **User data**, bạn điền đoạn script sau:


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

9. Chọn **Launch instance**

![Create EC2](/images/1/0009.png?featherlight=false&width=90pc)

10. Tạo EC2 thành công

![Create EC2](/images/1/00010.png?featherlight=false&width=90pc)

11. Xem chi tiết EC2 vừa tạo.

![Create EC2](/images/1/00011.png?featherlight=false&width=90pc)

12. Sao chép **Public IPv4 DNS**

![Create EC2](/images/1/00012.png?featherlight=false&width=90pc)

13. Sử dụng **Public IPv4 DNS** kèm theo **/api**

![Create EC2](/images/1/00013.png?featherlight=false&width=90pc)