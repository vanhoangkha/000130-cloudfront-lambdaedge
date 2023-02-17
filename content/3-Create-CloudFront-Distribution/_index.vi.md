---
title : "Tạo CloudFront Distribution"
date :  "`r Sys.Date()`" 
weight : 3
chapter : false
pre : " <b> 3. </b> "
---

#### Tạo CloudFront Distribution

1. Truy cập vào CloudFront trên bảng điều khiển AWS và nhấp vào **Create a CloudFront Distribution**.

![Create CloudFront Distribution](/images/3/0001.png?featherlight=false&width=90pc)

2. Cấu hình nguồn mặc định cho S3 bucket được tạo trước đó và cấp quyền cho CloudFront truy cập vào bucket bằng cách sử dụng thiết lập Origin Access Identity:

   - **Origin domain** > Chọn S3 bucket của bạn
   - Truy cập S3 bucket > Yes sử dụng OAI (bucket có thể giới hạn truy cập chỉ cho CloudFront)

![Create CloudFront Distribution](/images/3/0002.png?featherlight=false&width=90pc)

3. Origin access identity

   - Nhấp vào **Create new OAI** 


![Create CloudFront Distribution](/images/3/0003.png?featherlight=false&width=90pc)

4. - Trong hộp thoại hiển thị, nhấp vào Create

![Create CloudFront Distribution](/images/3/0004.png?featherlight=false&width=90pc)

5. **Policy bucket** > **Yes, update the bucket policyt**

![Create CloudFront Distribution](/images/3/0005.png?featherlight=false&width=90pc)

6.Cấu hình Default Cache Behavior như sau:

   - **View protocol policy** > **Redirect HTTP to HTTPS**.

![Create CloudFront Distribution](/images/3/0006.png?featherlight=false&width=90pc)

7. Cache key và origin requests 

   - Cache policy và origin request policy (khuyến khích)
   - Cache policy > CachingOptimized (Khuyến khích cho nguồn S3)
   - CloudFront cung cấp một tập hợp các cache policy quản lý mà bạn có thể đính kèm vào bất kỳ cache behavior của phân phối nào của bạn. Với một cache policy quản lý, bạn không cần phải viết hoặc duy trì chính sách cache của riêng mình. Các chính sách quản lý sử dụng các thiết lập được tối ưu hóa cho các trường hợp sử dụng cụ thể.

![Create CloudFront Distribution](/images/3/0007.png?featherlight=false&width=90pc)

8. Trong phần Settings:

   - Trong lab này, bạn sẽ sử dụng một tên miền được cung cấp bởi CloudFront, tuy nhiên, nếu bạn muốn sử dụng tên miền của riêng mình, bạn có thể cấu hình nó với Alternate Domain Names , bạn có thể thêm một mục mới trong phần Alternate domain name (CNAME) - tùy chọn.
   - Cấu hình Default root object - tùy chọn là index.html- Và để lại tất cả các giá trị còn lại mặc định


![Create CloudFront Distribution](/images/3/0008.png?featherlight=false&width=90pc)


9.  Nhấp vào **Create distribution**

![Create CloudFront Distribution](/images/3/0009.png?featherlight=false&width=90pc)

10. Tạo CloudFront distribution thành công.

![Create CloudFront Distribution](/images/3/00010.png?featherlight=false&width=90pc)

11. CloudFront bắt đầu tạo phân phối và thường mất từ 5 đến 10 phút để hoàn toàn phân phối. Trạng thái của phân phối sẽ là In Progress.

    - Để kiểm tra trạng thái, bạn có thể nhấp vào menu Distribution trên thanh bên trái.

![Create CloudFront Distribution](/images/3/00011.png?featherlight=false&width=90pc)
