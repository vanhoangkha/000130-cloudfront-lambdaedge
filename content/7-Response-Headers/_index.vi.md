---
title : "Response Headers"
date :  "`r Sys.Date()`" 
weight : 7
chapter : false
pre : " <b> 7. </b> "
---

#### Các phần tiêu đề phản hồi (Response Headers)

Trong phần này, bạn sẽ cấu hình các phần tiêu đề bảo mật trong phản hồi S3 được trả về bởi Distribution CloudFront của bạn. Bạn không cần phải cấu hình Origin  của mình hoặc sử dụng các hàm tùy chỉnh Lambda@Edge hoặc CloudFront để chèn các tiêu đề này. Amazon CloudFront hiện đã hỗ trợ phần tiêu đề phản hồi có thể cấu hình.

1. Truy cập vào AWS Management Console và chọn dịch vụ CloudFront.

- Chọn tab Distributions và chọn ID  Distributions của bạn.
- Trong tab Behaviors, chọn Default(*) behavior và nhấp vào nút Edit.

![CloudFront Lab](/images/8/00014.png?featherlight=false&width=90pc)

2. Trong phần "Cache key and origin requests", dưới "Response headers policy - optional", mở danh sách thả xuống để xem danh sách các tùy chọn. Chọn "Security headers" và nhấp vào nút "Save changes".
- Bước này sẽ thiết lập chính sách phản hồi phù hợp với tiêu đề bảo mật bạn đã thêm vào ở bước trước đó. Khi các yêu cầu đến CloudFront, các phần tiêu đề bảo mật được chèn vào phản hồi S3 từ Distribution của bạn. Điều này giúp bảo vệ trang web của bạn khỏi các cuộc tấn công khác nhau.

![CloudFront Lab](/images/8/00015.png?featherlight=false&width=90pc)

3. Thực hiện cập nhật Inbound rule của security group, đổi **MyIP** thành **Anywhere**

![CloudFront Lab](/images/8/00016.png?featherlight=false&width=90pc)

4. Chính sách phản hồi quản lý này sẽ thêm một tập hợp các phần tiêu đề bảo mật vào tất cả các phản hồi mà CloudFront gửi đến người xem. Để biết thêm thông tin về các phần tiêu đề bảo mật này, hãy xem hướng dẫn bảo mật web của Mozilla .

- Với chính sách phản hồi này, CloudFront sẽ thêm X-Content-Type-Options: nosniff vào tất cả các phản hồi, bất kể phản hồi mà CloudFront nhận được từ Origin  có chứa phần tiêu đề này hay không. Đối với tất cả các tiêu đề khác trong chính sách này, nếu phản hồi mà CloudFront nhận được từ Origin  chứa tiêu đề đó, CloudFront sử dụng tiêu đề được nhận (và giá trị của nó) trong phản hồi của mình đối với người xem, thay vì sử dụng tiêu đề trong chính sách này. 

![CloudFront Lab](/images/8/00018.png?featherlight=false&width=90pc)

5. Trở lại trang web của bạn bằng địa chỉ URL CloudFront của bạn (ví dụ: http://dxxxx.cloudfront.net), mở công cụ phát triển của trình duyệt của bạn và kiểm tra các phần tiêu đề phản hồi được gửi bởi CloudFront. Các phần tiêu đề bảo mật được thêm vào bằng chính sách phản hồi mà bạn đã cấu hình sẽ được liệt kê trong phần "Response Headers" của phản hồi.

![CloudFront Lab](/images/8/00017.png?featherlight=false&width=90pc)

- Bạn đã học cách tạo một Distribution với nhiều Origin  và nhiều hành vi nhằm cung cấp nội dung tĩnh và chuyển tiếp nội dung động API đến Origin của bạn.

- Bạn đã học cách thiết lập một Origin group để cung cấp định tuyến lại trong trường hợp xảy ra sự cố.

- Bạn cũng đã học cách thiết lập trang lỗi tùy chỉnh và vô hiệu hóa nội dung nhanh chóng.

- Cuối cùng, bạn đã tìm hiểu về một số phần tiêu đề CloudFront quan trọng để gỡ lỗi và cách thêm chính sách phản hồi vào phản hồi.


