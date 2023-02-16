---
title : "Cấu hình Origin Group"
date :  "`r Sys.Date()`" 
weight : 6
chapter : false
pre : " <b> 6. </b> "
---

#### Cấu hình Origin Group

Trong phần này, bạn sẽ cấu hình một Origin Group   để cung cấp định tuyến lại trong trường hợp sự cố. Bạn có thể liên kết một Origin Group   với một hành vi bộ nhớ đệm để yêu cầu được định tuyến từ nguồn chính đến nguồn phụ để có tính sẵn sàng cao.

1. Truy cập vào bảng điều khiển S3, tạo một bucket S3 mới ở một khu vực khác
- Đặt tên riêng cho bucket S3, nhớ rằng tên bucket S3 là duy nhất toàn cầu, vì vậy hãy thêm một hậu tố cá nhân hóa, ví dụ:

```
cloudfrontlab-s3bucket-secondary-<YourNameHere>
```

![CloudFront Lab](/images/8/0001.png?featherlight=false&width=90pc)

2. Chọn **Create bucket**

![CloudFront Lab](/images/8/0002.png?featherlight=false&width=90pc)

3. Tạo một tệp secondary-index.html trên máy tính của bạn với nội dung HTML bên dưới:

```
<html lang="en">
  <body>
    <h1>CloudFront Lab</h1>
    <strong>Hi, this is a page from my secondary Origin! We now support Origin group and failover!</strong>
  </body>
</html>

```

   - Mở trình duyệt web và đăng nhập vào bảng điều khiển S3.
   - Chọn tên S3 bucket mà bạn muốn tải tệp lên.
   - Nhấp vào nút "Upload" (Tải lên) ở góc trên bên phải của trang web.
   - Chọn tệp secondary-index.html từ máy tính của bạn bằng cách nhấp vào nút "Add files" (Thêm tệp) hoặc kéo và thả tệp vào vùng tải lên.
   - Nhấp vào nút "Upload" (Tải lên) để tải lên tệp secondary-index.html của bạn lên S3.

![CloudFront Lab](/images/8/0003.png?featherlight=false&width=90pc)

4. Upload thành công.

![CloudFront Lab](/images/8/0004.png?featherlight=false&width=90pc)

5. Truy cập vào tài khoản AWS của bạn và chọn dịch vụ CloudFront.
   - Tìm và chọn  CloudFront Distribution mà bạn muốn cấu hình origin group.
   - Tạo một origin mới bằng cách chọn tùy chọn "Create Origin" 

![CloudFront Lab](/images/8/0005.png?featherlight=false&width=90pc)

6. Chọn tên domain origin của bạn và chọn S3 bucket mới chứa file secondary-index.html.

![CloudFront Lab](/images/8/0006.png?featherlight=false&width=90pc)

7. Thiết lập quyền truy cập vào S3 bucket bằng cách chọn "Yes, use OAI" và chọn "Select" để chọn OAI bạn đã tạo trước đó.
   - Cập nhật chính sách bucket bằng cách chọn "Yes, update the bucket policy".
   - Chọn **Create origin**

![CloudFront Lab](/images/8/0007.png?featherlight=false&width=90pc)

8. Tạo origin thành công. Nhấp vào nút Create Origin Group để tạo Origin Group mới.

![CloudFront Lab](/images/8/0008.png?featherlight=false&width=90pc)

9. Thực hiện cấu hình origin group. Chọn nguồn từ danh sách thả xuống và nhấp vào nút Add để thêm nguồn vào Origin Group.
   - Sử dụng cloudfrontlab-s3bucket-* như primary origin
   - Và cloudfrontlab-s3bucket-secondary-<YourNameHere> như secondary origin
   - Đối với tiêu chí failover, chọn 403 Forbidden và 404 Not Found.
   - Nhấp vào nút Create origin group để hoàn tất việc thêm nguồn vào Origin Group.


![CloudFront Lab](/images/8/0009.png?featherlight=false&width=90pc)

10.  Sau khi hoàn tất, bạn đã thêm thành công nguồn vào Origin Group trên CloudFront. Khi nguồn chính gặp sự cố, CloudFront sẽ tự động chuyển hướng đến nguồn thứ hai để đảm bảo sự liên tục của dịch vụ.

![CloudFront Lab](/images/8/00010.png?featherlight=false&width=90pc)

11. Chỉnh sửa default behavior trên CloudFront để sử dụng Origin Group mới

    - Chọn tab Behaviors 
    - Chọn Default(*) và nhấp vào nút Edit để chỉnh sửa default behavior của distribution.


![CloudFront Lab](/images/8/00011.png?featherlight=false&width=90pc)

12.  Chọn Origin Group đã tạo trong bước trước.
- Nhấp vào nút Save changes để lưu thay đổi.
- Sau khi hoàn tất, CloudFront sẽ sử dụng Origin Group mới làm nguồn khi truy cập vào bản phân phối. Bạn có thể kiểm tra chức năng failover bằng cách thử truy cập vào trang web và tạm thời ngắt kết nối mạng để kiểm tra xem CloudFront có chuyển hướng đến nguồn thứ hai không.

![CloudFront Lab](/images/8/00012.png?featherlight=false&width=90pc)

13.  Sau khi trạng thái distribution được chuyển sang Deployed, bạn có thể yêu cầu trang web secondary-index.html từ CloudFront. Nếu CloudFront hoạt động chính xác, bạn sẽ thấy S3 origin thứ hai phục vụ yêu cầu của bạn.
    - Mở trình duyệt web và truy cập vào địa chỉ URL của bản phân phối CloudFront.
    - Thay đổi đường dẫn URL từ /index.html sang /secondary-index.html để yêu cầu trang web từ S3 origin thứ hai.
    - Kiểm tra xem trang web đã được tải lên từ S3 origin thứ hai hay chưa. Nếu trang web được tải lên và hiển thị đúng, đó là dấu hiệu cho thấy CloudFront đang hoạt động chính xác và chuyển hướng đến S3 origin thứ hai khi cần thiết.
    - Lưu ý: Nếu trang web không được tải lên hoặc hiển thị sai, hãy kiểm tra lại các thiết lập của bạn để đảm bảo rằng nó đã được cấu hình đúng và hoạt động như mong đợi.

![CloudFront Lab](/images/8/00013.png?featherlight=false&width=90pc)

