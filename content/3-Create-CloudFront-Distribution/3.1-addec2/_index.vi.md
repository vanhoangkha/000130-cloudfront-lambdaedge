---
title : "Thêm EC2 Origin"
date :  "`r Sys.Date()`" 
weight : 1
chapter : false
pre : " <b> 3.1 </b> "
---

#### Thêm EC2 Origi



1. Truy cập vào trang quản lý CloudFront distribution.

- Chọn distribution ID tương ứng với trang web bạn muốn cấu hình.

- Chọn tab Origins.
- Kiểm tra các origin hiện có. Nếu bạn đã có một origin, hãy nhấn nút Create Origin để thêm origin mới.
- Tại trang Origins, nhấn vào nút Create Origin để tạo một origin mới cho API.

![Create CloudFront Distribution](/images/4/0001.png?featherlight=false&width=90pc)

2. Nhập tên DNS của EC2 instance vào trường Origin Domain Name. Cấu hình bằng cách đặt Origin Protocol Policy thành HTTP only.

![Create CloudFront Distribution](/images/4/0002.png?featherlight=false&width=90pc)

3. Giữ mặc định và chọn **Additional settings**

![Create CloudFront Distribution](/images/4/0003.png?featherlight=false&width=90pc)

4. Tăng keep alive timeout lên 60 giây. 

- Lưu ý rằng mặc dù chúng ta muốn phục vụ nội dung trên HTTPS cho người dùng, nhưng chúng ta muốn giữ kết nối HTTP với origin để giảm thiểu chi phí của TLS. 
- Chọn **Create origin**

![Create CloudFront Distribution](/images/4/0004.png?featherlight=false&width=90pc)

5. Tạo origin thành công

![Create CloudFront Distribution](/images/4/0005.png?featherlight=false&width=90pc)

6. Cấu hình một Behavior cache thứ hai để sử dụng origin của EC2 với các tham số sau đây để sử dụng CloudFront như proxy và bỏ qua bất kỳ lớp cache nào.

![Create CloudFront Distribution](/images/4/0006.png?featherlight=false&width=90pc)

7. Path pattern > /api

- Origin và origin groups > Chọn EC2 Origin đã tạo trước đó

![Create CloudFront Distribution](/images/4/0007.png?featherlight=false&width=90pc)

8. Viewer protocol policy > Redirect HTTP to HTTPS


![Create CloudFront Distribution](/images/4/0008.png?featherlight=false&width=90pc)

9. Cache key và origin requests 

- Cache policy và origin request policy (khuyến nghị)
- Cache policy > CachingDisabled
- Origin request policy - tùy chọn -> AllViewer
- Trong cấu hình trên, chúng ta sử dụng hai loại chính sách quản lý, CachingDisabled là một chính sách cache quản lý -- chính sách này vô hiệu hóa cache, nó hữu ích cho nội dung động và cho các yêu cầu không thể được lưu vào bộ nhớ cache -- và AllViewer là một chính sách yêu cầu origin quản lý -- chính sách này bao gồm tất cả các giá trị (header, cookie và query string) trong yêu cầu của viewer.

![Create CloudFront Distribution](/images/4/0009.png?featherlight=false&width=90pc)

10. Chọn **Create behavior**

![Create CloudFront Distribution](/images/4/00010.png?featherlight=false&width=90pc)

11. Tạo behavior thành công.

![Create CloudFront Distribution](/images/4/00011.png?featherlight=false&width=90pc)