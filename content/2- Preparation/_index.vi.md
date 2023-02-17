---
title : "Các bước chuẩn bị"
date :  "`r Sys.Date()`" 
weight : 2
chapter : false
pre : " <b> 2. </b> "
---

#### Các bước chuẩn bị

Để tận dụng tối đa tiềm năng của**Amazon CloudFront**, bạn cần tạo các nguồn gốc (origins) cho nội dung của mình. Những nguồn gốc này sẽ chứa dữ liệu và được sử dụng bởi CloudFront để phân phối nội dung đến người dùng cuối. Hai nguồn gốc chính để sử dụng với**Amazon CloudFront** là Amazon S3 (Simple Storage Service) và Amazon EC2 (Elastic Compute Cloud).

- **Amazon S3 (Simple Storage Service)**: Nếu bạn đang sử dụng Amazon S3 để lưu trữ nội dung, bạn có thể tạo một S3 bucket làm nguồn gốc cho CloudFront. Một bucket S3 là một không gian lưu trữ đơn giản để lưu trữ các đối tượng như hình ảnh, video hoặc tài liệu. Sau khi tạo một bucket S3, bạn có thể đưa các đối tượng vào trong đó và sử dụng bucket S3 này làm nguồn gốc cho CloudFront.

- **Amazon EC2 (Elastic Compute Cloud)**: Nếu bạn đang sử dụng Amazon EC2 để chạy ứng dụng của mình, bạn có thể tạo một EC2 instance làm nguồn gốc cho CloudFront. Một EC2 instance là một máy ảo đang chạy trên nền tảng đám mây của Amazon. Sau khi tạo một EC2 instance, bạn có thể cài đặt và cấu hình ứng dụng của mình trên đó, sau đó sử dụng EC2 instance này làm nguồn gốc cho CloudFront.

Tạo nguồn gốc cho nội dung của bạn là cần thiết để sử dụng**Amazon CloudFront** một cách hiệu quả. Nếu bạn đang sử dụng Amazon S3 hoặc Amazon EC2, việc tạo nguồn gốc cho CloudFront là rất đơn giản. Việc sử dụng các nguồn gốc này giúp cho việc phân phối nội dung của bạn được thực hiện một cách nhanh chóng và an toàn.

#### Nội dung

1. [Tạo EC2](2.1-createec2/)
2. [Tạo S3](2.2-creates3/)
