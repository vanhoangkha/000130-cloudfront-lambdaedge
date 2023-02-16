---
title : "Tạo S3"
date :  "`r Sys.Date()`" 
weight : 2
chapter : false
pre : " <b> 2.2 </b> "
---

#### Tạo S3

1. Đăng nhập vào trang quản lý S3 của Amazon Web Services (AWS) tại https://console.aws.amazon.com/s3/.
2. Bấm vào nút **Create bucket** (Tạo bucket) để bắt đầu quá trình tạo bucket mới.

![Create S3](/images/2/0001.png?featherlight=false&width=90pc)

3. Nhập tên bucket. Tên bucket phải là duy nhất trong toàn bộ hệ thống S3 và không được chứa dấu cách.
4.  Chọn khu vực lưu trữ (Region) cho bucket. Khu vực lưu trữ sẽ ảnh hưởng đến tốc độ truy cập và giá cả lưu trữ. Bạn nên chọn khu vực gần với người dùng để tối ưu tốc độ truy cập.

![Create S3](/images/2/0002.png?featherlight=false&width=90pc)

4.  Chọn các tùy chọn khác nếu cần. AWS cung cấp nhiều tùy chọn để cấu hình bucket, ví dụ như mã hóa dữ liệu, chia sẻ bucket với người dùng khác, cấu hình quyền truy cập, …
5.  Bấm vào nút **Create bucket** để hoàn thành quá trình tạo bucket.

![Create S3](/images/2/0003.png?featherlight=false&width=90pc)

Sau khi tạo bucket, bạn có thể truy cập vào bucket và thêm, xóa, sửa các tệp tin trong đó. Để truy cập vào bucket, bạn có thể sử dụng trình duyệt hoặc các công cụ quản lý AWS SDK.

#### Hướng dẫn tạo file index.html trên Amazon S3

1. Tạo file index.html

- Mở trình soạn thảo văn bản trên máy tính của bạn và tạo một file mới với tên index.html. Dán nội dung HTML sau đây vào file này:

```
<!DOCTYPE html>
<html lang="en">
  <body>
    <table border="1" width="100%">
      <thead>
        <tr>
          <td><h1>CloudFront Lab</h1></td>
        </tr>
      </thead>
      <tfoot>
        <tr>
          <td>Immersion Days - Edge Services - Module 1</td>
        </tr>
      </tfoot>
      <tbody>
        <tr>
          <td>Response sent by API</td>
        </tr>
      </tbody>
      <tbody>
        <tr>
          <td>
            <iframe src="/api" style="width: 100%; height: 100%"></iframe>
          </td>
        </tr>
      </tbody>
    </table>
  </body>
</html>

```

- Lưu file index.html vào một địa chỉ dễ nhớ trên máy tính của bạn.

2. Tải file index.html lên Amazon S3

- Truy cập vào bảng điều khiển Amazon S3 và chọn bucket đã được tạo. 

![Create S3](/images/2/0004.png?featherlight=false&width=90pc)

3. Tại giao diện của bucket, click vào nút **Upload** để tải file index.html lên.

![Create S3](/images/2/0005.png?featherlight=false&width=90pc)

4. Trong cửa sổ tiếp theo, click vào nút **Add files** và chọn file index.html từ máy tính của bạn. Sau đó, click vào nút **Next** để đi đến trang tiếp theo.

- Ở trang này, để tất cả các thiết lập mặc định và click vào nút **Next** một lần nữa. Tiếp tục để thiết lập các cài đặt khác và click vào nút **Upload** để hoàn tất việc tải lên.


![Create S3](/images/2/0006.png?featherlight=false&width=90pc)

5. Kiểm tra file index.html

![Create S3](/images/2/0007.png?featherlight=false&width=90pc)

6. Khi truy cập vào file index.html bằng đường dẫn Object URL được cung cấp bởi Amazon S3.

![Create S3](/images/2/0008.png?featherlight=false&width=90pc)

7. Bạn sẽ thấy thông báo từ chối truy cập do file không được cấu hình truy cập public.


![Create S3](/images/2/0009.png?featherlight=false&width=90pc)

