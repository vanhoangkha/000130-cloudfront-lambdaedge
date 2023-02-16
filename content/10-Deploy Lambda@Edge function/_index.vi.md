---
title : "Triển khai Lambda@Edge function đến CloudFront"
date :  "`r Sys.Date()`" 
weight : 10
chapter : false
pre : " <b> 10. </b> "
---

#### Triển khai Lambda@Edge function đến CloudFront

Trong phần này, chúng ta sẽ thêm CloudFront như là một trigger cho Lambda function của bạn.

1. Trong cùng bảng điều khiển lambda, bạn đã triển khai version 1 của Lambda function. Nhấn vào nút Add trigger và chọn CloudFront.

![CloudFront Lab](/images/11/0001.png?featherlight=false&width=90pc)

2. Nhấn Deploy to Lambda@Edge.

![CloudFront Lab](/images/11/0002.png?featherlight=false&width=90pc)

3. ấu hình trigger để sử dụng CloudFront Distribution và Cache Behavior đã tạo trước đó với các cài đặt sau:

- Distribution: <chọn distributionID được tạo từ bài thực hành 1>
- Cache behavior: "/serverless"
- CloudFront event: Origin request
- Chọn "I acknowledge that on deploy a new version of this function will be published with the above trigger and replicated across all available AWS regions."
- Nhấn **Deploy**

![CloudFront Lab](/images/11/0003.png?featherlight=false&width=90pc)

4. Việc triển khai sẽ mất khoảng 5 phút để hoàn tất cho CloudFront distribution. Trong một số trường hợp, bạn có thể bắt đầu kiểm tra trong thời gian ngắn hơn 5 phút, phụ thuộc vào vị trí của bạn.

![CloudFront Lab](/images/11/0004.png?featherlight=false&width=90pc)

5. Quay lại giao diện **Lambda** và chọn **Replicas**. 

![CloudFront Lab](/images/11/0005.png?featherlight=false&width=90pc)

6. Bây giờ tìm kiếm Lambda function của bạn trong danh sách Lambda function và bạn sẽ tìm thấy một Lambda function Replica ở us-east-1 cho Lambda function mà bạn đã tạo. 

![CloudFront Lab](/images/11/0006.png?featherlight=false&width=90pc)

7. Khi bạn chuyển sang các khu vực AWS khác, bạn sẽ thấy rằng có một Lambda function replica trong tất cả các khu vực mà CloudFront có Regional Edge Cache. Đây là các Lambda function sẽ được gọi khi CloudFront distribution của bạn thực thi Lambda@Edge. Khi CloudFront distribution của bạn đã triển khai xong, kiểm tra CloudFront distribution của bạn bằng cách truy cập vào Distribution trên trình duyệt với đường dẫn serverless.

![CloudFront Lab](/images/11/0007.png?featherlight=false&width=90pc)

