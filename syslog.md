# Tổng quan về Log, Syslog, Rsyslog
I Mục lục :
1. giới thiệu 
2. 
II Log, Syslog, Rsyslog :
1 Giới thiệu 
- Phân tích tệp nhật ký là một nhiệm vụ quan trọng của quản trị viên hệ thống. Nếu có vấn đề gì xảy ra sai trên hệ thống Linux, câu trả lời thường nằm trong các tệp nhật ký.
- Hai hệ thống nhật ký khác nhau được sử dụng song song và điều quan trọng là phải biết thông tin có thể được tìm thấy ở đâu. 

2 Tìm hiểu về hệ thống Logging :

- Log ghi lại liên tục các thông báo về hoạt động của cả hệ thống hoặc của các dịch vụ được triển khai trên hệ thống và file tương ứng. Log file thường là các file văn bản thông thường dưới dạng “clear text” tức là bạn có thể dễ dàng đọc được nó, vì thế có thể sử dụng các trình soạn thảo văn bản (vi, vim, nano…) hoặc các trình xem văn bản thông thường (cat, tailf, head…) là có thể xem được file log.
- Các file log có thể nói cho bạn bất cứ thứ gì bạn cần biết, để giải quyết các rắc rối mà bạn gặp phải miễn là bạn biết ứng dụng nào. Mỗi ứng dụng được cài đặt trên hệ thống có cơ chế tạo log file riêng của mình để bất cứ khi nào bạn cần thông tin cụ thể thì các log file là nơi tốt nhất để tìm.
- Các tập tin log được đặt trong thư mục /var/log. Bất kỳ ứng dụng khác mà sau này bạn có thể cài đặt trên hệ thống của bạn có thể sẽ tạo tập tin log của chúng tại /var/log. Dùng lệnh ls -l /var/log để xem nội dung của thư mục này.
- Số lượng tệp chính xác trong thư mục / var / log sẽ thay đổi, tùy thuộc vào cấu hình của một máy chủ và các dịch vụ đang chạy trên máy chủ đó. Một số tuy nhiên, tệp tồn tại trong hầu hết các trường hợp và với tư cách là quản trị viên, bạn nên biết chúng là tệp nào và loại nội dung nào
- VD: Ý nghĩa một số file log thông dụng có mặc định trên /var/log : 
	 - /var/log/messages – Chứa dữ liệu log của hầu hết các thông báo hệ thống nói chung, bao gồm cả các thông báo trong quá trình khởi động hệ thống.
	 - /var/log/dmesg – Thư mục này có chứa thông điệp rất quan trọng về kernel ring buffer. Lệnh dmesg có thể được sử dụng để xem các tin nhắn của tập tin này.
	 - /var/log/cron – Chứa dữ liệu log của cron deamon. Bắt đầu và dừng cron cũng như cronjob thất bại.
	 - /var/log/maillog hoặc /var/log/mail.log – Thông tin log từ các máy chủ mail chạy trên máy chủ.
	 - /var/log/secure – Thông điệp an ninh liên quan sẽ được lưu trữ ở đây. Điều này bao gồm thông điệp từ SSH daemon, mật khẩu thất bại, người dùng không tồn tại, vv
	 - /var/log/boot.log - các thông báo liên quan đến khởi động hệ thống
	 - /var/log/audit/audit.log - Chứa các thông báo kiểm tra. SELinux ghi vào tệp này.
	 - /var/log/samba -  Cung cấp tệp nhật ký cho dịch vụ Samba. Lưu ý rằng Samba bằng mặc định không được quản lý thông qua rsyslog, nhưng ghi trực tiếp vào / var / thư mục log.
	 - /var/log/sssd - Chứa các tin nhắn đã được viết bởi dịch vụ sssd, đóng một vai trò quan trọng trong quá trình xác thực.
	 - /var/log/cups - Chứa các thông báo nhật ký được tạo bởi dịch vụ in CUPS.
	 - /var/log/httpd/ - Thư mục chứa các tệp nhật ký được viết bởi Apache máy chủ web. Lưu ý rằng Apache ghi thông báo vào các tệp này trực tiếp và không thông qua rsyslog
	 
- rsyslogd: rsyslogd là sự cải tiến của syslogd, một dịch vụ chăm sóc quản lý các tệp nhật ký tập trung.
	 - Rsyslogd ghi các tin nhắn tới các tệp khác nhau trong thư mục / var / log. rsyslogd cũng cung cấp các tính năng không tồn tại trên tạp chí Android, chẳng hạn như ghi nhật ký tập trung và lọc thư bằng cách sử dụng các mô-đun.
- journald: Với sự ra đời của systemd, hệ thống dịch vụ nhật ký journald cũng được giới thiệu. Dịch vụ này được tích hợp chặt chẽ với systemd, cho phép quản trị viên đọc thông tin chi tiết từ nhật ký trong khi theo dõi trạng thái dịch vụ bằng lệnh "systemctl status".
	 - journald (được thực hiện bởi daemon systemd-journald) cung cấp hệ thống quản lý nhật ký nâng cao. journald thu thập các thông báo từ kernel, toàn bộ quy trình khởi động và các dịch vụ và ghi các thông báo này vào một sự kiện nhật ký. Nhật ký sự kiện này được lưu trữ ở định dạng nhị phân và nó có thể được truy vấn bằng cách sử dụng lệnh journalctl.
- journald không phải là sự thay thế cho rsyslog; nó chỉ là một cách khác để ghi lại thông tin. journald được tích hợp chặt chẽ với systemd và do đó ghi lại mọi thứ mà máy chủ của bạn đang làm. rsyslogd cho biết thêm một số dịch vụ cho nó. Đặc biệt, nó đảm nhiệm việc ghi thông tin nhật ký vào tệp (sẽ liên tục giữa các lần khởi động lại) và nó cho phép bạn định cấu hình từ xa ghi nhật ký và ghi nhật ký máy chủ

3 Reading Log Files ( đọc file log ) :
- Là quản trị viên, bạn cần có khả năng diễn giải nội dung của tệp nhật ký.
- VD  Hiển thị một phần nội dung từ tệp /var/log/messages.

![tail](https://user-images.githubusercontent.com/68736233/91069348-7d7f5580-e65f-11ea-9cf6-8e84ac6e6164.png)

-Date and time: Mọi thông báo nhật ký đều bắt đầu bằng thời gian.
-Host: Máy chủ lưu trữ tin nhắn. Điều này có liên quan vì rsyslogd có thể được cấu hình để xử lý ghi nhật ký từ xa.
-Service or process name : Tên của dịch vụ hoặc quy trình đã tạo thông điệp.
-Message content: Nội dung của tin nhắn, trong đó có thông báo chính xác đã được ghi lại.

4 Live Log File Monitoring ( giám sát tệp nhật ký trực tiếp ) :
- Khi bạn đang định cấu hình các dịch vụ trên Linux, có thể hữu ích khi xem trong thời gian thực điều gì đang xảy ra. Ví dụ: bạn có thể mở hai phiên đầu cuối cùng một lúc. Trong một phiên đầu cuối, bạn định cấu hình và kiểm tra dịch vụ. Trong phiên đầu cuối khác, bạn thấy chính xác điều gì đang xảy ra trong thời gian thực .
- Câu lệnh : hiển thị trong thời gian thực dòng nào được thêm vào tệp nhật ký

```
tail -f <logfile>
```

5 Configuring rsyslogd ( Định cấu hình rsyslog ) :
- Để đảm bảo rằng thông tin cần ghi được ghi vào vị trí mà bạn muốn tìm, bạn có thể cấu hình dịch vụ rsyslogd thông qua /etc/rsyslog.conf. Trong tệp này, bạn tìm thấy các phần khác nhau cho phép bạn chỉ định thông tin nên được viết ở đâu và như thế nào.
- Understanding rsyslogd Configuration Files 
	 - cấu hình cho rsyslogd không được xác định chỉ trong một tệp cấu hình. Tệp /etc/rsyslogd.conf là vị trí trung tâm nơi rsyslogd được định cấu hình.
	 - Thư mục này có thể được điền bằng cách cài đặt các gói RPM trên máy chủ. Khi tìm kiếm cấu hình nhật ký cụ thể, hãy đảm bảo luôn xem xét nội dung của thư mục này.
	 - Nếu các tùy chọn cụ thể cần được chuyển tới dịch vụ rsyslogd khi khởi động, bạn có thể thực hiện việc này bằng cách sử dụng tệp / etc / sysconfig / rsyslog.
	 - Tệp này theo mặc định chứa một dòng ghi SYSLOGD_OTIONS = “”. Trên dòng này, bạn có thể chỉ định rsyslogd tham số khởi động. Biến SYSLOGD_OPTIONS được bao gồm trong tệp cấu hình systemd khởi động rsyslogd.
	 - Về mặt lý thuyết, bạn có thể thay đổi tham số khởi động trong tệp này, nhưng điều đó không được khuyến khích.
	 
- Các phần trong rsyslog.conf : rsyslog.conf được sử dụng để chỉ định những gì sẽ được ghi lại và vị trí của nó đã đăng nhập. Để thực hiện việc này, bạn sẽ tìm thấy các phần khác nhau trong tệp cấu hình:
	 - #### MODULES ####: rsyslogd là mô-đun. Các mô-đun được đưa vào nâng cao các tính năng được hỗ trợ trong rsyslogd.
	 - #### GLOBAL DIRECTIVES ####: Phần này được sử dụng để chỉ định toàn cầu các tham số, chẳng hạn như vị trí nơi các tệp phụ được ghi hoặc mặc định định dạng dấu thời gian.
	 - #### RULES ####: Đây là phần quan trọng nhất của tệp rsyslog.conf. Nó chứa các quy tắc chỉ định thông tin nào nên được ghi vào đó
	 
6 Facilities, Priorities, and Log Destinations: 
- Một cơ sở chỉ định một loại thông tin được ghi lại. Rsyslogd sử dụng một danh sách cơ sở cố định, không thể mở rộng. Điều này là do lạc hậu khả năng tương thích với dịch vụ nhật ký hệ thống kế thừa.
- Mức độ ưu tiên được sử dụng để xác định mức độ nghiêm trọng của thông báo cần được ghi lại. Khi chỉ định mức độ ưu tiên, theo mặc định, tất cả các thư có mức độ ưu tiên đó và tất cả các ưu tiên cao hơn được ghi lại.
- Đích xác định nơi thông báo sẽ được ghi tới. Đích tiêu biểu là các tệp, nhưng mô-đun rsyslog cũng có thể được sử dụng làm đích, để cho phép xử lý thêm thông qua một mô-đun rsyslogd.

6.1 rsyslogd Facilities ( cơ sở rsyslogd ) :
- Các cơ sở hệ thống syslog được xác định vào những năm 1980 và để đảm bảo khả năng tương thích ngược, không có cơ sở mới nào có thể được thêm vào. Kết quả là một số cơ sở vẫn tồn tại về cơ bản không còn phục vụ mục đích nào nữa và một số dịch vụ đã trở nên có liên quan tại giai đoạn sau không có cơ sở riêng của họ.
- Như một giải pháp, hai loại cơ sở cụ thể có thể được sử dụng. Cơ sở daemon là một phương tiện chung có thể được sử dụng bởi bất kỳ daemon nào. Ngoài ra, phương tiện local0 đến local7 có thể được sử dụng.
- Để xác định loại thư nào nên được ghi lại, các mức độ nghiêm trọng khác nhau có thể được sử dụng trong các dòng rsyslog.conf. Những mức độ nghiêm trọng này là ưu tiên của nhật ký hệ thống.
	 - auth / authpriv : Tin nhắn liên quan đến xác thực
	 - cron : Tin nhắn do dịch vụ crond tạo ra
	 - daemon : Cơ sở chung có thể được sử dụng cho daemon không xác định
	 - kern : Tin nhắn từ kernel
	 - lpr : Tin nhắn được tạo thông qua hệ thống in lpd cũ
	 - mail : Thư liên quan đến email
	 - mark : Cơ sở đặc biệt có thể được sử dụng để viết điểm đánh dấu định kỳ
	 - News : Tin nhắn do hệ thống tin tức NNTP tạo ra
	 - security : Giống như auth / authpriv. Không nên sử dụng nữa
	 - syslog : Tin nhắn được tạo bởi hệ thống syslog
	 - user : Tin nhắn được tạo trong không gian người dùng
	 - uucp : Thông báo được tạo bởi hệ thống UUCP kế thừa
	 - local0-7 : Tin nhắn được tạo bởi các dịch vụ được cấu hình bởi bất kỳ local nào từ 0-7
	 
6.2 rsyslogd Priorities :
- Khi một mức độ ưu tiên cụ thể được sử dụng, tất cả các tin nhắn có mức độ ưu tiên đó trở lên sẽ ghi nhật ký theo các thông số kỹ thuật được sử dụng trong quy tắc cụ thể đó. Nếu bạn cần định cấu hình ghi nhật ký một cách chi tiết, nơi các thư có mức độ ưu tiên khác nhau được gửi đối với các tệp khác nhau, bạn có thể chỉ định mức độ ưu tiên bằng dấu bằng (=) phía trước nó, như trong tệp cấu hình sau, tệp này sẽ gửi tất cả các thông báo gỡ lỗi cron tới tệp cụ thể có tên /var/log/cron.debug.
	 - debug : thông báo gỡ lỗi sẽ cung cấp nhiều thông tin nhất có thể về hoạt động dịch vụ
	 - info : Thông báo cung cấp thông tin về hoạt động bình thường của dịch vụ
	 - notice : Được sử dụng cho các thông báo cung cấp thông tin về các mục có thể trở thành vấn đề sau
	 - warning / warn : Có điều gì đó chưa tối ưu nhưng vẫn chưa có lỗi 
	 - err /error : Đã xảy ra lỗi không xác định
	 - crit : Đã xảy ra lỗi nghiêm trọng
	 - alert : cảnh báo 
	 - emerg / panic : Thông báo được tạo khi tính khả dụng của dịch vụ bị ngừng
	 
- Hãy xem xét dòng sau, trong đó tất cả các thông báo cron chỉ có ưu tiên gỡ lỗi được ghi vào một tệp cụ thể. Lưu ý phần trước của dòng, bộ đệm nào viết như vậy thông tin đó được ghi lại theo cách hiệu quả hơn:
	 - " cron.=debug -/var/log/cron.debug "
	 
7. Rotating Log Files :
- Để ngăn các thông báo nhật ký hệ thống lấp đầy hoàn toàn hệ thống của bạn, các thông báo nhật ký có thể được xoay vòng. Điều đó có nghĩa là khi đạt đến một ngưỡng nhất định, tệp nhật ký cũ bị đóng và tệp nhật ký mới được mở. Tiện ích logrotate được khởi động định kỳ thông qua dịch vụ crond để chăm sóc các tệp nhật ký luân phiên.
- Khi một tệp nhật ký được xoay, tệp nhật ký cũ thường được sao chép vào một tệp có ngày luân chuyển trong đó.
- Các tệp nhật ký đã được xoay không được lưu trữ ở bất kỳ đâu; chúng chỉ là biến mất. Nếu chính sách công ty của bạn yêu cầu bạn có thể truy cập thông tin về các sự kiện đã xảy ra hơn 5 tuần trước, bạn nên thực hiện các biện pháp.
- Có thể quyết định sao lưu tệp nhật ký hoặc định cấu hình máy chủ nhật ký tập trung nơi logrotate giữ các thông báo được luân chuyển trong một khoảng thời gian dài hơn đáng kể.
- Cài đặt mặc định để log rotation được giữ trong tệp /etc/logrotate.conf 

![rotate](https://user-images.githubusercontent.com/68736233/91529906-5614db00-e934-11ea-9b2f-c1ee1eed853b.png)

- Các cài đặt quan trọng nhất được sử dụng trong tệp cấu hình này yêu cầu logrotate xoay tệp hàng tuần và giữ bốn phiên bản cũ của tệp. Bạn có thể tải xuống thêm thông tin về các tham số khác trong tệp này thông qua man logrotate.

8. Working with journald
- Dịch vụ systemd-journald lưu trữ các thông báo nhật ký trong tạp chí, một tệp nhị phân được lưu trữ trong tệp / run / log / journal. Bạn có thể kiểm tra tệp này bằng cách sử dụng journalctl
- Điều làm cho journalctl trở thành một lệnh linh hoạt là nhiều tùy chọn lọc của nó cho phép bạn để hiển thị chính xác những gì bạn cần.
- Cách dễ nhất để sử dụng journalctl là chỉ cần gõ lệnh. Nó hiển thị cho bạn gần đây các sự kiện đã được ghi vào nhật ký kể từ khi máy chủ của bạn khởi động lần cuối. Thông báo rằng kết quả của lệnh này được hiển thị trong ít trang hơn và theo mặc định, bạn sẽ thấy đầu nhật ký.
- Bởi vì nhật ký được viết từ thời điểm của bạn máy chủ khởi động, điều này đang hiển thị thông báo nhật ký liên quan đến khởi động. Nếu bạn muốn xem lần cuối thư đã được ghi, bạn có thể sử dụng "journalctl -f", hiển thị cuối cùng dòng thông báo nơi các dòng nhật ký mới được tự động thêm vào.
8.2 Discovering journalctl:
- command :

```
journalctl
```

-options : 
	 - Tab : Điều này cho thấy các tùy chọn cụ thể có thể được sử dụng để lọc.
	 - -n number : tùy chọn hiển thị số dòng cuối cùng của tạp chí
	 - -p err : hiển thị dòng lỗi 
	 - -o verbose : Màn hiển thị các tùy chọn khác nhau được sử dụng khi viết nhật ký
	 
8.3 Bảo quản systemd Journal :
- Theo mặc định, journal được lưu trữ trong tệp / run / log / journal. Toàn bộ thư mục / run chỉ được sử dụng cho thông tin trạng thái quy trình hiện tại, có nghĩa là journal bị xóa khi hệ thống khởi động lại. Để làm cho journal liên tục giữa hệ thống khởi động lại, bạn nên đảm bảo rằng có tồn tại thư mục / var / log / journal.
- Ngay cả khi journal được ghi vào tệp vĩnh viễn trong / var / log / journal, điều đó không có nghĩa là journal được lưu giữ mãi mãi. Journal có tích hợp log rotation sẽ được sử dụng hàng tháng.
- Để thay đổi các cài đặt này, bạn có thể sửa đổi tệp /etc/systemd/journald.conf.

