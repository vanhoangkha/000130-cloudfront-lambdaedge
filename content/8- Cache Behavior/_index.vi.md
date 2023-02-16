---
title : "Tạo Cache Behavior"
date :  "`r Sys.Date()`" 
weight : 8
chapter : false
pre : " <b> 8. </b> "
---



#### Tạo nội dung động với Lambda@Edge

Trong bài lab này, bạn sẽ sử dụng Lambda@Edge để động tạo trang web được tạo. Thay vì chỉ đơn giản là xuất các tiêu đề yêu cầu, chúng ta sẽ đưa ra các giá trị trong một bảng HTML. Bạn sẽ học cách tạo quyền cho Lambda@Edge, triển khai mã chức năng Lambda@Edge và kiểm tra nó. Cuối cùng, bạn sẽ có thể xem các nhật ký chức năng, số liệu thống kê và khắc phục sự cố mã của bạn.

#### Tạo Cache Behavior


Trong phần này, bạn sẽ tạo một Cache Behavior mới trong phân phối CloudFront mà bạn đã tạo. Bạn sẽ sử dụng Cache Behavior này để kết nối chức năng Lambda@Edge mà bạn sẽ viết.

1 - Truy cập vào bảng điều khiển CloudFront và chọn phân phối mà bạn đã tạo trong Lab 1.

2 - Chuyển đến tab "Cache Behaviors" và nhấp vào "Create Behavior"

![CloudFront Lab](/images/9/0001.png?featherlight=false&width=90pc)

3. Thực hiện cấu hình sau:

   - Path : “/serverless”

   - Origin: <Select the EC2 origin created in Lab 1>

![CloudFront Lab](/images/9/0002.png?featherlight=false&width=90pc)

4. Cache Policy: “Managed-CachingDisabled”

   - Origin Request Policy: “Managed-AllViewer”

   - Để lại tất cả các thiết lập khác ở giá trị mặc định.

![CloudFront Lab](/images/9/0003.png?featherlight=false&width=90pc)

5. Nhấp vào “Create”

![CloudFront Lab](/images/9/0004.png?featherlight=false&width=90pc)

6. Hoàn thành tạo Cache Behavior mới.

![CloudFront Lab](/images/9/0005.png?featherlight=false&width=90pc)

