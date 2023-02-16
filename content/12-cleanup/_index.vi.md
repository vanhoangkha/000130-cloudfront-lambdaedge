---
title : "Dọn dẹp tài nguyên"
date :  "`r Sys.Date()`" 
weight : 12
chapter : false
pre : " <b> 12. </b> "
---
#### Dọn dẹp tài nguyên

#### Xóa S3 bucket

- Bước 1: Đăng nhập vào AWS Management Console.

- Bước 2: Chọn dịch vụ S3.

- Bước 3: Chọn bucket mà bạn muốn xóa.

- Bước 4: Nhấn vào nút Xóa bucket ở phía trên màn hình.

- Bước 5: Điền tên bucket vào ô xác nhận và nhấn Xóa.

Lưu ý: Nếu bucket chứa bất kỳ đối tượng nào, bạn sẽ không thể xóa bucket trực tiếp. Bạn phải xóa tất cả các đối tượng trong bucket trước khi xóa bucket. Nếu bạn muốn xóa một số đối tượng cụ thể, hãy chọn đối tượng đó và nhấn vào nút Xóa.

Sử dụng AWS Command Line Interface (CLI) để xóa một bucket

Bạn cũng có thể sử dụng AWS CLI để xóa bucket. Sau đây là các bước để xóa một bucket bằng AWS CLI:

- Bước 1: Mở Command Prompt hoặc Terminal.

- Bước 2: Đăng nhập vào AWS CLI.

- Bước 3: Sử dụng lệnh sau để xóa bucket:

```
aws s3 rb s3://bucket-name --force
```
Trong đó, bucket-name là tên bucket mà bạn muốn xóa. Tùy chọn --force được sử dụng để xác nhận việc xóa bucket.

Lưu ý: Nếu bucket chứa bất kỳ đối tượng nào, bạn sẽ không thể xóa bucket trực tiếp. Bạn phải xóa tất cả các đối tượng trong bucket trước khi xóa bucket. Nếu bạn muốn xóa một số đối tượng cụ thể, hãy sử dụng lệnh aws s3 rm để xóa chúng.

Với các bước trên, bạn có thể xóa một bucket trong AWS S3 bằng cách sử dụng giao diện người dùng hoặc AWS CLI. Hãy đảm bảo rằng bạn đã sao lưu toàn bộ dữ liệu trước khi xóa bucket, và thực hiện tác vụ này cẩn thận.

#### Terminate EC2

- Bước 1: Đăng nhập vào AWS Management Console

  - Để xóa EC2, trước tiên bạn cần đăng nhập vào AWS Management Console. Điều này có thể được thực hiện bằng cách truy cập vào địa chỉ https://aws.amazon.com và đăng nhập bằng tài khoản AWS của bạn.

- Bước 2: Tìm kiếm EC2 instance cần xóa

  - Sau khi đăng nhập vào AWS Management Console, bạn cần tìm EC2 instance mà bạn muốn xóa. Bạn có thể sử dụng các công cụ tìm kiếm hoặc duyệt các danh sách EC2 instance để tìm kiếm các instance mà bạn muốn xóa.

- Bước 3: Xóa EC2 instance

- Sau khi tìm thấy EC2 instance cần xóa, bạn có thể xóa nó bằng cách thực hiện các bước sau:

  - Nhấp chuột phải vào EC2 instance mà bạn muốn xóa.
  - Chọn "Instance State" từ menu xuất hiện.
  - Chọn "Terminate" để xóa EC2 instance.
  - Bạn sẽ nhận được một cảnh báo để xác nhận việc xóa EC2 instance. Nếu bạn chắc chắn muốn xóa EC2 instance, hãy chọn "Yes, Terminate".

#### Xóa CloudFront Distribution

- Bước 1: Truy cập AWS Console

- Đầu tiên, bạn cần đăng nhập vào AWS Console bằng tài khoản của mình tại https://console.aws.amazon.com/.

- Bước 2: Chọn dịch vụ CloudFront

- Sau khi đăng nhập vào AWS Console, bạn cần chọn dịch vụ CloudFront bằng cách nhấp vào biểu tượng "Services" (Dịch vụ) trên thanh đầu màn hình và tìm kiếm CloudFront. Bạn có thể nhập từ khóa "CloudFront" vào ô tìm kiếm để tìm dịch vụ nhanh chóng hơn.

- Bước 3: Chọn CloudFront Distribution cần xóa

- Trong màn hình CloudFront, bạn sẽ thấy danh sách các CloudFront Distribution. Tìm và chọn CloudFront Distribution mà bạn muốn xóa bằng cách nhấp vào tên của nó.

- Bước 4: Xóa CloudFront Distribution

- Sau khi chọn CloudFront Distribution cần xóa, bạn cần nhấp vào nút "Distribution Settings" (Cài đặt phân phối). Trong trang cài đặt phân phối, bạn sẽ thấy nút "Delete" (Xóa). Nhấp vào nút này và xác nhận việc xóa CloudFront Distribution bằng cách nhập "Yes" (Có) trong hộp thoại xác nhận.

Lưu ý: Khi xóa CloudFront Distribution, tất cả các dữ liệu liên quan đến nó sẽ bị xóa khỏi hệ thống và không thể khôi phục lại. Do đó, hãy đảm bảo rằng bạn đã sao lưu các dữ liệu quan trọng trước khi thực hiện thao tác xóa.

#### Xóa Lambda Function
- Bước 1: Đăng nhập vào tài khoản AWS và vào trang quản lý dịch vụ Lambda.

- Bước 2: Tìm và chọn Lambda Function bạn muốn xóa.

- Bước 3: Nhấp vào nút Actions và chọn Delete Function.

- Bước 4: Xác nhận xóa bằng cách nhấn Delete.

Lưu ý: Bạn không thể khôi phục lại Lambda Function đã xóa.

#### Xóa Lambda Edge
- Bước 1: Đăng nhập vào tài khoản AWS và vào trang quản lý dịch vụ Lambda.

- Bước 2: Chọn tab Functions và chọn Lambda Function được sử dụng bởi Lambda Edge.

- Bước 3: Tìm và nhấp vào tab Triggers và chọn Edge Association.

- Bước 4: Nhấp vào nút Delete và xác nhận bằng cách nhấn Yes.

Lưu ý: Sau khi xóa Lambda Edge, bạn cần chờ khoảng 10 phút để các thay đổi có hiệu lực trên toàn mạng lưới CDN.