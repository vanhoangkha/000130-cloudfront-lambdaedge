---
title : "Cấu hình tùy chỉnh Error Page"
date :  "`r Sys.Date()`" 
weight : 5
chapter : false
pre : " <b> 5. </b> "
---

#### Cấu hình tùy chỉnh Error Page

1. Khi kiểm tra một URL ngẫu nhiên bằng tên miền CloudFront của bạn, bạn sẽ nhận được phản hồi 403 Forbidden từ S3 đằng sau CloudFront vì tệp không tồn tại. Mặc định, CloudFront lưu trữ tạm thời phản hồi này trong 10 giây.

![CloudFront Lab](/images/7/0001.png?featherlight=false&width=90pc)

2. Tạo tệp error.html trên máy tính của bạn sử dụng trình soạn thảo văn bản với nội dung HTML bên dưới và tải lên bucket S3 của bạn như cách bạn đã làm trước đó cho tệp index.html.

- Mở trình soạn thảo văn bản trên máy tính của bạn
- Nếu bạn sử dụng Windows, bạn có thể sử dụng Notepad hoặc Notepad++ để soạn thảo văn bản
- Nếu bạn sử dụng MacOS, bạn có thể sử dụng TextEdit hoặc các trình soạn thảo văn bản khác để soạn thảo văn bản
- Tạo tệp error.html với nội dung HTML bên dưới:
```
<html lang="en">
  <body>
    <h1>CloudFront Lab</h1>
    <strong>Ops, this is a nice error page!</strong>
  </body>
</html>
```
- Lưu tệp error.html với định dạng UTF-8 và đặt tên cho tệp tùy ý (ví dụ: error.html)

- Đăng nhập vào AWS Console và chọn dịch vụ S3

- Chọn bucket S3 mà bạn muốn tải lên tệp error.html



![CloudFront Lab](/images/7/0002.png?featherlight=false&width=90pc)

2. Chọn "Upload" để tải lên tệp error.html từ máy tính của bạn lên S3 bucket



![CloudFront Lab](/images/7/0003.png?featherlight=false&width=90pc)

3. Chờ cho quá trình tải lên hoàn tất



![CloudFront Lab](/images/7/0004.png?featherlight=false&width=90pc)

4. Để kiểm tra xem tệp error.html đã được tải lên thành công, hãy chọn tệp đó trên S3 bucket và xem trước nội dung của tệp.

![CloudFront Lab](/images/7/0005.png?featherlight=false&width=90pc)

#### Hướng dẫn cấu hình trang lỗi tùy chỉnh trong CloudFront

Để cấu hình trang lỗi tùy chỉnh trong CloudFront, bạn có thể thực hiện các bước sau:

1. Đăng nhập vào bảng điều khiển CloudFront

- Chọn  CloudFront Distribution mà bạn muốn cấu hình trang lỗi tùy chỉnh
- Chọn tab "Error Pages"
- Tìm và chọn tab "Error Pages" 
- Tạo trang lỗi tùy chỉnh
- Nhấp vào nút "Create custom error response"

![CloudFront Lab](/images/7/0006.png?featherlight=false&width=90pc)

2. Bạn có thể cấu hình trang lỗi tùy chỉnh với các thiết lập sau đây.

   - HTTP error code > 403 Forbidden
   - Error caching minimum TTL: 60
   - Customize error response: Yes
   - Response page path: /error.html
   - HTTP Response code: 200 OK
   - Chọn Create custom error response

- Với các thiết lập này, khi trang web của bạn gặp lỗi HTTP > 403 Forbidden, nó sẽ hiển thị trang lỗi tùy chỉnh được cấu hình trước đó và lưu cache trong ít nhất 60 giây. Các khách hàng truy cập trang web của bạn sẽ nhận được phản hồi lỗi tùy chỉnh với đường dẫn /error.html và mã phản hồi HTTP 200 OK.

![CloudFront Lab](/images/7/0007.png?featherlight=false&width=90pc)

3. Tạo custom error response thành công. 


![CloudFront Lab](/images/7/0008.png?featherlight=false&width=90pc)

4. Kiểm tra trang lỗi tùy chỉnh của bạn bằng cách yêu cầu một trang ngẫu nhiên từ CloudFront. Bạn có thể cần vài phút để chờ cập nhật phân phối và lan truyền đến các vị trí Edge. Hãy đảm bảo rằng bạn sử dụng một giá trị ngẫu nhiên khác so với bài kiểm tra trước đó, nếu không bạn sẽ nhận được phiên bản cache giống như khi kiểm tra trong 5 phút qua.

- Để kiểm tra trang lỗi tùy chỉnh, làm theo các bước sau:

  - Mở trình duyệt web và truy cập vào một trang ngẫu nhiên từ CloudFront.
  - Đợi vài phút để CloudFront cập nhật và lan truyền phân phối.
  - Nhập một giá trị ngẫu nhiên khác với bài kiểm tra trước đó.
  - Nhận thông báo lỗi HTTP > 403 Forbidden từ CloudFront.
  - Kiểm tra xem trang lỗi tùy chỉnh đã được hiển thị hay chưa. Nếu trang lỗi tùy chỉnh được hiển thị, có nghĩa là bạn đã cấu hình thành công.

- Nếu bạn vẫn nhận được thông báo lỗi mặc định của CloudFront, hãy kiểm tra lại cấu hình trang lỗi tùy chỉnh của bạn và đảm bảo rằng bạn đã lưu lại các thay đổi. Bạn cũng nên kiểm tra xem các giá trị của bạn có phù hợp với các thiết lập yêu cầu hay không.

![CloudFront Lab](/images/7/0009.png?featherlight=false&width=90pc)

5. Tạo trang lỗi tùy chỉnh mới để hiển thị khi CloudFront không thể kết nối đến nguồn. Sử dụng các thiết lập sau:

   - HTTP error code > 504 Gateway Timeout
   - Error caching minimum TTL: 5
   - Customize error response: Yes
   - Response page path: /error.html
   - HTTP Response code: 200 OK
   - Chọn Create custom error response

![CloudFront Lab](/images/7/00010.png?featherlight=false&width=90pc)

6. Hoàn thành tạo 2 Error page.

![CloudFront Lab](/images/7/00011.png?featherlight=false&width=90pc)

7. Thay đổi Inbound rule của Security group 

- Truy cập vào EC2 Console.
- Tại giao diện EC2 Console, chọn Security Groups trong bảng điều khiển bên trái.
- Chọn Security Group chứa Inbound rule truy cập đến EC2 instance đang chạy Nodejs API.


![CloudFront Lab](/images/7/00012.png?featherlight=false&width=90pc)

8. Chỉnh sửa Inbound rule cho **HTTP** từ **0.0.0.0/0** thành **MyIP**
- Chọn nút Save Rules để lưu các thay đổi đã được thực hiện.

![CloudFront Lab](/images/7/00013.png?featherlight=false&width=90pc)

9. Chỉnh sửa Security group thành công.

![CloudFront Lab](/images/7/00014.png?featherlight=false&width=90pc)

10. Mở trình duyệt web và nhập địa chỉ URL CloudFront của trang index.html vào thanh địa chỉ.
- Nhấn Enter để truy cập trang web.
- Kiểm tra xem trang web có hoạt động bình thường hay không.
- Bạn  sẽ thấy giao diện như hình

![CloudFront Lab](/images/7/00015.png?featherlight=false&width=90pc)