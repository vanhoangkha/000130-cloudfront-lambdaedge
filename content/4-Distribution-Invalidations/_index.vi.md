---
title : "Kiểm tra Distribution Invalidations"
date :  "`r Sys.Date()`" 
weight : 4
chapter : false
pre : " <b> 4. </b> "
---

#### Kiểm tra Distribution Invalidations

Khi sử dụng Amazon CloudFront để phân phối tài nguyên cho website, một số tài nguyên sẽ được lưu trữ trong bộ nhớ cache của CloudFront để tăng tốc độ truy cập cho người dùng. Tuy nhiên, khi bạn thực hiện thay đổi trên một tài nguyên đã được lưu trữ trong bộ nhớ cache nhưng không thể thay đổi URL để trỏ đến phiên bản mới, bạn cần phải thực hiện Invalidations để loại bỏ phiên bản cũ và tải lại phiên bản mới từ máy chủ gốc.

1. Truy cập vào tab Invalidations trên giao diện CloudFront Console.

- Tạo một Invalidation cho tài nguyên index.html. 

![CloudFront Lab](/images/6/0001.png?featherlight=false&width=90pc)

2. Bạn có thể chỉ định / trong Object paths vì chúng tôi đã đặt index.html làm đối tượng gốc mặc định.


![CloudFront Lab](/images/6/0002.png?featherlight=false&width=90pc)

3. Đang trong quá trình tạo  Invalidations


![CloudFront Lab](/images/6/0003.png?featherlight=false&width=90pc)

4. Tạo  Invalidations thành công

![CloudFront Lab](/images/6/0004.png?featherlight=false&width=90pc)

5. Sau vài giây, thử lại trang web bằng cách sử dụng công cụ phát triển trình duyệt, bạn sẽ thấy rằng nó đã không còn được lưu trữ trong bộ nhớ cache của CloudFront nữa và tải lại phiên bản mới từ máy chủ gốc.

![CloudFront Lab](/images/6/0005.png?featherlight=false&width=90pc)

Lưu ý: Quá trình Invalidations có thể mất vài phút để hoàn tất và trong khoảng thời gian đó, người dùng có thể truy cập vào phiên bản cũ của tài nguyên. Do đó, bạn cần cân nhắc và thực hiện Invalidations vào thời điểm phù hợp để đảm bảo tài nguyên mới nhất được phân phối cho người dùng.

Dữ liệu cho thấy khi bạn thực hiện Invalidations, nếu một tài nguyên đã được lưu trữ trong bộ nhớ cache của CloudFront, nó sẽ bị loại bỏ khỏi cache và phiên bản mới sẽ được tải xuống từ máy chủ gốc khi người dùng yêu cầu truy cập tài nguyên đó. Điều này giúp đảm bảo rằng người dùng sẽ nhận được phiên bản mới nhất của tài nguyên mà không cần phải xóa bộ nhớ cache của trình duyệt hoặc chờ đợi bộ nhớ cache của CloudFront hết hạn.

Việc sử dụng Invalidations trong Amazon CloudFront cũng giúp tiết kiệm chi phí và tăng hiệu quả hoạt động cho website của bạn. Khi một tài nguyên được lưu trữ trong bộ nhớ cache của CloudFront, việc tải xuống tài nguyên đó từ máy chủ gốc sẽ tốn nhiều thời gian và tài nguyên hệ thống của bạn. Khi bạn sử dụng Invalidations để loại bỏ các phiên bản cũ, CloudFront sẽ không còn phải tải lại các phiên bản cũ này nữa, giúp tiết kiệm tài nguyên và giảm chi phí hoạt động cho website của bạn.

Tóm lại, Invalidations là một công cụ quan trọng giúp đảm bảo rằng người dùng sẽ nhận được phiên bản mới nhất của tài nguyên và giúp tăng tốc độ truy cập cho website. Nó cũng giúp tiết kiệm tài nguyên và giảm chi phí hoạt động cho website của bạn.