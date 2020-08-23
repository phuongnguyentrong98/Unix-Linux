# Password_Linux
##Password_Linux
I Mục Lục :
1. Giới thiệu .
2. Password_Linux.

II Nội dung :
1. Giới thiệu :

 - Nếu bạn là người quản trị hệ thống Linux thường xuyên thì việc login/logout vào hệ thống là điều mặc định hiển nhiên.
 - Trên màn hình đăng nhập, Linux yêu cầu bạn nhập username/password, nếu bạn nhập chính xác thì bạn đăng nhập thành công vào hệ thống. Vậy điều gì đã xảy ra khi bạn nhập username/password, Linux xử lý dữ liệu đó như thế nào? mật khẩu người dùng lưu ở đâu? cơ chế xác thực như thế nào? Trong bài viết này, tôi tập trung vào tìm hiểu cách linux lưu trữ mật khẩu người dùng.

2. Password_Linux:

2.1 Thông tin password:

 - Trong Linux, file /etc/passwd là file lưu thông tin user của hệ thống, khi bạn tạo một user mới thì linux sẽ add thêm 1 bản ghi mới vào file này. Bạn dùng lệnh để show quyền truy cập file này thì thấy file này có 1 đặc điểm là tất cả người dùng trong hệ thống đều có thể đọc được .
 - Câu lệnh : 
 
 ```
ll /etc/passwd
 ```
 
![ll pass](https://user-images.githubusercontent.com/68736233/89672060-4b0af400-d90e-11ea-84ff-5bf8a17d89c0.png)

 
 - Nếu để password lưu trữ trong /etc/passwd thì cũng rất nguy hiểm, mặc dù có thể mã hóa mật khẩu bằng 1 thuật toán. Vì vậy, cần lưu trữ password người dùng trong 1 file mà chỉ ‘root’ mới đọc được. Giải pháp mà Linux đưa ra là bổ xung 1 file tên là /etc/shadow để lưu trữ mật khẩu người dùng. File /etc/shadow này chỉ truy cập được bởi ‘root’.
 
![ll shaodw](https://user-images.githubusercontent.com/68736233/89672219-886f8180-d90e-11ea-9486-7db5fa8ae13c.png)

 - Bây h xem thử nội dung của etc/shadow :
 
![ll shaodw](https://user-images.githubusercontent.com/68736233/89672421-cff60d80-d90e-11ea-8195-5d63aa963af7.png)

 - etc/shadow : chứa các thông số điều khiển quá trình user login: user password (dạng hash, không đọc được)
 - Trường đầu tiên, đó chính là username : root 
 - Trường thứ 2 đó là trường password đã được mã hóa: $6$wLE9EaMP$kyOmjKoZrGaLYAqHBAwn0903beIpX5kE6PUbYX1Qocek0Vtwg0bMkSCAw.iUe4jrAauAUq2qFGX5sPGQQh3ld1:18471:0:99999:7:::
     - Nội dung password đã được mã hóa : 
		 - Trường đầu tiên được mã hóa : ($6) cho biết thuật toán sử dụng để mã hóa với các mã :
			 - $1 : MD5 hashing algorithm.
			 - $2 : Blowfish Algorithm is in use.
			 - $2a : eksblowfish Algorithm
			 - $5 : SHA-256 Algorithm
			 - $6 : SHA-512 Algorithm
		 - Trường thứ 2 là một chuỗi dữ liệu ngẫu nhiên(random data hay còn gọi là salt) được sinh ra để kết hợp với mật khẩu người dùng(user password), để tăng sức mạnh : ($wLE9EaMP) 
		 - Trường thứ 3 là giá trị của salt + user password : ($kyOmjKoZrGaLYAqHBAwn0903beIpX5kE6PUbYX1Qocek0Vtwg0bMkSCAw.iUe4jrAauAUq2qFGX5sPGQQh3ld1)
 - Hệ thống sẽ sử dụng giá trị salt của user + password mà bạn nhập vào để tạo ra 1 chuỗi mã hóa. Nếu chuỗi mã hóa này trùng với chuỗi mã hóa trong file /etc/shadow thì user login thành công.
 
2.2 Đổi password : 

 - Để thay đổi password của user ta dùng câu lệnh passwd :
 
```
passwd
```


![passwd](https://user-images.githubusercontent.com/68736233/89673880-5e6b8e80-d911-11ea-960d-556e765f1f19.png)

2.3 Lập lịch gia hạn password :

 - Mặc định password sẽ hợp lệ trong 99.999 ngày, hay 2739 năm (default PASS_MAX_DAYS).
 - User sẽ được cảnh báo trong vòng 7 ngày trước khi password hết hạn sử dụng (default PASS_WARN_AGE) với thông báo sau khi đăng nhập vào hệ thống:
	 - Warning: your password will expire in 6 days
 
 - Ngoài ra còn có một chính sách khác nữa cho password gọi là PASS_MIN_DAYS. Đây là số ngày tối thiểu trước khi user có thể đổi password; mặc định giá trị này = 0.
 
 - Để tăng độ bảo mật tài khoản :
	 - Thay đổi thời hạn password với chage :
		
		
```	 
 chage [options] <user>
```



 - Options:
	 - -m <mindays> Minimum days
	 - -M <maxdays> Maximum days
	 - -d <lastdays> Day last changed
	 - -I <inactive> Inactive lock, sau khi mật khẩu hết hạn bao lâu sẽ lock tài khoản.
	 - -E <expiredate> Expiration (YYYY-MM-DD or MM/DD/YY)
	 - -W <warndays> Warning days
		 
 - Trong tùy chọn -d, ngày được viết dưới dạng UNIX (ngày được biểu diễn bằng số ngày kể từ ngày 1/1/1970) hay dạng YYYY/MM/DD
 - Các giá trị này được lưu ở tập tin /etc/shadow, chúng ta thể thay đổi trực tiếp trên tập tin này	
	 
	 
 - Ví dụ set up hạn của account : 2 ngày 
 
![Expriation](https://user-images.githubusercontent.com/68736233/89675903-e606cc80-d914-11ea-9daf-c17ef182132a.png)

 
 
 
 - Ví dụ set up lần thay đổi pass cuối cùng : 
 
![last change](https://user-images.githubusercontent.com/68736233/89676370-c15f2480-d915-11ea-8928-0e4cefe56875.png)
 
 
 
