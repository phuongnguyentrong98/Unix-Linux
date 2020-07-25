# Unix-Linux
Unix / Linux
============

- 1. Unix là gì?

![Alt](https://github.com/phuongnguyentrong98/Unix-Linux/issues/1#issue-665612698)

 - UNIX là một hệ điều hành máy tính viết vào những năm 1960 và 1970 do một số nhân viên của công ty AT&T Bell Labs.
 - Unix là một hệ điều hành đa nhiệm, viết bằng ngôn ngữ lập trình C. Unix có các công cụ đơn giản được thiết lập theo module. Chúng có thể chạy trên nhiều loại máy tính khác nhau.
 - Hệ điều hành Unix là tập hợp các chương trình mà thực hiện vai trò như một đường link giữa máy tính và người sử dụng. Các chương trình máy tính phân cấp các nguồn hệ thống và phối hợp tất cả các phần bên trong của máy tính được gọi là Hệ điều hành hoặc kernel.Hiện nay có khá nhiều phiên bản khác nhau của Unix trên thị trường. Trong đó Linux là một phiên bản miễn phí của hệ điều hành này.

- 2. Linux là gì?

![Alt](https://github.com/phuongnguyentrong98/Unix-Linux/issues/2#issue-665613158)

 Hệ điều hành Linux được phát triển dựa vào hệ điều hành Unix và được phát hành miễn phí hay được biết đến là một hệ điều hành nguồn mở dựa trên Unix.  Server Linux thường được sử dụng nhiều hơn là Windows hay bất kì hệ điều hành nào khác.

 - Các distro của Linux :

  - Ubuntu : là bản phân phối hiện đại, được người dùng biết đến nhiều nhất của Linux. Mục tiêu Ubuntu là mang lại cho user trải nghiệm tốt nhất trên máy tính và máy chủ.
  - Linux Mint : là một trong những bản phân phối được yêu thích nhất của Linux được xây dựng trên nền tảng Ubuntu. Do đó, Linux Mint kế thừa hầu hết các phương tiện và phần mềm sở hữu độc quyền của “đàn anh” này.
  - Debian : Debian là một hệ điều hành bao gồm các phần mềm mã nguồn mở miễn phí và luôn được cộng đồng lập trình viên yêu thích. Mặc dù thuờng xuyên phát hành các phiên bản mới nhưng nhược điểm của Debian là cập nhật khá chậm so với các bản phân phối khác.
  - Fedora : Fedora chủ yếu tập trung vào các phần mềm miễn phí nên người dùng thuờng gặp phải khó khăn trong việc cài đặt các trình điều khiển đồ họa độc quyền trên Fedora. Hiện nay, phiên bản này vẫn đang không ngừng được cải tiến và phát triển thêm.
  - CenOS/Red Hat Enterprise Linux : Red Hat Enterprise Linux là một bản phân phối Linux thương mại dành cho máy chủ và máy trạm, được phát triển dựa trên Fedora, nhưng có một nền tảng ổn định và được hỗ trợ lâu dài hơn.
  - OpenSUSE/SUSE Linux Enterprise : OpenSUSE là một trong những bản phân phối khá mạnh của Linux. Đây được đánh giá là một trong những bản phân phối thân thiện nhất của hệ điều hành này với người dùng.
  - Mageia/Mandriva : Mageia với thiết kế linh hoạt, gọn nhẹ, đơn giản hết mức có thể. Mageia được xem là “tiền bối” trong số các bản phân phối của Linux. Bên cạnh đó, Mageia còn cung cấp các tệp cấu hình sạch được thiết kế giúp người dùng chỉnh sửa một cách dễ dàng.
  - Slackware Linux : Slackware là bản phân phối lâu đời nhất của của Linux, hiện vẫn được duy trì sử dụng và đều đặn đưa ra các bản phát hành mới.
  - Puppy Linux : Puppy Linux là một bản phân phối khá nổi tiếng của Linux được phát triển dựa trên Slackware. Puppy Linux được thiết kế để trở thành một hệ điều hành nhỏ, nhẹ, có khả năng hoạt động mượt trên các máy tính cũ.

- 3.Kernel trong Linux :
  - Kernel là một chương trình máy tính điều khiển mọi thứ khác, nó là hạt nhân - trái tim của hệ điều hành! Bất cứ điều gì xảy ra trên máy tính đều đi qua nó. Đó là chương trình cốt lõi trong hệ điều hành, cũng là chương trình đầu tiên tải sau bộ nạp khởi động. 
  - Với hầu hết các kernel hiện nay, chúng ta có thể chia ra làm 3 loại: Monolithic Kernel (Kernel nguyên khối), Microkernel (Kernel vi mô ), và HybridKernel ( Kernel lai ).
  - Linux sử dụng kernel monolithic có :
   - Ưu điểm:
     - Truy cập trực tiếp đến các phần cứng
     - Dễ dàng xử lý các tín hiệu và liên lạc giữa nhiều thành phần với nhau
     - Nếu được hỗ trợ đầy đủ, hệ thống phần cứng sẽ không cần cài đặt thêm driver cũng như phần mềm khác
     - Quá trình xử lý và tương tác nhanh hơn vì không cần phải chờ đợi

   -Nhược điểm:
     - Tiêu tốn nhiều footprint cài đặt và lưu trữ
     - Tính bảo mật kém hơn vì tất cả đều hoạt động trong chế độ giám sát - supervisor mode

 - Trên nền tảng Linux, không gian địa chỉ ảo được chia thành không gian kernel và không gian người dùng.
   - Không gian người dùng, là một tập hợp các vị trí nơi các quy trình người dùng bình thường chạy (nghĩa là mọi thứ khác ngoài kernel). Vai trò của kernel là quản lý các ứng dụng đang chạy trong không gian này khỏi sự lộn xộn với nhau và máy.
   - Không gian kernel, là vị trí lưu trữ mã của kernel và thực thi theo.
   ![Alt](https://github.com/phuongnguyentrong98/Unix-Linux/issues/3#issue-665630611)
    Hình minh họa các Ring trong kiến trúc CPU

   -Nhân Linux chỉ sử dụng 0 và 3:

     - 0 cho nhân
     - 3 cho người dùng

   - Kernel là một đoạn mã, quản lý phần cứng của bạn và cung cấp sự trừu tượng hóa hệ thống. Vì vậy, nó cần phải có quyền truy cập cho tất cả các hướng dẫn máy. Hơn nữa nó là phần mềm đáng tin cậy nhất. Vì vậy nên được thực hiện với đặc quyền cao nhất. Và Cấp độ 0 là chế độ đặc quyền nhất. Cấp độ vòng 0 cũng được gọi là Chế độ hạt nhân.
   -Ứng dụng người dùng là một phần mềm đến từ bất kỳ nhà cung cấp bên thứ ba nào và bạn không thể hoàn toàn tin tưởng vào họ. Ai đó có ý định xấu có thể viết mã để đánh sập hệ thống của bạn nếu anh ta có quyền truy cập hoàn toàn vào tất cả các hướng dẫn máy. Vì vậy, ứng dụng nên được cung cấp quyền truy cập vào bộ hướng dẫn giới hạn. Và Cấp độ 3 là chế độ ít đặc quyền nhất. Vì vậy, tất cả các ứng dụng của bạn chạy trong chế độ đó. Do đó, Cấp độ 3 cũng được gọi là Chế độ người dùng.

