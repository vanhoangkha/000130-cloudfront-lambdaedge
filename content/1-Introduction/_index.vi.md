---
title : "Giới thiệu"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 1. </b> "
---

#### Giới thiệu

Amazon CloudFront là dịch vụ phân phối nội dung tĩnh và động của Amazon Web Services (AWS). Với khả năng tăng tốc độ và độ ổn định của ứng dụng web của bạn, Amazon CloudFront cung cấp một giải pháp lưu trữ tạm thời cho nội dung của bạn trên các máy chủ Amazon Edge.

Amazon CloudFront có khả năng tùy chỉnh và linh hoạt cho phép bạn cấu hình các tính năng như EC2 và S3 Origins, CloudFront Distribution, Custom Error Page, Origin Group, Response Headers, tạo hành vi bộ đệm mới, tạo hàm Lambda@Edge và triển khai hàm Lambda@Edge lên CloudFront. Điều này giúp tăng tính sẵn sàng của nội dung và giảm thời gian phản hồi.

Ngoài ra, Amazon CloudFront còn cung cấp các tính năng giám sát và phân tích hiệu suất của nội dung được phân phối thông qua dịch vụ này. Với việc lưu trữ nhật ký trong S3 và sử dụng các công cụ như Amazon Athena và Amazon Redshift, bạn có thể dễ dàng giám sát và phân tích hiệu suất của nội dung của mình.

Để giúp bạn hiểu rõ hơn về Amazon CloudFront, hãy xem xét một số tính năng và cách sử dụng của dịch vụ này:

1. EC2 và S3 Origins: Amazon CloudFront cho phép bạn kết nối nội dung từ EC2 hoặc S3. Điều này giúp tăng tốc độ và giảm thời gian phản hồi của ứng dụng web của bạn.

2. CloudFront Distribution: Để sử dụng Amazon CloudFront, bạn cần tạo một phân phối. Phân phối là một tập hợp các máy chủ Edge của Amazon, mà nội dung của bạn được lưu trữ tạm thời trên đó.

3. Custom Error Page: Bạn có thể tùy chỉnh trang lỗi của mình để tương thích với trang web của bạn.

4. Origin Group: Nếu bạn có nhiều máy chủ Origin, bạn có thể cấu hình chúng vào một nhóm. CloudFront sẽ tự động chuyển đổi sang các máy chủ khác trong nhóm nếu máy chủ gốc gặp sự cố.

5. Response Headers: Bạn có thể cấu hình các tiêu đề phản hồi HTTP để tùy chỉnh các yêu cầu của khách hàng.

6. Tạo một hành vi bộ đệm mới: Nếu bạn muốn tạo một hành vi bộ đệm mới, bạn cần cấu hình các tính năng của nó trên máy chủ Origin hoặc bằng cách sử dụng Lambda@Edge.

7. Tạo hàm Lambda@Edge: Nếu bạn muốn xử lý yêu cầu CloudFront, bạn có thể sử dụng hàm Lambda@Edge.

7. Triển khai hàm Lambda@Edge lên CloudFront: Bạn có thể triển khai hàm Lambda@Edge của mình lên CloudFront bằng cách sử dụng AWS CLI.

8. Metrics and Logs: Amazon CloudFront cung cấp các tính năng giám sát và phân tích hiệu suất của nội dung được phân phối thông qua dịch vụ này. Với việc lưu trữ nhật ký trong S3 và sử dụng các công cụ như Amazon Athena và Amazon Redshift, bạn có thể dễ dàng giám sát và phân tích hiệu suất của nội dung của mình.

Như vậy, Amazon CloudFront là một dịch vụ tuyệt vời để tăng tốc độ và độ ổn định của ứng dụng web của bạn. Với các tính năng và ưu điểm của nó, Amazon CloudFront là một giải pháp phân phối nội dung đáng tin cậy và linh hoạt.


#### Best practice 

Để tận dụng tối đa tiềm năng của Amazon CloudFront, bạn nên tuân thủ một số best practice sau:

- Sử dụng S3 Bucket hoặc EC2 Instance làm Origin: Sử dụng S3 Bucket hoặc EC2 Instance làm Origin cho CloudFront Distribution của bạn sẽ tăng tốc độ phản hồi và giảm chi phí băng thông.

- Sử dụng SSL/TLS Encryption: Sử dụng SSL/TLS Encryption để bảo vệ dữ liệu trên đường truyền giữa Origin và Edge Locations. Bạn có thể sử dụng chứng chỉ SSL miễn phí hoặc trả phí để đảm bảo bảo mật cho dữ liệu của bạn.

- Sử dụng Compression: Sử dụng tính năng nén trong CloudFront Distribution để giảm kích thước tệp và tăng tốc độ tải trang.

- Sử dụng CloudFront Behaviors: Tạo các CloudFront Behaviors để tùy chỉnh cách CloudFront xử lý các yêu cầu. Ví dụ, bạn có thể tạo một hành vi bộ đệm để tối ưu hóa hiệu suất cho các yêu cầu GET hoặc HEAD.

- Sử dụng Caching: Sử dụng tính năng bộ đệm trong CloudFront để giảm thời gian tải trang và giảm chi phí băng thông. Bạn có thể cấu hình bộ đệm để lưu trữ tạm thời các tài nguyên và giảm số lượng yêu cầu đến Origin.

- Sử dụng Lambda@Edge: Sử dụng Lambda@Edge để tùy chỉnh và xử lý các yêu cầu của khách hàng trên CloudFront. Lambda@Edge cung cấp khả năng thêm, sửa đổi hoặc xóa các tiêu đề HTTP hoặc tài nguyên trên trang web của bạn.

- Sử dụng AWS WAF: Sử dụng AWS WAF để bảo vệ các ứng dụng của bạn trên CloudFront. AWS WAF cung cấp các chính sách bảo mật, bộ lọc và quản lý truy cập cho các ứng dụng của bạn.

- Sử dụng CloudFront Logs: Sử dụng tính năng nhật ký trong CloudFront để giám sát và phân tích hiệu suất của nội dung phân phối. Bạn có thể sử dụng các công cụ phân tích dữ liệu, như Amazon Athena hoặc Amazon Redshift, để phân tích nhật ký và đưa ra quyết định kinh doanh thông minh.