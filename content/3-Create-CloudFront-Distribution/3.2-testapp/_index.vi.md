---
title : "Kiểm tra ứng dụng"
date :  "`r Sys.Date()`" 
weight : 2
chapter : false
pre : " <b> 3.2 </b> "
---

#### Kiểm tra ứng dụng

1 - Khi bạn tạo một phân phối CloudFront mới, nó sẽ có trạng thái đang tiến hành và nó sẽ cần một thời gian để phân tán đến tất cả các điểm hiện diện (points of presence) trên toàn cầu. Tuy nhiên, bạn có thể kiểm tra xem phân phối đã sẵn sàng để sử dụng cục bộ hay chưa bằng cách tra cứu tên miền CloudFront của nó bằng lệnh nslookup trong dòng lệnh. Khi bạn tra cứu tên miền CloudFront, CloudFront sẽ trả về nhiều địa chỉ IP để tăng tính sẵn sàng cho ứng dụng.

- Khi phân tán đã đạt đến tất cả các điểm hiện diện, trạng thái của phân phối sẽ thay đổi thành được triển khai (deployed) và bạn có thể sử dụng nó trên trình duyệt web của mình bằng URL CloudFront của riêng bạn.

- Truy cập vào EC2

![CloudFront Lab](/images/5/0001.png?featherlight=false&width=90pc)

- Thực hiện connect vào EC2.

![CloudFront Lab](/images/5/0002.png?featherlight=false&width=90pc)

2 - Khi phân tán hoàn tất phân tán, bạn có thể kiểm tra trang web trên trình duyệt của mình được phục vụ bởi CloudFront bằng cách sử dụng URL CloudFront của bạn http://dxxxx.cloudfront.net.

Trong trang web, bạn có thể thấy các tiêu đề khác nhau mà CloudFront đã chuyển tiếp và đính kèm vào điểm cuối API của bạn:

![CloudFront Lab](/images/5/0003.png?featherlight=false&width=90pc)

x-amz-cf-id: Một id duy nhất cho yêu cầu này do CloudFront cung cấp. Nếu bạn làm mới trang web, bạn sẽ thấy rằng id yêu cầu thay đổi. Nó hữu ích để đăng nhập nó trên máy chủ web của bạn nói chung. Ngoài ra, id này sẽ được gửi trở lại cho mọi yêu cầu của người xem và được gửi đến nhật ký truy cập CloudFront. Nếu bạn cần gỡ lỗi vấn đề nào, bạn có thể mở một phiếu hỗ trợ và cung cấp cho họ id yêu cầu.
Hãy lưu ý cách CloudFront đã chuyển hướng yêu cầu sang HTTPS.

![CloudFront Lab](/images/5/0004.png?featherlight=false&width=90pc)

3 - Nếu bạn sử dụng các công cụ phát triển trình duyệt web yêu thích của mình, bạn có thể kiểm tra các tiêu đề phản hồi được gửi bởi CloudFront. Ba tiêu đề đáng chú ý để kiểm tra:

x-amz-cf-id: Chứa id yêu cầu được gán bởi CloudFront.
x-amz-cf-pop: Cho biết vị trí cạnh CloudFront đã phục vụ yêu cầu của bạn. Mỗi vị trí cạnh được định danh bằng một mã ba chữ cái và một số được gán tùy ý, ví dụ, DFW3. Mã ba chữ cái thường tương ứng với mã sân bay của Hiệp hội Vận tải Hàng không Quốc tế cho một sân bay gần vị trí cạnh.
x-cache: Cho biết liệu yêu cầu đã được đánh giá trúng hay trượt. Thông thường, đối với tệp html của bạn, bạn sẽ nhận được giá trị 'Hit từ Cloudfront' trong các yêu cầu tiếp theo, nhưng luôn luôn 'Miss from CloudFront' cho yêu cầu /api vì bộ nhớ đệm đã bị vô hiệu hóa cho hành vi này.

![CloudFront Lab](/images/5/0007.png?featherlight=false&width=90pc)

Điều này có nghĩa là nếu bạn truy cập trang web của mình một lần nữa, yêu cầu sẽ được truy xuất từ bộ nhớ đệm và trả về kết quả lưu trữ trong đó thay vì phải tải lại từ máy chủ gốc, cải thiện thời gian tải trang và tăng hiệu suất. Tuy nhiên, nếu bạn thực hiện các thay đổi trên trang web của mình, bạn có thể muốn làm mới bộ nhớ đệm để đảm bảo rằng người dùng của bạn xem được các thay đổi mới nhất.

![CloudFront Lab](/images/5/0005.png?featherlight=false&width=90pc)

4 - Trong trường hợp bạn cần truy cập phân phối từ một vùng địa lý khác, bạn có thể sử dụng các tên miền thay thế của CloudFront, bao gồm cả tên miền cho từng khu vực địa lý khác nhau. Điều này giúp đảm bảo rằng người dùng tại mỗi khu vực đều được phục vụ bởi cạnh CloudFront gần nhất của họ, giúp tối ưu hóa thời gian tải trang và giảm thiểu độ trễ.


![CloudFront Lab](/images/5/0006.png?featherlight=false&width=90pc)

5 - Nếu bạn cần tạo ra một bản sao của phân phối CloudFront hiện có, bạn có thể sử dụng tính năng tạo bản sao để tạo ra một bản sao chính xác của phân phối hiện tại. Điều này có thể hữu ích khi bạn cần phục vụ một phiên bản khác của trang web hoặc ứng dụng của mình tại cùng một thời điểm, hoặc khi bạn cần đối phó với bất kỳ sự cố nào xảy ra với phân phối hiện tại.

6 - Khi bạn cần thiết lập các chính sách truy cập để giới hạn quyền truy cập đến phân phối của mình, bạn có thể sử dụng tính năng quản lý quyền truy cập của CloudFront. Điều này cho phép bạn thiết lập các chính sách truy cập dựa trên địa chỉ IP, tên miền, phương thức HTTP và nhiều hơn nữa, giúp đảm bảo rằng chỉ có những người dùng được ủy quyền mới có thể truy cập đến phân phối của bạn.


7 - Cuối cùng, nếu bạn cần hỗ trợ từ đội ngũ kỹ thuật của AWS, bạn có thể mở một phiếu hỗ trợ và cung cấp chi tiết về vấn đề của bạn, bao gồm các ID yêu cầu CloudFront và các thông tin khác về phân phối của bạn. Đội ngũ kỹ thuật của AWS sẽ cố gắng hỗ trợ bạn giải quyết vấn đề của bạn trong thời gian sớm nhất có thể.